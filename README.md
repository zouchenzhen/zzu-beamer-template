# ZZU Beamer Template

> 一份贴近郑州大学（Zhengzhou University, ZZU）视觉风格的 LaTeX Beamer 演示模板。<br>
> A LaTeX Beamer template themed for Zhengzhou University.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Engine](https://img.shields.io/badge/engine-XeLaTeX-red.svg)
![Aspect Ratio](https://img.shields.io/badge/aspect-16%3A9%20%7C%204%3A3-lightgrey.svg)

---

## 简介 / Overview

本模板面向郑州大学师生的学术汇报场景：本科与研究生答辩、课题组组会、学术讲座、课程展示等。模板提供了：

- 基于郑大主色 `#A33A37`（实证提取自官方校徽）的完整 Beamer 配色方案
- 红色横幅式标题页 + 全屏红色分节页 + 致谢页的现成实现
- 列表、公式、表格、代码、图片、引用等常用元素的演示
- 4:3 与 16:9 双比例兼容
- 单文件主题 (`zzubeamer.sty`) 设计，开箱即用

> ℹ️ **致谢**: 本模板的整体组织结构（多文件拆分、章节自动分页、配色注入方式）参考了以下开源工作。本仓库为独立重写，颜色 / 版式 / Logo / 文案均已替换为郑州大学元素，可独立使用。
>
> - [pan2013e/ZJU-beamer-template](https://github.com/pan2013e/ZJU-beamer-template) — 浙江大学 Beamer 模板（Zhiyuan Pan），提供 `frame/format/command` 三段式组织思路
> - [qychen2001/ZJU-Beamer-Template](https://github.com/qychen2001/ZJU-Beamer-Template) — 更现代的浙大模板（光头哥 / PhilFan），借鉴其 `*.sty` + `\usepackage{}` 风格的命名约定
> - [ZZUTUG/ZZU-Beamer](https://github.com/ZZUTUG/ZZU-Beamer) — 已有的郑大 Beamer 主题集合（Fw[a]rd，改编自 HFUT），本仓库**有意更名为 `zzubeamer.sty`** 以避免与之同名冲突

## 截图 / Screenshots

编译生成的 `main.pdf` 包含封面、目录、分节页、内容页（公式 / 代码 / 表 / 图）、致谢页。运行下文 "快速开始" 即可获得本地预览。

## 目录结构 / Project Structure

```
zzu-beamer-template/
├── main.tex                    # 入口文件（XeLaTeX 编译）
├── zzubeamer.sty               # 主题：颜色、字体、页眉脚、封面、分节页
├── lstlang0.sty                # MiKTeX listings.cfg 兼容垫片（可选保留）
├── frames/                     # 各类幻灯片片段
│   ├── cover.tex               # 封面
│   ├── toc.tex                 # 目录
│   ├── intro.tex               # 研究背景
│   ├── method.tex              # 方法（公式 / 代码示例）
│   ├── results.tex             # 实验（表格 / 图片示例）
│   ├── conclusion.tex          # 结论
│   ├── bib.tex                 # 参考文献
│   └── thanks.tex              # 致谢
├── figures/                    # Logo 与示例图
│   ├── zzu_logo.pdf            # 校徽（矢量，推荐）
│   ├── zzu_logo.jpg            # 校徽（彩色光栅）
│   └── zzu_name.png            # 校名字样
├── README.md
├── LICENSE
└── .gitignore
```

## 快速开始 / Quick Start

### 依赖 / Prerequisites

- TeX 发行版：TeX Live 2022+ / MiKTeX / MacTeX
- 推荐字体：Windows 自带的 SimSun / SimHei / KaiTi（macOS/Linux 用户首次编译需调整 `ctex` 的 `fontset` 参数）
- 引擎：**XeLaTeX**（CJK 与字体所需）

### 编译 / Compile

在仓库根目录执行：

```bash
xelatex main.tex
xelatex main.tex     # 二次编译以正确解析目录与交叉引用
```

或者使用 `latexmk`：

```bash
latexmk -xelatex main.tex
```

编译产物 `main.pdf` 即为最终幻灯片。

### 个性化 / Customize

最常见的修改：

1. **替换标题、作者、单位、日期** — 编辑 [`main.tex`](main.tex) 中的 `\title{}` / `\author{}` / `\institute{}` / `\date{}` 区块。
2. **替换章节内容** — 编辑 `frames/intro.tex` 等文件，或新增 `frames/your-section.tex` 并在 `main.tex` 用 `\input{frames/your-section.tex}` 引入。
3. **调整主色调** — 在 [`zzubeamer.sty`](zzubeamer.sty) 中修改 `\definecolor{zzured}{HTML}{A33A37}` 即可全局生效。
4. **替换校徽** — 将自己的 logo 放到 `figures/` 并在主题文件用 `\setzzulogo{figures/your_logo.pdf}` 指定。
5. **切换屏幕比例** — `\documentclass[10pt, aspectratio=43, mathserif]{beamer}` 切回 4:3。

## 配色规范 / Color Palette

| 用途 | 颜色名 | HEX | 备注 |
|------|--------|-----|------|
| 主色（标题、强调、链接） | `zzured` | `#A33A37` | 实证提取自官方校徽 |
| 深色变体（阴影、辅强调） | `zzudarkred` | `#7E2A28` | |
| 亮色变体（高亮） | `zzubrightred` | `#C8484A` | |
| 正文文字 | `zzuink` | `#2C2C2C` | 略带暖意的近黑 |
| 辅色（次要文字） | `zzuslate` | `#4D5B78` | 同样从校徽提取 |
| 柔和背景 | `zzucream` | `#F7F3EB` | |
| 装饰金 | `zzugold` | `#C9A14A` | 标题页装饰线 |
| 页脚灰 | `zzugray` | `#8A8A8A` | |

> 注：郑州大学尚未在官网公开发布完整的 VI 视觉识别手册。本模板的色值通过对官方校徽位图（双环红色"人"字版）的像素级颜色聚类实证得出，仅供学术汇报场景使用。如需用于学校正式宣传场合，请咨询学校党委宣传部以获取官方授权色值。

## 致谢与引用 / Acknowledgements & Citation

本模板在组织方式上参考了以下三个开源工作，特此致谢：

- **[pan2013e/ZJU-beamer-template](https://github.com/pan2013e/ZJU-beamer-template)** by Zhiyuan Pan, Zhejiang University. 提供 `frame/format/command` 三段式组织、章节自动分页机制、页眉脚实现思路。
- **[qychen2001/ZJU-Beamer-Template](https://github.com/qychen2001/ZJU-Beamer-Template)** by 光头哥 & PhilFan, Zhejiang University. 启发了 `*.sty + \usepackage{}` 的命名约定与现代化的颜色钩子设计。
- **[ZZUTUG/ZZU-Beamer](https://github.com/ZZUTUG/ZZU-Beamer)** by Fw[a]rd（改编自合工大孙晓教授 Beamer-HFUT）. 既有的郑大 Beamer 主题，本仓库以 `zzubeamer.sty` 与之**显式区分**以避免命名冲突；二者在配色（蓝 vs 红）、版面（导航条 vs 红色横幅）上设计取向不同，可按个人偏好选用。

本仓库的色值（`#A33A37`、`#4D5B78`）通过对官方校徽位图进行像素级颜色聚类**独立实证**得出，非源自上述任一项目。所有 LaTeX 代码均为独立编写。

如果本模板对您的工作有帮助，欢迎引用：

```bibtex
@misc{zzu-beamer-template,
  author       = {zouchenzhen},
  title        = {ZZU Beamer Template: A Beamer template for Zhengzhou University},
  year         = {2026},
  url          = {https://github.com/zouchenzhen/zzu-beamer-template},
}
```

## 许可证 / License

本模板遵循 [MIT License](LICENSE) 开源。校徽与校名图像版权归郑州大学所有，本仓库仅以"合理使用"的范围用于学术汇报场景；商用前请向校方申请授权。

## 反馈 / Feedback

欢迎在 [Issues](https://github.com/zouchenzhen/zzu-beamer-template/issues) 区提交 Bug 报告、改进建议或新功能请求；也欢迎 Pull Request。
