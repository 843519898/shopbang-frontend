# shopbang-frontend

上品帮前端开发规范：供 AI 编程助手在开发、修复和代码审查时使用的 Agent Skill。

适用于上品帮团队的前端项目，也可明确指定在其他项目中采用。不限定项目数量、仓库路径或个人电脑环境。

## 核心规范

- 业务接口统一封装到 `api/`，复用项目的请求客户端。
- Vue 文件顺序为 `template` → `script setup` → `style`，样式使用无 `tw-` 前缀的 UnoCSS。
- 页面保留查询、分页、勾选、刷新和业务编排；组件管理自己的状态与行为。
- 业务弹窗通过 `ref.open(payload)` 打开，自行管理表单、校验、提交和关闭。
- 高内聚、低耦合；参数与事件精简，props、事件载荷和 `open` 入参附必要注释。
- 按完整职责组件化，控制文件数量，不为简单逻辑或单次调用机械拆文件。
- 明确资源生命周期，处理异步竞态、重复订阅和缓存增长，并报告实际验证范围。

完整规则见 [SKILL.md](SKILL.md)。这些是团队约定，包含与部分通用 Vue 指导不同的模板顺序和弹窗调用方式。

## 安装

将此仓库克隆到本地 Codex 的个人 skills 目录：

```sh
git clone https://github.com/843519898/shopbang-frontend.git ~/.codex/skills/shopbang-frontend
```

已有同名目录时先保留本地修改，再选择更新方式。安装后，在支持 Agent Skills 的助手中选择该技能；在 Codex 中可输入：

```text
$shopbang-frontend 按这套规范完成当前前端需求。
```

也可将整个文件夹放入支持 Agent Skills 的工具所使用的技能目录。

## 文件结构

```text
shopbang-frontend/
├── SKILL.md                       # 技能入口与团队规范
├── agents/openai.yaml             # 展示信息
├── references/existing-projects.md # 已知项目示例，按需读取
├── references/resource-lifecycle.md # 资源清理与验证参考
├── README.md
└── LICENSE
```

修改技能时保持接口约定、按需引用和项目实际命令一致；不将特定机器路径、凭据或真实业务数据加入仓库。

## 许可证

[MIT](LICENSE)
