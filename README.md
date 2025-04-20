# AI-Minecraft-Server

这是一个基于阿里云 ECS 搭建的 Minecraft Fabric 服务端项目，同时配套整理了部署过程中的关键配置脚本、排错记录以及 AI 协作总结，旨在为未来复现、迁移或他人学习提供便利。
---

## 🔗 教程参考资源
本项目最初搭建流程主要参考了以下视频教程：

- [【B站】阿里云ECS搭建我的世界Java版服务器（含fabric模组）](https://www.bilibili.com/video/BV1PE411c7t9)

在此基础上，根据自身服务器环境（CentOS）以及 Java 版本兼容问题，对部分步骤进行了修改，并在 AI 协助下记录了常见问题与排错过程。

---

## 🌐 项目结构说明

```bash
AI-Minecraft-Server/
├── README.md                          # 项目说明文档（当前文件）
├── scripts/                           # 服务器配置与辅助脚本
│   ├── start.sh                       # 启动 Minecraft 服务端脚本
│   ├── bash_profile_java.sh           # JAVA_HOME 设置脚本
│   └── screen_usage.md                # screen 指令速查
├── prompt_notes/                      # AI 辅助排错与协作过程记录
│   ├── 01_安装Java环境失败问题解决记录.md
│   ├── 02_screen会话管理问题排查.md
│   └── 03_GPT协作总结与反思.md
├── server/                            # Minecraft 服务端文件
│   └── world_backup.zip               # 存档备份文件
├── images/                            # 项目相关截图
│   └── server_running.png             # Minecraft 控制台运行截图（可选）
```

---

## 🛠️ 部署说明（简略版）

> 详细操作请参考 `scripts/` 与 `prompt_notes/` 中的说明文档。

### 1. 安装 Java 环境

确保使用 Java 21，并正确配置 `JAVA_HOME` 到 `.bash_profile` 中，执行 `source ~/.bash_profile` 生效。

```bash
export JAVA_HOME=/usr/local/java/jdk-21.0.3/
export PATH=$JAVA_HOME/bin:$PATH
```

### 2. 使用 screen 管理服务端运行

避免 XShell 断连中断服务，使用 `screen` 管理运行会话。

```bash
screen -S server
sh ./scripts/start.sh
```

断开后重新连接：
```bash
screen -r [会话名或编号]
```

更多参考 `screen_usage.md`

### 3. 启动 Minecraft 服务端

请使用启动脚本（可修改内存参数）：

```bash
sh ./scripts/start.sh
```

---

## 📄 附录与说明

- 服务端基于 Fabric 构建，Jar 文件为 `fabric-server-launcher.jar`
- 存档位于 `server/world_backup.zip`，解压后作为 `world/` 目录使用
- 文档中部分内容由 AI（ChatGPT）协助生成与总结

---

## ✨ 后续计划

- 添加 `mods/` 与 `config/` 配置共享支持
- 制作自动部署脚本（One-click setup）
- 增加 Dockerfile 支持版本

如有更多建议，欢迎提出 Issue 或 Pull Request。

如果你准备将这个项目用于**prompt工程岗位申请**或是**大模型安全相关展示**，并且强调人机协作、可验证性、可追溯性，那么提及该教程是**非常有价值**的。原因如下：

---
感谢 AI 伙伴的协助，也感谢曾经被 screen 卡住的我自己

