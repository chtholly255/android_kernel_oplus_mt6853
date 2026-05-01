# OPlus MT6853 Universal Kernel Project

![Kernel Version](https://img.shields.io/badge/Kernel-4.14.336%2B-blue.svg)
![Target-Android](https://img.shields.io/badge/Android-12%20%7C%2013-green.svg)
![Platform](https://img.shields.io/badge/Platform-MT6853-orange.svg)

针对 OPPO/Realme MT6853 (Dimensity 720/800U) 平台的通用高性能内核。本项目通过深度回写（Backport）现代内核特性，完美适配 Android 12 及更高版本的系统需求。

## 📱 支持设备清单
本内核采用通用配置，支持以下基于 OPlus 底层的 MT6853 机型：
- **OPPO 系列**: A72 5G, A53 5G, K7x, A95 5G, Reno4 SE
- **Realme 系列**: Q2, Q2 Pro, Q2i, V5 5G, V15 5G, X7 5G

## 🚀 核心改进

### ⚙️ 内核基础
- **LTS 更新**: 同步至 Linux 官方稳定版 **4.14.336+**。
- **工具链**: 使用 AOSP Clang 10.0.4 (r383902) 进行优化编译。

### 🔗 eBPF & 网络适配 (Android 12+)
- **BPF Backport**: 完整移植了高版本内核的 eBPF 支撑框架，解决 Android 12 上的网络统计、流量限制（Tethering）和防火墙兼容性问题。
- **稳定性修复**:
    - 修复了 `bpf_verifier_vlog` 的内存溢出与偏移问题。
    - 适配了 `get_cred_rcu` 的原子操作类型（atomic_long），避免权限校验时的内核 Panic。
    - 修复了 `arraymap` 更新逻辑中的冗余检查。

### 🛠️ 附加驱动与功能
- **ReSukiSU**: 内置 Root 权限支持。
- **Xiaomi sdFAT**: 引入小米高性能 sdFAT 驱动，大幅优化大容量 SD 卡的挂载速度与 exFAT 性能。
- **性能调优**: 优化了 MTK 平台的调度响应，降低 Android 12 系统下的后台耗电。

## 🛠️ 编译说明
**源码克隆**:
```bash
git clone [https://github.com/momo54181/android_kernel_oplus_mt6853.git](https://github.com/momo54181/android_kernel_oplus_mt6853.git)