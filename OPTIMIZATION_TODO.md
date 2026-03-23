# spec-kit-zh 优化点清单

## P0：优先处理

### 1. 统一所有 CLI 展示品牌
- 将 `version`、`doctor`、`extension` 子命令中的 `Specify CLI`、`specify`、英文旧提示统一为：
  - 分发包：`specify-cli-zh`
  - 命令名：`specify-zh`
- 重点检查：
  - 成功提示
  - 错误提示
  - 面板标题
  - help 文本
  - 示例命令

### 2. 完成 extension 子系统中文化收口
- 目前 `extension info/update/enable/disable` 仍有明显英文残留。
- 需要统一：
  - `Error`
  - `Install`
  - `To remove`
  - `Updates available`
  - `Up to date`
  - `Cancelled`
  - `Not installed`
  - `Verified`
  - `Requirements`
  - `Provides`
  - `Tags`
  - `Statistics`

### 3. 增加安装验证说明
- 增加一份安装后验证清单：
  - `specify-zh --help`
  - `specify-zh version`
  - `specify-zh check`
- 明确“安装包名”和“执行命令名”的区别。

### 4. 增加发布前 smoke test
- 至少覆盖：
  - `uv tool install specify-cli-zh --from git+...`
  - `specify-zh --help`
  - `specify-zh init --help`
  - `specify-zh check`
- 目标是防止包名、入口命令、版本读取再次脱节。

## P1：强烈建议处理

### 5. 给 `specify-zh doctor` 增加更细的诊断结果
- 增加：
  - 当前分发包名
  - 当前命令入口名
  - GitHub Token 检测建议
  - 下载模板失败时的离线方案
- 输出结构建议统一成：
  - 现状
  - 风险
  - 修复命令

### 6. 增强 `init` 的交互体验
- 缺失参数时自动进入引导式初始化。
- 建议补：
  - 当前目录/新目录选择
  - AI agent 选择说明
  - 初始化摘要确认
  - 检测到已有 `.specify/` 时的处理选项

### 7. 增加 `init --dry-run`
- 预览将创建哪些目录、哪些文件、哪些 agent 目录。
- 明确哪些文件会覆盖。

### 8. 增加 `init --json`
- 方便脚本或 CI 集成。
- 输出建议包含：
  - project path
  - ai agent
  - generated files
  - warnings
  - skills installed

### 9. 优化 `check` 展示层
- 增加汇总区：
  - 已安装 CLI 数量
  - 缺失 CLI 数量
  - 推荐优先安装项
- 把 `IDE 型 agent，无需 CLI 检测` 这类提示做得更短更整齐。

### 10. `version` 命令增强
- 显示：
  - 分发包名：`specify-cli-zh`
  - 命令入口：`specify-zh`
  - 当前模板来源仓库
  - 本地运行还是已安装运行

## P2：体验增强

### 11. README 首页结构再优化
- 增加“3 分钟上手”
- 增加“安装包名 vs 运行命令”说明卡片
- 增加“我应该用哪个命令？”小节

### 12. 顶部徽章继续优化
- 可补：
  - version badge
  - latest release badge
  - docs status badge
- 统一视觉风格，避免混杂不同来源的 badge 样式。

### 13. 文档语言一致性继续收尾
- README 和 docs 中仍有少量英文段落没有完全本地化。
- 建议统一：
  - 中文正文
  - 英文保留仅用于命令、参数、术语、外链标题

### 14. 增加 migration guide
- 增加从以下项目迁移到 `spec-kit-zh` 的说明：
  - `spec-kit`
  - `spec-kit-cn`
- 说明：
  - 哪些目录可复用
  - 哪些模板建议重生成
  - 如何避免覆盖已有 agent 命令

### 15. 增加“常见安装问题”文档
- 单独列出：
  - `Executable already exists`
  - GitHub API rate limit
  - 缺少 `typer`
  - 当前目录非空
  - agent CLI 未安装
- 每个问题给出一条直接可复制的解决命令。

## P3：工程质量与维护性

### 16. 为展示文案增加测试
- 增加 CLI 输出快照或关键断言：
  - `check`
  - `doctor`
  - `version`
  - `extension search/info/update`
- 防止后续又混回英文或旧命令名。

### 17. 抽取统一文案常量
- 将高频品牌词和常用提示抽成常量：
  - `specify-cli-zh`
  - `specify-zh`
  - banner tagline
  - 常见错误模板
- 降低后续修改成本。

### 18. 统一 README/docs 中的术语规则
- 明确哪些词固定保留英文：
  - Spec
  - Plan
  - Tasks
  - Extension
  - Catalog
  - Agent
  - Skill
- 避免同一概念多种翻译。

### 19. 补一份发布检查清单
- 发布前检查：
  - `pyproject.toml` 版本
  - `CHANGELOG.md`
  - 命令入口
  - 安装文档
  - smoke test
  - README 顶部 badge
  - docs 链接有效性

### 20. 增加 CI 校验
- 校验：
  - README 中不应再出现旧安装命令
  - `pyproject.toml` 包名与文档一致
  - `specify-zh` 入口存在
  - `CHANGELOG` 已更新

## P4：功能扩展与深度本地化

### 21. 国内网络加速与镜像指引
- 在 `init` 或 `extension install` 阶段，如果检测到网络超时或下载极慢，给出国内代理或镜像源设置指南。
- 针对部分受限资源的下载（例如官方库访问不畅），探索提供国内镜像或配置指引的可能性。

### 22. AI 指令（Prompt）模板深度本地化与调优
- 除了 CLI 本体输出外，彻底检查并翻译生成的各工具 AI 指令模板（例如初始化时注入到 `.claude/commands/`、`.cursor/commands/` 等目录下的内容）。
- 结合国内团队习惯，优化提示词表达结构，确保国内使用者用 AI 生成的代码和文档更符合习惯。

### 23. 探索国内主流大模型/工具生态接入
- 调研并逐步拓展对国内主流 AI 编码工具或 CLI（如果有）的集成与支持。
- 在文档中增加使用国内大模型（例如通义灵码、DeepSeek 等）配合 Spec-Driven Development 的最佳实践或 Workaround。

### 24. 建立与上游版本（Upstream）的同步基准和机制
- 制定当原版 `spec-kit` 和 `specify` 更新时的版本同步与合并策略：
  - 基于 GitHub Actions 定期检测并同步上游 Release 或代码变更。
  - 自动高亮有文本变更的地方以便快速进行中文化翻译。
  - 明确主版本号和修补版本号的跟随规则。

### 25. 中文文档死链与一致性自动扫描
- 在 CI 中加入 Markdown 链接检查工具，扫描 README 及 docs 目录中的内外超链接。
- 防止翻译过程中导致的本地锚点失效或外部链接 404，确保指向原英文版和本地中文版文件的界限清晰正确。
