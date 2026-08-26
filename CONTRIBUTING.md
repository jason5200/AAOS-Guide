# 贡献指南

感谢你愿意为 AAOS-Guide 贡献！无论是纠错、补充内容，还是提出建议，都非常欢迎。

## 如何贡献

### 1. 报告问题（Issue）

如果你发现错误或有改进建议，请提交 Issue，并尽量包含：

- 问题的具体描述
- 相关章节/文件的链接
- 期望的改进方向

### 2. 提交代码/内容（Pull Request）

1. **Fork** 本仓库
2. 克隆到本地：`git clone https://github.com/<你的用户名>/AAOS-Guide.git`
3. 创建分支：`git checkout -b feature/你的改动`
4. 修改内容
5. 提交：`git commit -m "docs: 描述你的改动"`
6. 推送：`git push origin feature/你的改动`
7. 发起 **Pull Request**

## 内容规范

- **准确性优先**：示例代码请标明是否在 AAOS 模拟器或真机上跑过。
- **版本**：源码路径默认对照 [AOSP_VERSION.md](AOSP_VERSION.md)；改路径时请写明标签。
- **标题层级**：文章用 `##` 作为主标题，`###` 作为小节。
- **配图**：架构图使用 Mermaid 或 draw.io 源文件，放在 `assets/` 目录。
- **代码块**：标注语言（如 ` ```kotlin `）。
- **语言**：中文为主，专业术语可保留英文。

## 提交信息规范

遵循 Conventional Commits 风格：

- `docs:` 文档/文章内容
- `feat:` 新增特性
- `fix:` 修复错误
- `chore:` 杂项

## 行为准则

- 尊重他人，保持友善
- 技术讨论对事不对人
- 共同维护良好的学习氛围
