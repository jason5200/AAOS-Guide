# 源码对照版本

本仓库叙述默认对照：

| 项 | 值 |
|----|----|
| AOSP 标签 | `android-14.0.0_r67` |
| 对应 | Android 14 / 常见 AAOS 14 参考基线 |
| 代码浏览 | https://cs.android.com/android/platform/superproject/+/android-14.0.0_r67: |

说明：

- 行号、类名、隐藏 API 会随分支变化，引用时请以该标签为准再 diff 到你的项目分支。
- `CarSensorManager` 在较新的 AAOS 中已废弃，车辆信号请走 `CarPropertyManager` / `CarPropertyService`。见 [01-car-service/car-sensor.md](01-car-service/car-sensor.md)。
- 若你的座舱基于 Android 13/15，先对一下 `packages/services/Car` 再套用文中路径。
