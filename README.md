<!--
Copyright (c) 2026 江上晚 (jiangshangwan) <liyd9745@gmail.com>
SPDX-License-Identifier: GPL-3.0-only
qm-lspidx-6D40 · LSPosed 模块仓库展示页
-->

<div align="center">

# QQ音乐简洁版适配

**修复 QQ音乐简洁版在 HyperOS 播放时通知栏与锁屏无播放器控件，恢复系统样式富媒体播放卡片。**

<a href="https://www.android.com/"><img src="https://img.shields.io/badge/Android-7.0--15-brightgreen?style=flat&logo=android&logoColor=white"></a>
<a href="https://hyperos.mi.com/"><img src="https://img.shields.io/badge/HyperOS-OS3--OS4-purple?style=flat&logo=xiaomi&logoColor=white"></a>
<a href="https://github.com/LSPosed/LSPosed"><img src="https://img.shields.io/badge/LSPosed-API%20102-blue?style=flat&logo=xdadevelopers&logoColor=white"></a>
<a href="https://github.com/jiangshangwan/qqmusiclitefix"><img src="https://img.shields.io/badge/GitHub-black?style=flat&logo=github&logoColor=white"></a>
<a href="https://www.coolapk.com/u/3019478"><img src="https://img.shields.io/badge/酷安-江上晚-green?style=flat&logo=fishshell&logoColor=white"></a>

</div>

---

## 问题背景

QQ音乐简洁版播放音乐时，通知栏与锁屏不显示播放器控件。原因是应用在构建播放通知时使用了 `MediaStyle`，却没有把已创建的 `MediaSession` token 绑定到通知上——系统因此不把它识别为媒体会话载体，HyperOS 的媒体中心与锁屏富媒体卡片不会渲染。

## 核心功能

- ✅ **恢复 HyperOS 系统样式富媒体播放卡片**：通知栏与锁屏正常显示大封面、进度条与系统媒体中心样式控件
- ✅ **播放按钮居中**：上一曲 / 播放暂停 / 下一曲落在卡片中部，与系统播放器视觉一致
- ✅ **系统矢量图标**：播放控制按钮使用 framework 矢量资源，避免位图放大模糊
- ✅ **通知渠道修正**：强制播放渠道为锁屏可见，避免历史设置导致通知被关闭
- ✅ **主题启动跟随系统**：应用启动或重新打开时按系统当前深色 / 浅色模式加载主题

## 安装说明

### 环境要求

- 已 Root 的小米 / 红米设备，HyperOS 3 ~ HyperOS 4
- LSPosed 框架需支持 libxposed Modern API 102（如 LSPosed 2.2.1 / 7949、Vector v2.2+）；本模块不兼容旧版 `de.robv.android.xposed` API
- 目标应用：QQ音乐简洁版 `com.tencent.freemusic`

### 使用步骤

1. 在 LSPosed 中启用本模块，勾选作用域「QQ音乐简洁版」
2. 强制停止并重新打开 QQ音乐简洁版
3. 模块无界面，不需要启动任何 Activity；若卡片未刷新，可重启 SystemUI 或设备

## 已知限制

- 播放器内实时切换系统深色 / 浅色模式不会立即生效，需结束应用后重新打开（目标应用主题在 Flutter 引擎初始化时读取，不响应系统亮度变化）
- 播放器「唱」按钮与点赞后的粉红心特效由 Flutter / Dart 层渲染，不在本模块处理范围

## 源码与反馈

- 源码仓库：[jiangshangwan/qqmusiclitefix](https://github.com/jiangshangwan/qqmusiclitefix)
- 问题反馈：请在源码仓库提交 Issue

<!-- qm-lspidx-end-6D40 -->
