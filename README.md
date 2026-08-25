<div align="center">

# AAOS-Guide 🚗

**车载 Android（Android Automotive OS）系统学习路线与实战教程 —— 从零搭建智能座舱认知**

[![Stars](https://img.shields.io/github/stars/jason5200/AAOS-Guide?style=social)](https://github.com/jason5200/AAOS-Guide)
[![Forks](https://img.shields.io/github/forks/jason5200/AAOS-Guide?style=social)](https://github.com/jason5200/AAOS-Guide)
[![License](https://img.shields.io/github/license/jason5200/AAOS-Guide)](https://github.com/jason5200/AAOS-Guide)
[![Visitors](https://komarev.com/ghpvc/?username=jason5200&repo=AAOS-Guide&color=blueviolet)](https://github.com/jason5200/AAOS-Guide)

</div>

---

## 📌 为什么有这个仓库

网上车载 Android（AAOS）的资料零散、门槛高：要么是官方文档太抽象，要么是碎片化的博客，缺少一条**从「手机 Android」过渡到「车载 Android」的清晰路径**。

本仓库目标：做一张**车载 Android 学习路线图**，用「概述 + 源码 + 实战 Demo + 系列文章」的方式，帮你建立对智能座舱系统的完整认知。

## 🧭 学习路线总览

```
手机 Android 基础
      │
      ▼
00 车载 Android 全景（AAOS 是什么、和手机 Android 的区别）
      │
      ├── 01 CarService 架构与核心服务
      ├── 02 CarService API（车辆属性 / CarPropertyManager）
      ├── 03 多屏显示与适配
      ├── 04 车机性能（启动 / 流畅度 / 稳定性）
      └── 05 AI 上车（语音 / 大模型 / 端侧推理）
```

## ✨ 特性

- ✅ 体系化学习路线，标注前置知识与难度
- ✅ 每篇配合源码解读与可运行 Demo
- ✅ 与 `Framework-Source-Note`、`Car-Launcher-Demo`、`AI-Android-Demo` 仓库联动
- ✅ 开放共建，欢迎 PR 补充与纠错

## 🗂️ 目录结构

```
AAOS-Guide/
├── README.md                 # 本文件：路线图 + 导航
├── 00-overview/              # 车载 Android 全景：AAOS vs 手机 Android
├── 01-car-service/           # CarService 架构与核心服务
├── 02-carservice-api/        # 车辆属性、CarPropertyManager
├── 03-multi-display/         # 多屏显示与适配
├── 04-perf/                  # 车机启动、流畅度、稳定性
├── 05-ai-integration/        # AI 上车：语音、大模型、端侧推理
└── assets/                   # 图片、架构图
```

## 📚 系列文章

| 序号 | 目录 | 文章 | 状态 |
|------|------|------|------|
| 00 | 00-overview | 《车载 Android 全景：AAOS 到底是什么》 | ✅ 已发布 |
| 01 | 01-car-service | 《CarService 架构：从 SystemServer 到车辆服务》 | ✅ 已发布 |
| 02 | 02-carservice-api | 《CarPropertyManager：如何读写车辆属性》 | ✅ 已发布 |
| 03 | 03-multi-display | 《车机多屏显示：从 Display 到 Surface 的链路》 | ✅ 已发布 |
| 04 | 04-perf | 《车机冷启动优化实战》 | ✅ 已发布 |
| 05 | 05-ai-integration | 《大模型上车：端侧推理的可行方案》 | ✅ 已发布 |
| 06 | 05-ai-integration | 《车载语音助手：从 ASR 到 LLM》 | ✅ 已发布 |
| 07 | 05-ai-integration | 《Agent 在车机场景的应用》 | ✅ 已发布 |
| 08 | 05-ai-integration | 《端侧 AI 的工程化实践》 | ✅ 已发布 |
| 09 | 06-audio | 《CarAudioService：车载音频管理》 | ✅ 已发布 |
| 10 | 07-ota | 《车载 OTA 升级：从差分包到 A/B 分区》 | ✅ 已发布 |
| 11 | 08-permission | 《CarService 权限模型：系统权限与驾驶分心》 | ✅ 已发布 |
| 12 | 09-rag | 《车载 RAG 实战：本地知识库问答》 | ✅ 已发布 |
| 13 | 10-multimodal | 《车载多模态：语音 + 视觉融合》 | ✅ 已发布 |
| 14 | 11-agent | 《Agent 框架：Function Calling 实战》 | ✅ 已发布 |
| 15 | 00-overview | 《AAOS 与手机 Android 的 5 个本质区别》 | 🚧 编写中 |

## 🚀 快速开始

```bash
# 克隆仓库
git clone https://github.com/jason5200/AAOS-Guide.git
cd AAOS-Guide

# 建议阅读顺序：README → 00-overview → 01-car-service → ...
```

> 💡 配套 Demo 仓库：`Car-Launcher-Demo`（车机 Launcher 实战）、`AI-Android-Demo`（AI 落地示例）

## 🤝 参与共建

欢迎 Issue 提需求、PR 补内容！贡献流程：

1. Fork 本仓库
2. 新建分支 `feature/你的内容`
3. 提交 PR，说明改动点

## 📄 License

[Apache-2.0](LICENSE) © [jason5200](https://github.com/jason5200)
