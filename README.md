# OPlus MT6853 Universal Kernel

![Kernel Version](https://img.shields.io/badge/Kernel-4.14.336%2B-blue.svg)
![Platform](https://img.shields.io/badge/Platform-MT6853-orange.svg)
![Toolchain](https://img.shields.io/badge/Clang-6443078-red.svg)

针对 **OPPO / Realme (OPlus)** 平台开发的高性能通用内核，基于联发科 **MT6853 (天玑 720 / 800U)** 芯片组。

## 📱 支持设备
理论上支持所有搭载 MT6853 芯片组的 OPlus 设备：
- OPPO A72 5G / A92s / Reno4 SE
- Realme V5 / V15 / Q2i
- 其他同平台的 OPlus 设备

## ✨ 主要特性

### 1. 内核版本同步 (LTS)
- **版本更新**：从 `4.14.186` 深度同步至 **`4.14.336+`**。
- **安全性**：集成了上游安全补丁，提升系统稳定性。

### 2. eBPF 特性 Backport (Android 12+ 适配)
- **网络监管**：回写了现代 eBPF 特性，支持 Android 12/13 的流量统计与防火墙。
- **关键修复**：
    - 修复了 `bpf_verifier_vlog` 导致的内存偏移崩溃。
    - 修复了 `get_cred_rcu` 原子操作类型不匹配问题（适配 `atomic_long`）。
    - 优化 `arraymap.c`，移除冗余检查。

### 3. 功能增强
- **ReSukiSU**：集成内置 Root 解决方案。
- **Xiaomi sdFAT**：移植自小米内核的高性能 `sdfat` 驱动，提升 exFAT 格式 SD 卡的读写速度。

