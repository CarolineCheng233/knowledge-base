---
name: knowledge-base
description: "管理个人知识库：创建日记、周报、月报、Bug记录、经验总结、工具收集、项目记录、学习笔记。支持按关键词检索知识库内容，汇总生成周报/月报。当用户提到写日记、记录bug、记笔记、搜索知识库、总结本周/本月等场景时触发。"
---

# 个人知识库管理

## 知识库路径

`/Users/chy/Documents/knowledgeBase/`

## 目录结构

| 目录 | 用途 |
|------|------|
| `diary/` | 日记 |
| `weekly/` | 周报 |
| `monthly/` | 月报 |
| `bugs/` | Bug记录 |
| `experience/` | 经验总结 |
| `tools/` | 工具收集 |
| `projects/` | 项目记录 |
| `learning/` | 学习笔记 |

## 命名规则

所有文件统一命名为：`YYYY-MM-DD-中文标题.md`

示例：`2025-01-15-代理连接问题.md`

## 核心工作流

### 创建条目

1. 根据用户意图识别内容类型
2. 读取 `references/templates.md` 中对应模板
3. 用实际内容填充模板（保留 YAML frontmatter）
4. 写入到对应目录，文件名遵循命名规则

### 检索内容

1. 用 Grep 在 `/Users/chy/Documents/knowledgeBase/` 下搜索关键词
2. 用 Read 读取匹配的文件
3. 向用户总结呈现相关内容

### 生成报告

1. 确定时间范围（本周/本月）
2. 用 Glob 找到时间范围内的条目（按文件名日期前缀匹配）
3. 读取并汇总这些条目
4. 按周报/月报模板生成报告文件

## 模板参考

所有内容类型的模板定义在 `references/templates.md` 中。创建条目前务必先读取对应模板。
