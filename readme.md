# HAL_3_ButtonCount

## 简介

基于 STM32F103C8T6 与 STM32 HAL，本项目通过外部中断对按键计数，并在 OLED（SSD1306 驱动）上实时显示计数值。适合作为学习外部中断、GPIO 与软件 I2C 的示例工程。

## 主要特性

- 使用 STM32 HAL API，兼容 CubeMX 生成的初始化代码
- 软件 I2C 驱动 SSD1306 OLED（默认 PB8=SCL，PB9=SDA，可在代码中修改）
- 外部中断（按键）计数，主循环读取并刷新 OLED 显示
- 简单按键去抖与计数溢出保护

## 目录及关键文件

- CMakeLists.txt — 根构建脚本
- CMakePresets.json — 构建预设（Debug / Release）
- config.ioc — CubeMX 配置（外设、时钟、引脚配置）
- Core/Src/main.c — 程序入口与主循环
- Core/Src/OLED.c — OLED 驱动（软件 I2C）
- Core/Inc/OLED.h — OLED 接口声明
- Core/Inc/OLED_Font.h — 字库数据
- cmake/user_sources.cmake — 自定义源与 include 注册
- Drivers/ — STM32 HAL 与 CMSIS 文件

## 构建环境与依赖

- CMake 3.22 及以上
- Ninja 构建器
- ARM GCC 交叉编译器（如 `arm-none-eabi-gcc`）
- STM32 HAL 库（包含在 `Drivers/` 目录中）

## 构建步骤

推荐使用 VS Code 的 CMake 工具

## 运行与下载

1. 生成固件之后，使用 ST-Link 或其他支持的下载工具烧录生成的 ELF/HEX/BIN 文件到目标板。
2. 重新上电后，OLED 屏幕应显示主程序中指定的字符串。

## 硬件说明

- 目标 MCU：STM32F103 系列
- OLED 使用软件 I2C 模拟，默认引脚：
  - `PB8`：SCL
  - `PB9`：SDA
- 按钮：`PB1`

## 许可

MIT License
