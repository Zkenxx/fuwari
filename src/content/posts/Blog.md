---  
title: Blog创建教程  
published: 2025-03-14  
description: '这个教程将帮助你快速部署一个美观、功能完整的个人博客网站，包括评论功能，完全免费且无需服务器。'  
image: ''  
tags: []  
category: '教程'  
draft: false   
lang: ''  
---  
### 准备工作

1. 注册 [GitHub](https://github.com/) 账号（如果已有可跳过）
2. 准备好以下网址：
   - [Fuwari 模板](https://github.com/saicaca/fuwari)
   - [Netlify 部署平台](https://app.netlify.com/)

### 第一步：部署网站基础版本

1. 访问 [Fuwari](https://github.com/saicaca/fuwari) 仓库
   - 点击右上角的 "Fork" 按钮将项目复制到你的 GitHub 账号
   - 或者下载代码后新建仓库上传（如果希望不公开）

2. 使用 Netlify 部署网站
   - 前往 [Netlify](https://app.netlify.com/)
   - 使用 GitHub 账号登录（首次使用需要授权）
   - 点击 "Add new site" > "Import an existing project"
   - 选择 "GitHub" 并授权
   - 选择你刚刚 Fork 的 Fuwari 仓库
   - 在 "Build Command" 中填写：`astro build`
   - **可选：点击"Site settings"，在"Site information"中自定义你的站点名称（例如改为"myblog"，这样你的网址就会变成`myblog.netlify.app`）**
   - 保持其他设置默认，点击 "Deploy site"

3. 等待部署完成
   - Netlify 会自动分配一个域名（例如 `random-name-123456.netlify.app`）
   - 此时你的网站已经部署成功，但还是使用默认内容

### 第二步：个性化你的博客

1. 基础信息设置
   - 在你的 GitHub 仓库中找到 `/src/config.ts` 文件
   - 修改其中的网站标题、副标题、站长名称、个人简介等信息
   - 提交更改后，Netlify 会自动重新部署

2. 文章管理
   - 博客文章存放在 `/src/content/` 目录中
   - 参考现有示例创建新的 Markdown 文件
   - 每篇文章需要包含前缀（frontmatter）部分，包括标题、日期、标签等信息
   - 前缀格式示例：
     ```
     ---
     title: 我的第一篇博客
     description: 这是一篇测试文章
     date: 2025-03-14
     tags: [博客, 测试]
     ---
     ```

3. 自定义主题和样式（可选）
   - 在 `/src/styles/` 目录中可以修改 CSS 样式
   - 在 `/src/components/` 中可以修改网站组件

### 第三步：添加评论功能

1. 配置 Giscus
   - 访问 [giscus.app](https://giscus.app/)
   - 如果首次使用，需要安装 Giscus GitHub App
   - 点击 "安装" 按钮，授权给你的仓库

2. 启用 Discussions 功能
   - **注意：如果你的博客代码仓库是私有的，需要新建一个公开仓库专门用于评论功能**
   - **如果使用单独的评论仓库：创建一个新的公开仓库（例如命名为`blog-comments`）**
   - 返回到你的 GitHub 仓库（或者新创建的评论仓库）
   - 点击 "Settings" 选项卡
   - 向下滚动找到 "Features" 部分
   - 勾选 "Discussions" 选项并保存

3. 配置 Giscus 并集成到博客
   - 返回 [giscus.app](https://giscus.app/)
   - 在 "仓库" 字段中输入 `你的用户名/仓库名`
     - 如使用博客仓库：`username/fuwari`
     - 如使用单独评论仓库：`username/blog-comments`
   - 选择合适的讨论分类（通常选择 "Announcements"）
   - 选择 "使用 Discussion 的标题" 作为映射关系
   - 选择 "只有具有写入权限的人可以评论" 作为权限设置
   - 复制生成的 "启用 giscus" 代码段

4. 将评论功能集成到博客模板
   - 在 Fuwari 中，你可以编辑 `/src/layouts/BlogPost.astro` 文件
   - 找到文章内容结束的位置（通常在 `<article>` 标签结束之后）
   - 粘贴之前复制的 Giscus 代码

### 本地开发环境设置（可选）

如果你想在本地预览和开发你的博客：

1. 安装必要的软件
   - 安装 [Node.js](https://nodejs.org/)（建议选择 LTS 版本）
   - 安装完成后重启电脑确保环境变量生效

2. 下载和安装项目
   - 克隆或下载你的 Fuwari 仓库到本地
   - 打开命令提示符（Win+R 然后输入 `cmd`）
   - 进入项目目录：`cd /d 项目目录路径`
   - 执行以下命令：
     ```
     npm install -g pnpm
     pnpm install
     pnpm add sharp
     ```

3. 启动本地开发服务器
   - 执行 `npm run dev`
   - 打开浏览器访问显示的本地地址（通常是 `http://localhost:4321/`）

完成以上步骤后，你将拥有一个功能完整的个人博客，包括评论系统，而且完全免费！

<script src="https://giscus.app/client.js"
        data-repo="Linyoux/LinYou_commits"
        data-repo-id="R_kgDOOIhNng"
        data-category="Announcements"
        data-category-id="DIC_kwDOOIhNns4CoBfK"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="bottom"
        data-theme="preferred_color_scheme"
        data-lang="zh-CN"
        crossorigin="anonymous"
        async>
</script>
