# 🛠️ KonaryBuildProject
"为什么是Building,编译只有进行时！！！"
"Why "Building"? Compilation is a continuous process！！！"
> 面向 **OPPO Pad (OPD2101 / SM8250-ac)** 的一体化 Android 编译工程  
> 基于开源源码深度重构，支持 **Kernel / TWRP** 云端一键构建，打造稳定、可控、可持续维护的底层生态。

[![Kernel Build](https://img.shields.io/github/actions/workflow/status/Shirayukilu/KonaryBuildProject/kernel.yml?label=Kernel&logo=github&style=flat-square)
[![TWRP Build](https://img.shields.io/github/actions/workflow/status/Shirayukilu/KonaryBuildProject/twrp.yml?label=TWRP&logo=github&style=flat-square)
[![License](https://img.shields.io/badge/license-GPL--3.0-blue.svg?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-SM8250-lightgrey.svg?style=flat-square)](https://www.qualcomm.com/smartphones/products/8-series/snapdragon-870-5g-mobile-platform)
[![Device](https://img.shields.io/badge/device-OPPO%20Pad%20(OPD2101)-green.svg?style=flat-square)](https://www.oppo.com/cn/accessories/oppo-pad/)

---

## 📖 项目简介

`KonaryBuildProject` 是一个**工程化 Android 底层编译项目**，面向 OPPO Pad (OPD2101, Snapdragon SM8250)，覆盖：

- ✅ **Linux Kernel（msm-4.19）**
- ✅ **TWRP Recovery（TeamWin Recovery Project）**
- ✅ **GitHub Actions 云端全自动化构建**
- ✅ **KernelSU / SusFS 可选集成**
- ✅ **AnyKernel3 / Recovery-flashable ZIP 双产物**

项目目标不是“能跑”，而是：

> **可复现、可维护、可演进的长期内核 & Recovery 构建体系**

---

## ✨ 当前能力矩阵

| 模块 | 状态 | 说明 |
|----|----|----|
| Linux Kernel | ✅ 稳定 | msm-4.19，GCC / Clang 双工具链 |
| TWRP Recovery | ✅ 支持 | omni-12.1 / twrp-12.1 基线 |
| KernelSU | ✅ 可选 | 内核级 Root，GKI / Non-GKI 适配 |
| SusFS | ✅ 可选 | Root 隐藏，抗检测 |
| GitHub Actions | ✅ 完善 | 多工作流、并行构建 |
| 设备树 | ✅ 完整 | OPD2101 / SM8250 全驱动适配 |

---

## 📁 项目结构（标准化）

---

## ⚙️ GitHub Actions 参数说明

### Kernel 构建参数

| 参数 | 说明 |
|----|----|
| `KERNEL_REPO` | 内核源码仓库 |
| `KERNEL_BRANCH` | 内核分支 |
| `DEVICE_TREE_REPO` | 设备树仓库 |
| `DEFCONFIG` | 内核配置文件 |
| `ENABLE_KSU` | 是否启用 KernelSU |
| `ENABLE_SUSFS` | 是否启用 SusFS |
| `VERSION_TAG` | 自定义版本后缀 |

### TWRP 构建参数

| 参数 | 说明 |
|----|----|
| `TWRP_REPO` | TWRP 源码仓库 |
| `TWRP_BRANCH` | TWRP 分支 |
| `DEVICE` | 设备代号（opd2101） |
| `RECOVERY_VARIANT` | recovery / bootimage |

---

## 📦 构建产物

| 类型 | 路径 | 用途 |
|----|----|----|
| Kernel | `out/arch/arm64/boot/Image.gz-dtb` | 刷机 / AnyKernel3 |
| TWRP | `out/target/product/opd2101/recovery.img` | Recovery 刷入 |
| ZIP | `kernel-anykernel3-*.zip` | 一键刷机包 |

---

## 🧠 技术说明（重要）

### 工具链策略
- **Kernel**：优先 Clang 20，GCC 4.9 作为兼容兜底
- **TWRP**：严格使用 Android 官方预编译工具链
- **禁止混用宿主 gcc / clang**

### 闭源驱动处理
- 驱动仓库独立管理
- 编译期注入 `vendor/`
- 不提交二进制至主仓库

### Git 规范
- 源码与工具链分离
- 工具链通过 Release / Submodule 管理
- `.gitignore` 屏蔽所有构建产物

---

## 🛠️ 常见问题

### Q1：TWRP 编译失败，提示 soong 错误？
> 确认使用的是 **Android 12.1+ 源码 + JDK 11**，并确保 `repo sync` 完整。

### Q2：Kernel 编译时报 GCC 无法执行？
> 本项目 GCC 为 Python wrapper，需通过 `aarch64-linux-android-gcc.real` 调用，详见 `build_env.sh`。

### Q3：刷入后无法开机？
> 确认：
> - Kernel / TWRP 版本匹配
> - Bootloader 未锁
> - 已备份原厂镜像

---

## 📜 开源协议

本项目基于 **GPL-3.0** 发布，遵循 Linux Kernel 及 Android Open Source Project 相关规定。  
所有修改均保留原始版权声明，衍生作品须以相同协议开源。

---

## 🙏 致谢

- Qualcomm / OPPO 官方源码
- LineageOS / OmniROM / TWRP 团队
- KernelSU / SusFS 社区
- Android LLVM Toolchain 团队

---

> 💡 **KonaryBuildProject 不是一个“脚本集合”，而是一个长期维护的 Android 底层工程。**  
> 欢迎 Issue / PR / 讨论，共建 OPPO Pad 的开放生态。

⭐ 如果本项目对你有帮助，请点亮一颗 Star。

