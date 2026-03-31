# OpenCode 与 Claude Code 使用方式对比

## OpenCode

**特点：**
- **默认 TUI 模式**：启动后直接进入图形化的终端界面
- **多模型支持**：支持多个 AI 提供商的模型
- **Web 界面**：`opencode web` 可启动浏览器界面
- **服务器模式**：可作为 headless 服务器运行，支持远程连接
- **GitHub 集成**：内置 `opencode pr` 命令直接处理 PR
- **Agent 系统**：支持管理多个自定义 Agent
- **会话持久化**：支持导入/导出会话数据
- **统计功能**：显示 token 使用和成本统计
- **基于 Bun**：使用 Bun 运行时

**典型使用：**
```bash
opencode                    # 启动 TUI
opencode web                # 启动 Web 界面
opencode run "帮我写代码"    # 直接运行一条命令
opencode pr 123             # 处理 GitHub PR
```

---

## Claude Code

**特点：**
- **纯命令行交互**：逐条对话，无 TUI
- **仅 Claude 模型**：专为 Anthropic Claude 优化
- **计划模式**：`/plan` 进入设计模式，实现前先规划
- **技能系统**：内置和自定义技能，如 `/commit`
- **工作树支持**：`/worktree` 创建隔离开发环境
- **任务管理**：内置任务列表跟踪进度
- **自动记忆**：跨会话记忆项目偏好和模式
- **钩子系统**：配置 shell 命令在事件触发时执行
- **权限模式**：精细控制工具使用权限

**典型使用：**
```bash
claude-code                # 直接对话
/commit                    # 使用提交技能
/plan                      # 进入计划模式
/worktree                  # 创建工作树
```

---

## 核心区别总结

| 特性 | OpenCode | Claude Code |
|------|----------|-------------|
| 界面模式 | TUI + Web | 纯命令行 |
| 模型支持 | 多提供商 | 仅 Claude |
| 远程访问 | 原生支持 | 不支持 |
| PR 集成 | 内置命令 | 需手动操作 |
| 开发流程 | 即时执行 | 计划先行 |
| 会话管理 | 导入/导出 | 自动记忆 |

---

## 选择建议

- **选择 OpenCode**：偏好图形化界面、需要多模型、远程协作
- **选择 Claude Code**：偏好快速命令行、深度 Claude 集成、项目规划流程
