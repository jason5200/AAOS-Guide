<div align="center">

# AAOS-Guide

**车载 Android（Android Automotive OS）学习路线 —— 先把座舱系统讲清楚，AI 上车作为选读**

[![Stars](https://img.shields.io/github/stars/jason5200/AAOS-Guide?style=social)](https://github.com/jason5200/AAOS-Guide)
[![License](https://img.shields.io/github/license/jason5200/AAOS-Guide)](https://github.com/jason5200/AAOS-Guide)
[![AOSP](https://img.shields.io/badge/AOSP-android--14.0.0__r67-green)](AOSP_VERSION.md)

</div>

---

## 为什么有这个仓库

网上车载 Android 资料要么是官方文档太抽象，要么是碎片博客。本仓库目标是一条**从手机 Android 过渡到 AAOS** 的主线：CarService、Vehicle HAL、多屏、性能、权限与座舱约束。

大模型相关内容放在文末「选读」，不占用主路线。源码默认对照 [AOSP android-14.0.0_r67](AOSP_VERSION.md)，行号随分支会变。

## 怎么读

```
手机 Android 基础
      │
      ▼
00 全景：AAOS 是什么、和 Android Auto 的区别
      │
      ├── 01 CarService 与车辆服务
      ├── 02 CarPropertyManager（现行车辆属性 API）
      ├── 03 多屏 / Cluster / HUD
      ├── 04 启动与性能
      ├── 06–08 音频、OTA、权限与驾驶分心
      └── 12–24 Vehicle HAL、蓝牙、导航、安全与测试
```

建议顺序：`00-overview` → `01-car-service` → `02-carservice-api` → `12-vehicle-hal`。有具体问题再跳章节。

配套代码：

- [Car-Launcher-Demo](https://github.com/jason5200/Car-Launcher-Demo) —— 车机 Home 骨架（应用网格 + 时钟），需 AAOS 模拟器
- [AI-Android-Demo](https://github.com/jason5200/AI-Android-Demo) —— 对话 UI + OpenAI 兼容 API（无 Key 时走 Mock）

## 目录结构

```
AAOS-Guide/
├── README.md
├── AOSP_VERSION.md           # 源码对照分支
├── 00-overview/              # AAOS 全景
├── 01-car-service/           # CarService 与子服务
├── 02-carservice-api/        # CarPropertyManager
├── 03-multi-display/         # 多屏
├── 04-perf/                  # 冷启动
├── 05-ai-integration/        # AI 上车（选读）
├── 06-audio/ … 08-permission/
├── 09-rag/ … 11-agent/       # RAG / 多模态 / Agent（选读）
├── 12-vehicle-hal/ … 24-testing/
└── 25-transformer/ … 47-llm-safety/  # 模型基础（选读）
```

## 主线文章（车载系统，28 篇）

| 序号 | 路径 | 文章 |
|------|------|------|
| 00 | 00-overview | [车载 Android 全景：AAOS 到底是什么](00-overview/aaos-intro.md) |
| 01 | 01-car-service | [CarService 架构：从 SystemServer 到车辆服务](01-car-service/carservice-architecture.md) |
| 02 | 01-car-service | [CarService 启动流程源码](01-car-service/carservice-startup-source.md) |
| 03 | 02-carservice-api | [CarPropertyManager：如何读写车辆属性](02-carservice-api/carproperty-manager.md) |
| 04 | 01-car-service | [CarPropertyService 属性读写源码](01-car-service/carproperty-source.md) |
| 05 | 01-car-service | [CarPowerManagementService：电源状态管理](01-car-service/car-power.md) |
| 06 | 01-car-service | [CarHvacService：空调控制](01-car-service/car-hvac.md) |
| 07 | 01-car-service | [车辆传感器数据（API 已迁移说明）](01-car-service/car-sensor.md) |
| 08 | 01-car-service | [CarInfoService：车辆静态信息](01-car-service/car-info.md) |
| 09 | 01-car-service | [CarUxRestrictionsService：驾驶分心](01-car-service/car-ux.md) |
| 10 | 08-permission | [CarService 权限模型](08-permission/car-permission.md) |
| 11 | 12-vehicle-hal | [Vehicle HAL：从 AIDL 到实现](12-vehicle-hal/vehicle-hal.md) |
| 12 | 03-multi-display | [车机多屏：从 Display 到 Surface](03-multi-display/multi-display.md) |
| 13 | 17-cluster | [Cluster 仪表盘显示](17-cluster/cluster.md) |
| 14 | 18-hud | [HUD 抬头显示](18-hud/hud.md) |
| 15 | 16-camera | [倒车影像与环视](16-camera/reverse-camera.md) |
| 16 | 06-audio | [CarAudioService：车载音频](06-audio/car-audio-service.md) |
| 17 | 15-multimedia | [多媒体：音频焦点与分区](15-multimedia/multimedia.md) |
| 18 | 13-bluetooth | [车载蓝牙电话：HFP](13-bluetooth/bluetooth-hfp.md) |
| 19 | 14-navigation | [车载导航](14-navigation/navigation.md) |
| 20 | 07-ota | [车载 OTA：差分包与 A/B 分区](07-ota/ota-upgrade.md) |
| 21 | 22-boot | [从开机到座舱可用](22-boot/boot-process.md) |
| 22 | 04-perf | [车机冷启动优化](04-perf/cold-start.md) |
| 23 | 23-memory | [低内存设备优化](23-memory/memory-optimization.md) |
| 24 | 19-v2x | [V2X 车联网（概述）](19-v2x/v2x.md) |
| 25 | 20-safety | [功能安全与 ISO 26262（概述）](20-safety/functional-safety.md) |
| 26 | 21-security | [CAN 总线安全（概述）](21-security/can-security.md) |
| 27 | 24-testing | [模拟器与 HIL 测试](24-testing/testing.md) |

带「概述」的几篇是背景扫盲，不是实车/HIL 实测报告。

## 选读：AI 上车（41 篇）

先读 `05-ai-integration/` 四篇建立「为什么要端侧」的直觉，其余（Transformer、量化、RAG、Agent 框架）按需查阅。完整列表见各目录，博客导读：[AI 上车系列](https://jason5200.github.io/#/series/ai)。

入口：

| 路径 | 建议先读 |
|------|----------|
| 05-ai-integration | [端侧推理可行方案](05-ai-integration/on-device-llm.md) · [车载语音](05-ai-integration/voice-assistant.md) · [座舱 Agent](05-ai-integration/agent-cockpit.md) · [工程化](05-ai-integration/ai-engineering.md) |
| 09-rag | [车载 RAG](09-rag/car-rag.md) |
| 11-agent | [Function Calling](11-agent/agent-framework.md) |

## 参与共建

欢迎 Issue 纠错（尤其是 AOSP 版本与 API 废弃信息）。贡献流程见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

[Apache-2.0](LICENSE) © [jason5200](https://github.com/jason5200)
