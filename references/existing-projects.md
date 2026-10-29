# 现有项目参考

这些是已知项目示例，不是本 skill 的适用范围限制。以当前检出的文件和脚本为准，不依赖个人机器路径。

| 目录 | 用途 | 主要入口 |
| --- | --- | --- |
| `bang-erp/` | ERP 前端，包含 Ozon、Wildberries、Mercado 业务 | `src/main.js`、`src/router/`、`src/pages/` |
| `agent-system/` | 管理后台前端 | `src/main.js`、`src/router/`、`src/pages/` |
| `img-edit/` | 可复用的 `@shopbang/img-editor` 图片编辑组件 | `src/index.js`、`src/EditSkuImgs.vue`、`playground/` |

三个项目各有 Git 仓库和依赖，使用 Vue 3、Vite、Ant Design Vue 和 UnoCSS；Tailwind 等样式工具以各自配置为准。ERP 的平台页面分布在 `src/pages/ozon/`、`src/pages/wb/`、`src/pages/mercado/`，根据需求检查是否需要覆盖多个平台。路由修改先查看 `src/router/`。

## 图片编辑组件联动

`img-edit` 由宿主注入请求、上传、store、路由和编辑器实现。涉及公共 props/events 或导出时，检查 `src/index.js`、注入依赖和消费方调用，保持已有消费方兼容，仅在任务涉及双方时同步修改。

`bang-erp` 通过 `@shopbang/img-editor` 消费组件。联动验证应核实宿主实际使用的包版本或本地链接，本地组件源码修改不代表自动进入 ERP。使用 `playground/` 验证组件交互，不为验证自行发布包。

## 已有命令

以下仅供定位，执行前确认当前 `package.json`：

| 项目 | 开发 | 验证 |
| --- | --- | --- |
| `bang-erp` | `npm run dev:test` / `npm run dev:prod` | `npm run build:test` / `npm run build:prod`；可对改动文件运行 `npx eslint <文件路径>` |
| `agent-system` | `npm run dev:test` / `npm run dev:prod` | `npm run build:test` / `npm run build:prod` |
| `img-edit` | `npm run dev` | playground 手动交互；`npm run preview` 预览已有构建产物 |

这三个项目此前没有统一的 `test` 脚本，`img-edit` 此前没有 `build` 脚本。不要把这点推广到其他项目，也不要在脚本新增后仍按旧情况判断。
