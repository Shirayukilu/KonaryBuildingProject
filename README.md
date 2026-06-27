# 🛠️ KonaryBuildProject
> 面向 **OPPO Pad (OPD2101 / SM8250-ac)** 的一体化 Android 编译工程  
> 基于开源源码深度重构，支持 **Kernel / TWRP** 云端一键构建，打造稳定、可控、可持续维护的底层生态。

[![Kernel Build](https://img.shields.io/github/actions/workflow/status/Shirayukilu/KonaryBuildProject/kernel.yml?branch=main&label=Kernel&style=flat-square)](https://github.com/Shirayukilu/KonaryBuildProject/actions)
[![TWRP Build](https://img.shields.io/github/actions/workflow/status/Shirayukilu/KonaryBuildProject/twrp.yml?branch=main&label=TWRP&style=flat-square)](https://github.com/Shirayukilu/KonaryBuildProject/actions)
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

