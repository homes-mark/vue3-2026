# Vue 3 案例练习

## 仓库目的

用同一个 Vue 3 + Vite 项目练习不同案例，通过 Git 提交记录每个案例的实现过程。当前版本是初始化模板，尚未加入练习案例。

## 下载到本地并运行

建议使用 Node.js 22.12 或更新的 LTS 版本。

**方式一：用 Git 克隆**（保留提交历史）。

```sh
git clone https://github.com/homes-mark/vue3-2026.git
cd vue3-2026
```

**方式二：[下载 ZIP](https://github.com/homes-mark/vue3-2026/archive/refs/heads/main.zip)**（无需安装 Git）。解压后，在包含 `package.json` 的目录打开终端。

两种方式下载后，都运行以下命令：

```sh
npm ci
npm run dev
```

打开终端显示的本地地址即可预览，按 `Ctrl+C` 停止开发服务器。需要生成生产构建时，运行 `npm run build`。

## 仓库内容

| 位置 | 内容 |
| --- | --- |
| [`src/`](./src/) | Vue 应用源码，包括入口、根组件、示例组件和样式。 |
| [`public/`](./public/) | 网站图标等静态资源。 |
| [`package.json`](./package.json) 和 [`package-lock.json`](./package-lock.json) | 项目依赖、运行命令及锁定的依赖版本。 |
| [`vite.config.js`](./vite.config.js) | Vite 构建配置。 |

要下载旧版本，在 GitHub 的提交历史中找到对应提交，选择「浏览文件」，再通过「代码 → 下载 ZIP」下载。得到的是该提交时的完整项目，不只是这次改动的文件。
