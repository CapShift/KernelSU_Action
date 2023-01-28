**中文** | [English](README_EN.md)

# KernelSU Action

用于 Non-GKI Kernel 的 Action，具有一定的普遍性，需要了解内核及 Android 的相关知识得以运用。


## 支持内核

- `4.19`
- `4.14`


## 使用

	Fork 本仓库到你的储存库然后点击`Action`，在左侧可看见`Build Kernel`选项，点击选项会看见右边的大对话框的上面会有`Run workflows`，里面有需要你填写的配置，看下面的部分，了解如何填写。

	或者使用 config.env(设置 USE_CONFIG 为 true)，按照以下内容编辑 config.env 然后提交，按 Star 或者 Run workflows，这个功能是方便手机修改参数。

### Build Kernel

	编译成功后，会在`Action`上传 AnyKernel3，已经关闭设备检查，请在 Twrp 刷入

#### Kernel Source

	填写你的内核仓库地址, 例如: [https://github.com/raystef66/InfiniR_kernel_alioth.git](https://github.com/raystef66/InfiniR_kernel_alioth)

#### Kernel Source Branch

	填写你的内核分支, 例如: 13.0-alioth

#### Kernel defconfig

	填写你的内核配置文件名, 例如: vendor/alioth_defconfig

#### Kernel file

	填写编译生成的Image，一般为你指定的内核配置[vendor/alioth_defconfig]中的CONFIG_BUILD_ARM64_APPENDED_KERNEL_IMAGE_NAME参数值, 例如: Image.gz-dtb

#### Clang version

	填写需要使用的 Clang 版本
	| Clang 版本 | 对应 Android 版本 | AOSP-Clang 版本 |
	| ---------- | ----------------- | --------------- |
	| 12.0.5 | Android S | r416183b |
	| 14.0.6 | Android T | r450784d |
	| 14.0.7 | | r450784e |
	| 15.0.1 | | r458507 |


#### Extra build commands

	有的内核需要手动加入一些编译命令，才能正常编译，不需要的话不填写即可，请在命令与命令之间用空格隔开
	例如: LLVM=1 LLVM_IAS=1

#### Disable LTO

	用于优化内核，但有些时候会导致错误，所以提供禁用它，设置为 true 即禁用

#### Use KernelSU

	是否使用 KernelSU，用于排查内核故障或单独编译内核

#### Use Kprobes

	如果你的内核 Kprobes 工作正常这项改成 true 即可自动在 defconfig 注入参数



## 感谢

- [AnyKernel3](https://github.com/osm0sis/AnyKernel3)
- [AOSP](https://android.googlesource.com)
- [KernelSU](https://github.com/tiann/KernelSU)
- [KernelSU_Action](https://github.com/xiaoleGun/KernelSU_Action)
