# 🚀 MT6853 Kernel (OPPO / Realme) - Android 12

![Kernel Version](https://img.shields.io/badge/Kernel-4.14.x-blue.svg)
![Android Version](https://img.shields.io/badge/Android-12-green.svg)
![Platform](https://img.shields.io/badge/Platform-MediaTek%20MT6853-orange.svg)

这是一个针对 **OPPO / Realme (联发科 MT6853 / 天玑 720)** 机型量身定制的 Android 12 内核源码仓库。本项目集成了主流的内核级特权框架，并实现了基于 GitHub Actions 的全自动 CI/CD 编译构建。

## 📱 支持设备清单
本内核采用通用配置，支持以下基于 OPlus 底层的 MT6853 机型：
* **OPPO 系列**: A72 5G, A53 5G, K7x, A95 5G, Reno4 SE
* **Realme 系列**: Q2, Q2 Pro, Q2i, V5 5G, V15 5G, X7 5G , realme 7 5G, narzo 30 Pro 5G

---

## ✨ 功能特性 (Features)

- **高性能编译器组合**：完美适配 Google 官方 NDK r24 Clang 主编译器，搭配原生 GCC 4.9 交叉编译工具链，提供绝佳的指令集优化与稳定性。
- **特权框架内置**：原生集成 **[ReSukiSU](https://github.com/ReSukiSU/ReSukiSU)** 内核特权解决方案，无需手动注入即可享受顺畅体验。
- **全自动 CI 刷包制作**：每一次成功构建都会自动通过 [AnyKernel3](https://github.com/momo54181/AnyKernel3) 打包成可直接在第三方 Recovery (如 TWRP / OrangeFox) 中刷入的 `.zip` 卡刷包，并自动发布到 GitHub Release。

---

## 🛠️ 编译工具链 (Toolchains)

项目构建环境基于 `Ubuntu 22.04 LTS`，推荐的交叉编译器配置如下：

- **Clang (LLVM)**: Android NDK r24 Clang / AOSP Clang
- **GCC 64-bit**: aarch64-linux-android-4.9 (android-12.1.0_r27)
- **GCC 32-bit**: arm-linux-androideabi-4.9 (android-12.1.0_r27)
- **Defconfig**: `mo-mt6853_defconfig`

---

## 💻 本地编译指南 (Local Build Guide)

如果你希望在本地机器上手动编译此内核，可以参考以下命令：

```bash
# 1. 克隆源码并进入目录
git clone -b kernel-main https://github.com/momo54181/android_kernel_oplus_mt6853 android-kernel
cd android-kernel

# 2. 设置环境变量 (请将路径替换为你本地的编译器实际路径)
export PATH=/path/to/clang-aosp/bin:/path/to/gcc64/bin:/path/to/gcc32/bin:$PATH

# 3. 配置文件生成
make -s -j$(nproc --all) O=out ARCH=arm64 mo-mt6853_defconfig

# 4. 执行编译
make -j$(nproc --all) CC="clang" O=out ARCH=arm64 \
    CLANG_TRIPLE=aarch64-linux-gnu- \
    CROSS_COMPILE=aarch64-linux-android- \
    CROSS_COMPILE_ARM32=arm-linux-androideabi- \
    LD=ld.lld
