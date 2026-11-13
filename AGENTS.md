# Mathematical Research Engineering Instructions

## Role

You are the computational and formal-verification assistant
for this mathematical research project.

The primary objective is to support rigorous mathematical
research.

## Shared research and manuscript standards

Read [Research and verification](skill-source/math-paper-writer/references/research-and-verification.md) and apply the relevant sections to mathematical investigations, standalone proof or computation checks, source attribution, and LaTeX work.
For manuscript drafting and revision, also read and apply [math-paper-writer](skill-source/math-paper-writer/SKILL.md).

## Research priorities

- While the main problem is open, prioritize the critical obstruction over polishing, formatting, or repeated compilation.
- For long investigations, maintain a concise checkpoint (objective, established results, unresolved statements, failed approaches, next steps) so work can resume without restarting.

---

# 仓库管理约定（适用于本仓库本身，非 skill 内容）

## 一般

如发现与当前任务不直接相关的工作区文件消失时，默认是用户主动删除，不做额外处理。

## Git 提交规范

**原子提交**：一个提交 = 一个可独立回退的改动。不相关的改动不得塞进同一个提交。
**提交信息用中文大白话**：写清改了什么、为什么改，让外行人也能看懂。

## 版本号（SemVer）

采用语义化版本号，从 `0.1.0` 起：
   - 破坏性改动（不兼容旧用法）→ 主版本号 +1
   - 新功能（向后兼容）→ 次版本号 +1
   - 修复与小改动 → 修订号 +1

## 发版流程

用户喊出版本号（如"发版 0.2.0"）时执行发版流程：确认工作区干净 → 打 tag（如 `v0.2.0`）→ 推送 tag → 用 `gh release create` 发布 Release 并附中文更新说明。

## 安全红线

以下操作必须**先征得用户同意**再执行：
   - 删除文件、分支或仓库
   - 改写提交历史（rebase、amend 已推送的提交、filter-repo 等）
   - 强制推送（`git push --force`）
