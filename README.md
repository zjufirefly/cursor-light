## 服装样品展示单页应用（Vue 3 + TypeScript + Tailwind）

一个使用 **Vue 3 + TypeScript + Vite + Tailwind CSS** 搭建的单页应用，主题为服装公司样品展示，包含固定顶部导航栏、服装分类展示主内容区以及页脚信息。

### 技术栈

- **框架**：Vue 3（组合式 API，`<script setup>`）
- **语言**：TypeScript
- **构建工具**：Vite
- **样式**：Tailwind CSS，深色主题（`#1a1a1a` 背景，橙色 `#ffa500` 强调色）

### 主要功能与布局

- **固定导航栏**
  - 左侧：Logo 与品牌文案
  - 中间：导航链接（首页、产品、关于我们、联系方式）
  - 右侧：搜索输入框，支持关键字搜索样品（版型、面料、场景等）

- **主内容区**
  - 上方为简洁的品牌介绍与视觉样片图片组合（参考精品服装设计展示风格）
  - 中部为「样品分类一览」，按类别展示卡片网格：
    - 廓形外套、礼服 & 晚装、日常基础款、运动与机能
  - 支持：
    - 关键字搜索（标题、描述、标签）
    - 类别筛选（桌面端为按钮组，移动端为下拉选择）

- **关于我们 & 联系方式**
  - 简要介绍工作室定位与样品应用场景
  - 显示邮箱、电话及工作室地址

- **页脚**
  - 版权声明
  - 技术栈标记（Vue 3 & Tailwind CSS）

### 目录结构（核心部分）

- `index.html`：应用入口 HTML
- `src/main.ts`：Vue 应用入口
- `src/App.vue`：整体页面布局和数据逻辑
- `src/components/TopNav.vue`：顶部导航栏（含搜索框）
- `src/components/CollectionGrid.vue`：服装样品网格展示组件
- `src/components/SiteFooter.vue`：页脚
- `src/assets/tailwind.css`：Tailwind 入口样式文件

### 本地运行

1. 安装依赖

```bash
npm install
```

2. 启动开发服务器

```bash
npm run dev
```

打开终端输出中给出的本地地址（默认 `http://localhost:5173`）即可预览页面。

3. 构建生产包

```bash
npm run build
```

4. 预览生产构建

```bash
npm run preview
```

### 代码风格与校验

- 使用 ESLint + `@vue/eslint-config-typescript` 进行基础代码规范约束。
- 运行代码检查：

```bash
npm run lint
```

