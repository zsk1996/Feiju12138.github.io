---
title: 【踩坑】Windows10 桌面右键卡死
categories:
  - Windows
date: 2020-02-23 16:38:09
---

## 前言

Windows10想刷新桌面，右键后鼠标一直转圈卡死

<!-- more -->

## 解决问题

### 打开注册表编辑器

- 打开运行，输入`regedit`，回车确定

### 删除igfxDTCM项

- 定位到`\HKEY_CLASSES_ROOT\Directory\Background\shellex\ContextMenuHandlers\igfxDTCM`

- 删除`igfxDTCM`项

## 完成

## 参考文献

[Microsoft社区——Yu-Shi](https://answers.microsoft.com/zh-hans/windows/forum/all/win10右键卡死/5f971c2d-442a-4813-ab5e-f33f8d006e1b)

