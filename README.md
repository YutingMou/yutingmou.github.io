# Yuting Mou 个人主页 — 使用说明

## 目录结构

```
site/
├── index.html              首页（简介 + 研究方向 + 招生信息）
├── publications.html       Publications（期刊、会议论文、报告）
├── students-teaching.html  Students & Teaching（教学、学生指导、学术服务）
├── projects-awards.html    Projects & Awards（科研项目、获奖）
├── css/
│   └── style.css           全站统一样式
├── images/                 所有图片放在这里
│   ├── YutingMou.jpg
│   ├── research-framework-en.png
│   ├── ev-grid-integration.png
│   ├── market-clearing-algorithm.png
│   └── capacity-remuneration-mechanism.png
└── pdfs/                   所有 PDF 放在这里
    ├── CV_YutingMOU.pdf
    ├── Mou2025.pdf
    ├── Mou2023b.pdf
    └── Mou2023a.pdf
```

## 重要：替换占位文件

`images/` 和 `pdfs/` 文件夹里目前放的是**占位文件**（灰色方块图 / 空白 PDF），
只是为了让网站能正常显示、链接不报 404。

**请用你的真实文件替换它们，文件名保持完全一致即可**（包括大小写），网站会自动生效：

| 占位文件名 | 对应原文件 |
|---|---|
| `images/YutingMou.jpg` | 你的证件照 |
| `images/research-framework-en.png` | 原 `研究框架EN.png` |
| `images/ev-grid-integration.png` | 原 `电动汽车-国自然.png` |
| `images/market-clearing-algorithm.png` | 原 `出清算法.png` |
| `images/capacity-remuneration-mechanism.png` | 原 `容量补偿机制.png` |
| `pdfs/CV_YutingMOU.pdf` | 你的简历 |
| `pdfs/Mou2025.pdf` | Utilities Policy 2025 论文 |
| `pdfs/Mou2023b.pdf` | Energy Policy 2023 论文 |
| `pdfs/Mou2023a.pdf` | Electric Power Systems Research 2023 论文 |

如果以后要新增论文 PDF，直接放进 `pdfs/` 文件夹，再去 `publications.html` 里
对应的 `<li>` 加一行 `<a class="pdf-link" href="pdfs/你的文件名.pdf" target="_blank">PDF</a>` 即可。

新增图片同理，放进 `images/`，在对应页面里用 `<img src="images/你的文件名.png">` 引用。

## 改动说明

1. **分成 4 个页面**：原来单页面的内容按逻辑拆分为 Home / Publications /
   Students & Teaching / Projects & Awards，每页通过左侧固定导航栏切换，
   长内容（尤其是论文列表和学生名单）不再需要在一个页面里无限下拉。

2. **文件分类**：图片统一放 `images/`，PDF 统一放 `pdfs/`，CSS 单独放 `css/`，
   不再和 HTML 混在根目录，方便维护、也方便 Git 管理。

3. **视觉美化**：
   - 左侧固定个人信息栏（头像、职位、联系方式、导航），仿照 MIT / Stanford
     教授主页的常见布局
   - 配色为蓝灰 + 暖棕金点缀（`#1E3A5F` 主色，`#8C6D46` 强调色），克制不花哨
   - 标题用衬线字体（Source Serif 4 / Noto Serif SC），正文用 Inter / Noto Sans SC，
     年份和编号用等宽字体 IBM Plex Mono，增强学术排版的层次感
   - 论文列表改为带编号、可点击 PDF 标签的卡片式列表，比原来的纯文字列表更易扫读
   - "近期研究内容"改为时间轴风格的卡片展示
   - 移动端做了响应式适配（导航栏会变成顶部横向菜单）

## 本地预览

直接在 `site/` 目录下用任意静态服务器打开，例如：

```bash
cd site
python3 -m http.server 8000
```

然后浏览器打开 `http://localhost:8000`。

## 部署到 GitHub Pages

把 `site/` 文件夹里的全部内容（包括替换后的真实图片和 PDF）放到你的
`yutingmou.github.io` 仓库根目录下，提交并 push 即可，GitHub Pages 会自动生效。

如果你想把网站放在子目录而不是仓库根目录，记得检查所有 HTML 文件里的相对路径
（`css/style.css`、`images/...`、`pdfs/...`）是否仍然正确——目前全部用的是相对路径，
只要相对层级不变，放在哪个目录都没问题。
