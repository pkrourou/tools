## 技术架构文档 - 点九图（9-Patch）测试工具

### 1. 技术选型
- 运行形态：纯静态页面（HTML + CSS + 原生 JavaScript）
- 渲染：Canvas 2D（支持多段 stretch 的分片绘制）
- 打包：无（单文件或少量静态文件即可运行）

### 2. 核心数据模型
- `rawImage`：原始 `.9.png` 图像（包含 1px 标注边）
- `trimmedCanvas`：去除 1px 边框后的实际内容图（W-2, H-2）
- `stretchX[]`：水平 stretch 区间数组，元素为 `[start, endExclusive)`，坐标基于 trimmed
- `stretchY[]`：垂直 stretch 区间数组，元素为 `[start, endExclusive)`
- `padding`：`{ left, top, right, bottom }`，坐标/数值基于 trimmed
- `segmentsX[] / segmentsY[]`：分段后的网格切片信息（用于渲染）

### 3. 解析算法
#### 3.1 黑色像素判定
- 读取 `ImageData`，像素满足 `alpha > 0 && r,g,b < 阈值` 视为标记像素
- 阈值可取 16 以内，兼容抗锯齿导致的近黑色

#### 3.2 区间提取（支持多段）
- 顶边（y=0，x=1..w-2）扫描得到 `stretchXRaw` 运行段
- 左边（x=0，y=1..h-2）扫描得到 `stretchYRaw` 运行段
- 底边（y=h-1）与右边（x=w-1）扫描得到内容区运行段，换算为 padding：
  - 若底边存在黑段 `[a,b]`（含端点，坐标基于 raw），则
    - `contentXStart = a-1`
    - `contentXEndExclusive = (b+1)-1`
    - `paddingLeft = contentXStart`
    - `paddingRight = trimmedW - contentXEndExclusive`
  - 竖向同理
- 坐标统一转换为 trimmed：`startTrim = startRaw - 1`

### 4. 渲染算法（多段 Nine-Patch）
#### 4.1 分段构建
- 从 `stretchX[]` 构建边界集合：`{0, W, s, e}`（e 为 endExclusive）
- 排序后得到 `boundariesX`，形成连续片段 `[b[i], b[i+1])`
- 片段 `stretchable` 判定：该片段区间与任一 `stretchX` 有交集
- Y 方向同理

#### 4.2 目标尺寸分配
- 固定片段宽度保持原宽
- 可拉伸片段按原宽比例分配到剩余宽度（目标宽 - 固定宽总和）
- 若无可拉伸片段或目标宽小于固定总和，退化为按整体比例缩放（保证可视）
- 高度同理

#### 4.3 网格绘制
- 双层循环遍历 `segmentsX × segmentsY`
- 对每个单元格执行 `drawImage(trimmedCanvas, sx, sy, sw, sh, dx, dy, dw, dh)`
- 支持 `imageSmoothingEnabled` 切换

### 5. UI 结构（建议）
- 左侧控制面板：上传、解析结果、宽高输入、预设、开关项（叠加/背景/平滑）
- 右侧预览区：多卡片网格，每张卡片展示不同尺寸渲染与内容区叠加

### 6. 安全与隐私
- 不进行网络上传，不写入本地文件系统（除非用户手动导出）
- 所有处理在浏览器内完成

### 7. 可测试点
- 单段 stretch、双段 stretch、多段 stretch
- 仅水平/仅垂直 stretch
- 无标注兜底逻辑
- padding 标注缺失/异常时的提示与默认值

