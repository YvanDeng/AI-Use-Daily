# iOS 开发 OpenCode 日常任务清单

---

## 📦 项目管理

| 任务 | 命令/操作 |
|------|----------|
| 克隆项目 | `git clone <repo>` |
| 切换分支 | `git checkout -b feature/xxx` |
| 拉取最新 | `git pull origin main` |
| 查看改动 | `git status`, `git diff` |
| 提交代码 | `git add . && git commit -m "xxx"` |
| 推送代码 | `git push` |

---

## 🔧 代码操作

| 任务 | 命令/操作 |
|------|----------|
| 查找文件 | `grep "关键字" **/*.swift` |
| 查看文件结构 | `ls -la`, `find . -name "*.swift"` |
| 创建新文件 | `touch xxx.swift` |
| 查看代码 | `read` 工具读取文件 |
| 修改代码 | `edit` 工具编辑 |
| 重构代码 | 告诉 AI 帮你重构 |

---

## 🧪 构建与测试

| 任务 | 命令/操作 |
|------|----------|
| 安装依赖 | `pod install` / `bundle install` |
| 构建项目 | `xcodebuild` 或 `xcodebuild -workspace` |
| 运行测试 | `xcodebuild test` |
| 清理构建 | `xcodebuild clean` |

---

## 🔍 代码审查

| 任务 | 命令/操作 |
|------|----------|
| 搜索代码 | `grep` 查找函数/类 |
| 查看历史 | `git log --oneline -10` |
| 对比分支 | `git diff main..feature/xxx` |
| 查找 Bug | 贴错误日志让 AI 分析 |

---

## 📝 文档与报告

| 任务 | 命令/操作 |
|------|----------|
| 生成项目结构分析 | "帮我分析项目结构" |
| 写 README | 让 AI 帮你写项目文档 |
| 生成接口文档 | 让 AI 根据代码生成 |
| 写提交信息 | `git commit` 时让 AI 生成 |

---

## 🔧 自动化脚本

| 任务 | 命令/操作 |
|------|----------|
| 批量重命名 | `rename` 命令 |
| 批量修改 | `sed` / `awk` |
| 格式化代码 | `swiftformat` |
| 运行脚本 | `./script.sh` |

---

## 🌐 网络与调试

| 任务 | 命令/操作 |
|------|----------|
| 测试 API | `curl` 命令 |
| 查看网络请求 | `Charles` / `mitmproxy` |
| 模拟数据 | 让 AI 生成 Mock 数据 |

---

## 📱 iOS 特定

| 任务 | 命令/操作 |
|------|----------|
| 查看设备列表 | `xcrun simctl list devices` |
| 启动模拟器 | `xcrun simctl boot "iPhone 15"` |
| 安装 App | `xcrun simctl install booted xxx.app` |
| 清理 DerivedData | `rm -rf ~/Library/Developer/Xcode/DerivedData` |
| 查看崩溃日志 | `log show --predicate 'eventMessage contains "Exception"'` |

---

## 📊 数据与分析

| 任务 | 命令/操作 |
|------|----------|
| 导出崩溃日志 | `grep` + `cut` 处理 |
| 分析性能 | `Instruments` 启动 |
| 统计代码行数 | `find . -name "*.swift" -exec wc -l {} +` |

---

## 🛠️ 常用快捷操作

| 场景 | 操作 |
|------|------|
| 不知道命令 | 直接问 AI |
| 忘记语法 | 让 AI 解释 |
| 遇到报错 | 贴给 AI 分析 |
| 写单元测试 | 让 AI 生成 |
| 代码优化 | 让 AI 优化 |

---

## 📋 每日工作流

### 早上
- [ ] 拉取最新代码 (`git pull`)
- [ ] 查看任务列表
- [ ] 了解今日需求

### 白天
- [ ] 写代码 (Cursor/Trae)
- [ ] 遇到问题 (问 AI)
- [ ] 运行测试
- [ ] 代码审查

### 晚上
- [ ] 提交代码 (让 AI 写 commit message)
- [ ] 推送代码
- [ ] 写每日总结

---

## 🤖 AI 协同工作流

```
需求 → 分析(Trae) → 编码(Cursor) → 测试(OpenCode) → 提交(OpenCode)
```

---

*由 OpenCode 自动生成*
