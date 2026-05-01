OPlus MT6853 通用内核项目
这是一个针对 OPPO / Realme (OPlus) 平台，基于联发科 MT6853 (天玑 720/800U) 芯片组定制的 Linux 内核。本项目在原生代码基础上进行了大量的上游同步与特性移植，旨在提升系统性能与安全性。

📱 支持设备
理论上支持所有搭载 MT6853 芯片组的 OPlus 系列设备，包括但不限于：

OPPO A72 5G / A92s

Realme V5 / V15

OPPO Reno4 SE

其他同平台的 OPlus 设备

✨ 主要特性
⬆️ 内核版本升级 (LTS Update)
版本更新：从传统的 4.14.186 深度同步至 4.14.336+ (持续跟进长期支持分支)。

稳定性提升：修复了上百个上游安全漏洞（CVE）并优化了内存管理。

🛡️ 核心功能添加
ReSukiSU：集成了最新的内置 Root 解决方案，提供更隐蔽、更强大的权限管理能力。

BPF 特性 Backport：

深度回写（Backport）了高版本内核的 eBPF 特性。

支持 Android 12+ 的网络监管与流量统计需求。

修复了 BPF 校验器（Verifier）的内存偏移与 get_cred_rcu 适配问题，确保系统不因 BPF 加载而崩溃。

📂 文件系统增强
Xiaomi sdFAT：从小米内核源码树移植了高性能的 sdfat 驱动。

完美支持大容量 SD 卡（exFAT 格式）。

相比原生驱动，拥有更快的读写速度和更佳的稳定性。

🚀 优化与修复
ArrayMap Fix：修复了 BPF 中 array_map_update_elem 的冗余检查，提升 Map 更新效率。

编译器优化：支持使用最新的 Clang/LLVM 进行编译，提升二进制执行效率。

🛠️ 编译说明
环境准备
建议使用 Ubuntu 20.04+ 或 Arch Linux 环境。

编译步骤
克隆源码：

Bash
git clone https://github.com/momo54181/android_kernel_oplus_mt6853.git
cd android_kernel_oplus_mt6853
设置工具链： https://github.com/crdroidandroid/android_prebuilts_clang_host_linux-x86_clang-6443078
确保你的环境变量中包含 AOSP Clang 或 GCC。

开始编译：

Bash
make O=out <mo-mt6853_defconfig>
make O=out -j$(nproc)
📦 刷入方法
编译完成后，将生成的 Image.gz-dtb 或 dtb 放入 AnyKernel3 模板中。

使用 zip 命令打包。

进入手机 Recovery 模式（如 TWRP），直接刷入生成的 .zip 文件。

🤝 致谢
Linux Kernel Stable

Google Android Common Kernel

Xiaomi (for sdfat driver)

OPlus (for base sources)

AnyKernel3 (for the flashable template)