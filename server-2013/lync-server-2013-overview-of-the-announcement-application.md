﻿---
title: Lync Server 2013：通知应用程序概述
TOCTitle: 通知应用程序概述
ms:assetid: 2abee804-2599-48bb-90b2-15df0bae5e20
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/JJ204757(v=OCS.15)
ms:contentKeyID: 49312329
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的通知应用程序概述

 

_**上一次修改主题：** 2012-09-13_

部署 通知应用程序时，需要配置未分配号码表，以确定在某人拨打未分配号码时要采取的操作。未分配号码表包含对组织有效的电话号码范围，并指定处理每个范围的 通知应用程序。当呼叫者拨打对您的组织有效，但尚未将其分配给任何人的电话号码时， Lync Server 会在未分配号码路由表中查找该号码，确定该号码所属的范围，并将呼叫路由至为该范围指定的 通知应用程序。 通知应用程序会应答该呼叫并播放音频消息（如果配置了此功能），然后断开呼叫连接或将呼叫转接至预定目标，例如转接给接线员。您可以使用 Lync Server 命令行管理程序 cmdlet 来配置多个音频消息或转接目标。

配置未分配号码表的方式取决于要使用该表的方式。如果您有不再使用的特定号码并且要播放为每个号码定制的消息，则可以输入未分配号码表中的那些特定号码。例如，如果已更改客户服务台的号码，则可以输入旧的客户服务号码并将其与提供新号码的通知相关联。如果要向呼叫未分配号码的任何人（例如已离开组织的员工）播放常规消息，则可以输入组织所有可用分机的范围。每当呼叫者拨打当前未分配的号码时，系统都会调用未分配号码表。

在 Lync Server 2013 中， 通知应用程序自动与 响应组应用程序一起安装。通知应用程序和响应组应用程序是 企业语音部署的标准组件：在部署 企业语音时，系统会自动部署这两个应用程序。
