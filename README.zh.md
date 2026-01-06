# Deep Research Skill for Claude Code

[English](README.md) | [中文](README.zh.md)

> 灵感来源：[RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context](https://arxiv.org/abs/2511.18743)

Claude Code 的结构化调研工作流技能，支持两阶段调研：outline生成（可扩展）和深度调查。人在回路设计确保每个阶段的精确控制。

## 使用场景

- **学术研究**：论文综述、benchmark评测、文献分析
- **技术研究**：技术对比、框架评估、工具选型
- **市场研究**：竞品分析、行业趋势、产品比较
- **尽职调查**：公司研究、投资分析、风险评估

## 安装

```bash
# 中文版
cp -r skills/research-zh ~/.claude/skills/research

# 英文版
cp -r skills/research-en ~/.claude/skills/research

# 必需：安装agent
cp agents/web-search-agent.md ~/.claude/agents/
```

## 命令

> **注意**：使用 `run /research` 而非直接 `/research`，因为斜杠命令与内置命令冲突。

| 命令 | 描述 |
|------|------|
| `run /research` | 生成包含items和fields的调研outline |
| `run /research/add-items` | 向现有outline添加更多items |
| `run /research/add-fields` | 向现有outline添加更多fields |
| `run /research/deep` | 使用并行agents对每个item进行深度调研 |
| `run /research/report` | 从JSON结果生成markdown报告 |

## 工作流 & 示例

> **示例**：调研 "AI Agent Demo 2025"

### 阶段1：生成Outline
```
run /research AI Agent Demo 2025
```
💡 **发生了什么**：告诉它你要研究什么 → 它帮你列出调研清单

**你会得到**：17个待调研的AI Agent清单（ChatGPT Agent、Claude Computer Use、Cursor等）+ 每个要收集哪些信息

### 阶段2：深度调研
```
run /research/deep
```
💡 **发生了什么**：AI自动上网搜索每个item的详细信息，逐个完成

**你会得到**：每个Agent的详细资料（公司、发布日期、定价、技术规格、用户评价...）

### 阶段3：生成报告
```
run /research/report
```
💡 **发生了什么**：所有数据 → 一份整理好的报告

**你会得到**：`report.md` - 带目录的完整Markdown报告，可直接阅读或分享

## 遇到问题？

如果过程中有什么不懂的，可以让Claude Code帮你理解这个项目：
```
帮我理解这个项目: https://github.com/Weizhena/deep-research-skills
```

## 参考文献

- RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context

## 许可证

MIT
