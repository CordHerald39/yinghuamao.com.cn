---
title: "代理端口不是控制端口：避免把管理接口当接入地址"
category: "tutorials"
label: "实用教学"
description: "代理端口不是控制端口：避免把管理接口当接入地址，按步骤核对条件、错误与恢复方法。"
date: "2026-10-04"
updated: "2026-10-04"
author: "樱花猫中文资料编辑"
draft: false
---

## 两种端口用途不同
代理监听接收应用请求，外部控制器 API 用于管理内核。把应用代理设置填成控制器端口，通常无法实现代理访问；把管理 API 暴露出去也不是提高速度的方法。
## 看配置字段确认
Mihomo 的 external-controller 与 port、socks-port、mixed-port 分开配置。先记录本机实际字段和监听地址，示例数字不可替代当前配置。控制面板能打开只证明管理入口可达，不等于节点已连接。
## 检查管理边界
只需本机管理时采用回环监听，并按文档设置管理访问密钥。文档特别指出 Unix socket、Windows named pipe 与部分接口有各自的验证边界，不能认为设置一个 secret 就保护了所有可能入口。不要把密钥写进截图或文章。
## 排查顺序
先用正确代理端口作一个普通请求，再独立检查管理界面。遇到配置不一致先恢复原设置，不通过绑定所有网卡来尝试“修好”。本教程不提供樱花猫的专用 API 或官方后台入口。
## 资料
[Mihomo 控制接口配置](https://wiki.metacubex.one/config/general/)；[代理端口](https://wiki.metacubex.one/config/inbound/port/)。另见[局域网共享范围](/tutorials/lan-sharing-boundary/)。
