# 源码对照版本

本仓库叙述默认对照：

| 项 | 值 |
|----|----|
| AOSP 标签 | `android-14.0.0_r67` |
| 对应 | Android 14 / AAOS 14 参考基线 |
| 代码浏览 | https://cs.android.com/android/platform/superproject/+/android-14.0.0_r67: |

中间件相关路径（均相对 AOSP 根目录）：

| 模块 | 路径 |
|------|------|
| CarService | `packages/services/Car/service/` |
| car-lib（App API） | `packages/services/Car/car-lib/` |
| Helper（SystemServer 侧） | `packages/services/Car/car-builtin-services/` |
| Vehicle HAL AIDL | `hardware/interfaces/automotive/vehicle/` |
| 参考 VHAL 实现 | `hardware/interfaces/automotive/vehicle/aidl/impl/` |
| 属性 ID | `hardware/interfaces/automotive/vehicle/aidl/android/hardware/automotive/vehicle/VehicleProperty.aidl` 以及 `android.car.VehiclePropertyIds` |

说明：

- 行号、类名会随分支变化。文中代码是按该标签**结构改写**，不是逐行拷贝，请到 cs.android.com 核对。
- Android 13 起 Vehicle HAL 以 **AIDL** 为主；更早分支常见 HIDL `IVehicle@2.0` 的 `get/set/subscribe`。
- `CarSensorManager`、`CarHvacManager`、`CarInfoManager` 已废弃，信号请走 `CarPropertyManager`。
- 车速属性是 `VehiclePropertyIds.PERF_VEHICLE_SPEED`（m/s）。HVAC 分区 `areaId` 来自 config 的 `VehicleAreaSeat` 位，不要写死 0/1/2。
- 调试：`adb shell dumpsys car_service`；AIDL VHAL：`dumpsys android.hardware.automotive.vehicle.IVehicle/default`。inject 子命令以当前 `cmd car_service` 为准。
