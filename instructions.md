# Role Definition
你是一位兼具学术背景与顶尖审美的高级前端工程师。你精通 "Apple Design System" (Human Interface Guidelines) 和现代 Web 技术。你的目标是利用 HTML5, Tailwind CSS, 和 JS，为一个顶级计算机视觉会议 (ICLR/CVPR) 的论文制作一个“液态毛玻璃风格 (Liquid Glassmorphism)”的项目主页。

# Input Data
1.  论文的每个小节的内容已经放到了sec/
2.  你需要展示的关键结果的 LaTeX 表格源码和核心 Algorithm 的 LaTeX 源码我专门放到了 tables_and_algorithms.txt
3.  我挑选好了的demo,一共两类分别是生成和理解的分别在:video_gen/,understanding/
4.  论文中的核心图片我专门放到了figures/下,这些图片的caption我专门放到了captions.txt里

# Visual Philosophy: Liquid Apple Aesthetics (核心美学)
1.  **Background (有机流体)**:
    -   背景不是静态的。创建一个包含 3 个流动的彩色光斑 (Orbs/Blobs) 的背景。
    -   颜色使用 **Cool Gray**, **Ethereal Blue**, 和 **Soft Indigo**。
    -   使用 CSS Animation 让它们缓慢移动、变形、融合，创造出一种“活”的呼吸感。
2.  **Glass Material (液态玻璃)**:
    -   所有卡片容器使用高透明度白色 (`bg-white/70`) 配合极高的背景模糊 (`backdrop-blur-3xl`)。
    -   边缘要有细腻的半透明描边 (`border-white/40`) 模拟玻璃反光。
    -   阴影要是彩色的、弥散的，而非纯黑。
3.  **Fluid Motion (灵动交互)**:
    -   所有动画使用 Spring Physics (弹簧物理) 曲线 (`cubic-bezier(0.16, 1, 0.3, 1)`).
    -   文本出现使用 "Blur-Reveal" (从模糊到清晰) 效果，而非生硬的淡入。

# Page Structure & Content Implementation

## 1. Hero Section
-   **Title**: "Pyramid Sparse Attention" (大号，字重对比明显).
-   **Authors & Affiliation**: 干净利落的排版。
-   **Links**: Pill-shaped buttons (Paper, Code, Demo).

## 2. Interactive Demos (核心亮点 - 需手写 JS 实现逻辑)
请创建两个玻璃面板：
* **Demo A: Video Generation (Speed Comparison)**
    -   左右并列两个视频容器：Left="Baseline", Right="Ours (w/ TDM)".
    -   **Feature**: 右上角悬浮一个磨砂徽章 "⚡️ [X]x Faster".
    -   **Control**: 一个播放按钮同时控制两个视频同步开始。
* **Demo B: Video Understanding (Latency Race)**
    -   模拟 Chat 界面。上方是 User Input (Video+Prompt)。
    -   下方是 Model Response。
    -   **Animation Logic**:
        -   Baseline: 显示 Loading Spinner (转圈) 持续 3秒。
        -   Ours: Spinner 仅显示 0.5秒，然后立即开始生成文本。
        -   **Effect**: 文本生成时使用 "Blur-in" 效果 (文字像墨水晕开一样出现)。

## 3. Method (Bento Grid)
-   使用 2x2 网格展示架构图和原理图。
-   风格保持一致的玻璃质感。

## 4. Scientific Rigor (LaTeX 渲染部分 - 重要)
我将提供 LaTeX 源码，请你将其转换为 HTML/Tailwind 结构，不要直接输出 LaTeX 代码。
* **Tables**:
    -   转换为 HTML `<table>`。
    -   **Style**: "Modern Booktabs"。无纵向边框，只有 Header 和 Bottom 有横向分隔线。
    -   Row Hover: 鼠标悬停行时，背景轻微变色。
    -   Font: 数字使用 Tabular figures (等宽数字) 对齐。
* **Algorithm**:
    -   转换为一个精美的 Pseudo-code Block (`<div>` 结构)。
    -   **Style**: 类似于高亮代码编辑器。显示行号 (Line numbers) 为灰色。
    -   Keywords (Input, Output, For, If) 使用粗体或特定颜色高亮。
    -   数学公式部分：请保留 LaTeX 格式 (例如 `$Q, K, V$`)，并引入 **MathJax** 库在网页加载时自动渲染这些数学符号。

# Technical Stack Constraints
1.  **Single File**: 输出单一 `index.html`。
2.  **Libraries**:
    -   Tailwind CSS (CDN)
    -   FontAwesome (CDN)
    -   **MathJax** (CDN, 用于渲染公式)
    -   Alpine.js (可选，如果需要处理复杂的交互状态，或者使用原生 JS)

# Action
请先阅读上述要求,然后编写完整的页面代码。目前我还没有准备好demo,视频展示demo你可以先不放具体视频,理解demo的吐字效果你可以先设置一个默认吐的字来看看效果,之后我准备好了我再给你提供我们再添加上去