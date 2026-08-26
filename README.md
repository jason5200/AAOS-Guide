<div align="center">

# AAOS-Guide

**车载 Android 中间件学习路线 —— Vehicle HAL · CarService · 车辆属性**

[![Stars](https://img.shields.io/github/stars/jason5200/AAOS-Guide?style=social)](https://github.com/jason5200/AAOS-Guide)
[![License](https://img.shields.io/github/license/jason5200/AAOS-Guide)](https://github.com/jason5200/AAOS-Guide)
[![AOSP](https://img.shields.io/badge/AOSP-android--14.0.0__r67-green)](AOSP_VERSION.md)

</div>

---

## 这个仓库讲什么

座舱里真正反复打交道的，不是应用皮肤，而是中间件：

**应用 → `android.car` → `com.android.car`（CarService）→ Vehicle HAL → 总线 / ECU**

本仓库按这条链路写：进程怎么起来、属性怎么读写、电源 / 音频 / 驾驶分心怎么卡住层。源码默认对照 [AOSP android-14.0.0_r67](AOSP_VERSION.md)。

多屏、OTA、导航等是座舱能力，放在主线后半；大模型相关是附录，不占中间件路径。

## 中间件怎么读

```
Binder / 系统服务基础
        │
        ▼
00  全景：AAOS ≠ Android Auto
        │
        ▼
    中间件地图（推荐先读）
        │
        ├── Vehicle HAL     硬件契约（AIDL IVehicle）
        ├── CarService      独立进程 com.android.car
        ├── Property        CarPropertyManager / CarPropertyService
        ├── Power           上电 / 熄火准备 / 挂起
        ├── Audio           Zone + 焦点 + 音量组
        └── Permission/UX   签名权限 + 驾驶分心
```

建议顺序：

1. [全景](00-overview/aaos-intro.md) → [中间件地图](00-overview/middleware.md)
2. [CarService 架构](01-car-service/carservice-architecture.md) → [启动流程](01-car-service/carservice-startup-source.md)
3. [CarPropertyManager](02-carservice-api/carproperty-manager.md) → [CarPropertyService](01-car-service/carproperty-source.md)
4. [Vehicle HAL](12-vehicle-hal/vehicle-hal.md)
5. [权限与分心](08-permission/car-permission.md) → [电源](01-car-service/car-power.md) → [音频](06-audio/car-audio-service.md)

配套：[Car-Launcher-Demo](https://github.com/jason5200/Car-Launcher-Demo)（Home 骨架，需 AAOS 模拟器）。

## 目录

```
AAOS-Guide/
├── 00-overview/          # 全景 + 中间件地图
├── 01-car-service/       # CarService / Property / Power / HVAC / UX
├── 02-carservice-api/    # CarPropertyManager
├── 06-audio/             # CarAudioService
├── 08-permission/        # 权限与驾驶分心
├── 12-vehicle-hal/       # IVehicle AIDL
├── 03 / 07 / 13–24       # 多屏、OTA、蓝牙等座舱能力
└── 05 / 09 / 25–47       # AI 附录（不挡中间件主线）
```

## 中间件核心文章

| | 文章 | 你读完应能回答 |
|--|------|----------------|
| 地图 | [车载中间件地图](00-overview/middleware.md) | 一层层谁和谁说话 |
| 架构 | [CarService 架构](01-car-service/carservice-architecture.md) | 为什么是独立进程 |
| 启动 | [CarService 启动流程](01-car-service/carservice-startup-source.md) | Helper 怎么 bind 起来 |
| API | [CarPropertyManager](02-carservice-api/carproperty-manager.md) | 怎么读/写/订阅属性 |
| 服务 | [CarPropertyService](01-car-service/carproperty-source.md) | 权限、缓存、下 HAL |
| HAL | [Vehicle HAL](12-vehicle-hal/vehicle-hal.md) | AIDL 契约和 vendor 实现 |
| 权限 | [权限与驾驶分心](08-permission/car-permission.md) | 谁能控车、行驶中 UI 怎么收 |
| 电源 | [CarPowerManagementService](01-car-service/car-power.md) | 熄火前 App 做什么 |
| 音频 | [CarAudioService](06-audio/car-audio-service.md) | Zone、焦点、音量组 |

其余车载文章（多屏、Cluster、OTA 等）见下表；标「概述」的不是实车/HIL 报告。

<details>
<summary>全部车载文章（含座舱能力）</summary>

| 序号 | 文章 |
|------|------|
| 00 | [AAOS 全景](00-overview/aaos-intro.md) |
| — | [中间件地图](00-overview/middleware.md) |
| 01 | [CarService 架构](01-car-service/carservice-architecture.md) |
| 02 | [CarService 启动流程](01-car-service/carservice-startup-source.md) |
| 03 | [CarPropertyManager](02-carservice-api/carproperty-manager.md) |
| 04 | [CarPropertyService](01-car-service/carproperty-source.md) |
| 05 | [电源](01-car-service/car-power.md) |
| 06 | [空调（走 Property）](01-car-service/car-hvac.md) |
| 07 | [传感器 API 已迁移](01-car-service/car-sensor.md) |
| 08 | [车辆信息（走 Property）](01-car-service/car-info.md) |
| 09 | [UX Restrictions](01-car-service/car-ux.md) |
| 10 | [权限模型](08-permission/car-permission.md) |
| 11 | [Vehicle HAL](12-vehicle-hal/vehicle-hal.md) |
| 12 | [多屏](03-multi-display/multi-display.md) |
| 13 | [Cluster](17-cluster/cluster.md) |
| 14 | [HUD](18-hud/hud.md) |
| 15 | [倒车影像](16-camera/reverse-camera.md) |
| 16 | [CarAudioService](06-audio/car-audio-service.md) |
| 17 | [多媒体焦点](15-multimedia/multimedia.md) |
| 18 | [蓝牙 HFP](13-bluetooth/bluetooth-hfp.md) |
| 19 | [导航](14-navigation/navigation.md) |
| 20 | [OTA](07-ota/ota-upgrade.md) |
| 21 | [启动到座舱可用](22-boot/boot-process.md) |
| 22 | [冷启动](04-perf/cold-start.md) |
| 23 | [内存](23-memory/memory-optimization.md) |
| 24 | [V2X（概述）](19-v2x/v2x.md) |
| 25 | [功能安全（概述）](20-safety/functional-safety.md) |
| 26 | [CAN 安全（概述）](21-security/can-security.md) |
| 27 | [测试](24-testing/testing.md) |

</details>

## 附录：AI 上车

不挡中间件主线。入口：`05-ai-integration/`。

## 参与共建

欢迎核对 AOSP 标签、废弃 API 和权限级别。见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

[Apache-2.0](LICENSE) © [jason5200](https://github.com/jason5200)
