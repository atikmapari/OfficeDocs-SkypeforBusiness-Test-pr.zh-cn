﻿---
title: 为即时消息 (IM) 配置文件传输和 URL 筛选
TOCTitle: 为即时消息 (IM) 配置文件传输和 URL 筛选
ms:assetid: 115a1a2c-599f-474c-a063-52f7144b5246
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg520952(v=OCS.15)
ms:contentKeyID: 49312037
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 为即时消息 (IM) 配置文件传输和 URL 筛选

 

_**上一次修改主题：** 2012-11-01_

智能 IM 筛选器工具有助于使 Lync Server 2013 部署遏制最常见病毒形式的传播，同时最大程度地减小对用户体验的影响。使用智能 IM 筛选器可以对筛选器进行配置，以阻止来自企业防火墙外部的未知终结点的未经请求或可能有害的即时消息。通过指定用于确定要阻止的内容（例如，包含带有特定前缀的超链接的即时消息和具有特定扩展名的文件）的条件来配置筛选器。

智能 IM 筛选器提供下列功能：

  - 增强的 URL 筛选功能。

  - 增强的文件传输筛选功能。

配置智能 IM 筛选器包括以下内容：

  - 配置 URL 筛选功能。

  - 配置文件传输筛选功能。

## 如何将筛选选项应用于即时消息

在部署智能 IM 消息筛选器工具之前，您需要了解在将消息从一台 Lync Server 2013 服务器路由到另一台服务器时如何应用筛选选项。应用这些筛选选项的方式是一致的，不管服务器是位于单个组织中还是跨越多个组织。在消息中插入自定义通知和警告文本以及在服务器之间发送这些消息的方式也是一致的。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>即时消息筛选器使得处理消息中的 URL 所需的 CPU 资源量增加。CPU 需求的增加也会影响 Lync Server 的性能。</td>
</tr>
</tbody>
</table>


通过使用 Lync Server 控制面板中的“IM 和状态”组的“URL 筛选器”页面，可以阻止一些或全部超链接，还可以配置警告。选择“超链接前缀”选项“发送警告消息”后，警告将插入到包含超链接的即时消息的开头。

当即时消息从一台服务器传输到另一台服务器时，将适用下面的一般准则：

  - 如果服务器阻止即时消息（因为选中了“URL 筛选器”页面上的“阻止带文件扩展名的 URL”复选框，或因为选择了“超链接前缀”选项“阻止超链接”），客户端将收到一条错误消息。后续服务器将不会接收此即时消息。

  - 如果服务器 (Server1) 将警告添加到包含活动超链接的即时消息，则接收此即时消息的后续服务器 (Server2) 仍然可以基于该即时消息中存在的这个活动超链接来采取不同的操作，并阻止该即时消息或添加警告。如果 Server2 配置为仅为此 URL 添加警告，则以前由 Server1 添加的警告将被删除，在 Server2 上配置的警告将添加到该即时消息的开头。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>如果您在混合环境中运行 Lync Server 2013，则 Live Communications Server 2005 SP1 是使用智能 IM 筛选器应用程序所需的最低版本。不带 SP1 的 Live Communications Server 2005 不支持智能 IM 筛选器。</td>
</tr>
</tbody>
</table>


## URL 筛选

将根据超链接前缀来筛选 URL。下面是有效前缀示例：

  - www\*.

  - ftp.

  - http:

如果您没有将即时消息筛选器配置为执行任何 URL 筛选，则包含在即时消息中的所有 URL 未经修改就可通过服务器。如果将即时消息筛选器配置为执行 URL 筛选，则将根据“编辑 URL 筛选器”或“新建 URL 筛选器”对话框中选择的选项来筛选即时消息中的 URL。

  - **启用 URL 筛选器** 此选项为全局部署或您选择的站点启用 URL 筛选。

  - **阻止带文件扩展名的 URL** 即时消息筛选器阻止包含具有“编辑文件筛选器”对话框的“要阻止的文件类型扩展名”下所列扩展名的文件的任何活动 Intranet 或 Internet URL。阻止 URL 之后，会向发送方显示一条错误消息。如果选择了此选项，则此选项优先于针对“要阻止的文件类型扩展名”下定义的任何文件扩展名的所有其他筛选选项。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>文件扩展名筛选仅限于标准文件名。筛选对于嵌入在其他名称中的文件扩展名不起作用。</td>
    </tr>
    </tbody>
    </table>


要配置即时消息对话中处理超链接的方式，请选择“超链接前缀”下的以下选项之一：

  - **不筛选** 消息中的 URL 通过服务器发送。选择此选项后，将显示“允许消息”框。在“允许消息”框中，指定要插入到每条包含超链接的即时消息开头的通知。此通知最多包含 65535 个字符。

  - **阻止超链接**Lync Server 阻止发送包含活动超链接的即时消息，并会向发送方显示一条错误消息。

  - **发送警告消息**Lync Server 允许在即时消息中包含活动超链接，但同时会包含警告。选择此选项后，将显示“警告消息”框。在“警告消息”框中，必须键入希望在包含有效超链接的即时消息中包含的警告。例如，此警告可以声明单击未知链接的潜在危险，或者引用您所在组织的相关策略和要求。此警告最多可包含 65535 个字符。

如果选择“阻止超链接”或“发送警告消息”，则下列选项可用：

  - **排除本地 Intranet 超链接** 即时消息筛选器只能阻止 Internet URL。Intranet 中的 URL 未经修改即可通过服务器。但是，各个运行 Lync Server 传递的服务器的 Intranet URL 取决于被视为其 Intranet 区域一部分的本地网站类型。要检查服务器的 Intranet 区域设置，请参阅[修改默认 URL 筛选器](lync-server-2013-modify-the-default-url-filter.md)中的“在 Internet Explorer 中配置您的 Intranet 设置”。

  - **筛选这些超链接前缀** 要选择希望阻止的前缀，请单击“选择”，然后在“选择超链接前缀”中，向“超链接前缀”列表中添加前缀。
    
    除了 **href** 之外，所有前缀都必须以句点或冒号结尾，或以星号后面跟一个句点结尾。有效前缀可包含有效 URL 字符集合中的任何字符，星号 (\*) 除外。有效 URL 字符集合包括：\#\*+/0123456789=@ABCDEFGHIJKLMNOPQRSTUVWXYZ^\_\` abcdefghijklmnopqrstuvwxyz|~

## 文件传输筛选

文件传输筛选既影响即时消息，又影响会议。对于会议来说，这些设置影响 Office Live Meeting 2007 客户端中的讲义功能和多媒体播放功能。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 还提供了文件传输设置选项。除了提供客户端控制外，Lync Server 中还提供了此服务器端选项。</td>
</tr>
</tbody>
</table>


可以在即时消息对话过程中、使用 Office Live Meeting 2007 客户端的讲义功能以及多媒体播放功能时，针对所有文件类型筛选文件传输。可以设置以下选项来控制文件传输：

  - **启用文件筛选器** 此选项为全局部署或您选择的站点启用文件筛选。
    
    启用文件筛选器后，可以在“文件传输”中选择以下选项之一：
    
      - **阻止特定文件类型** 通过指定要阻止的文件扩展名列表来指定服务器筛选的文件传输请求。列表中的条目可以包含所有标准字符，但不能包含通配符 (\*)。Office Live Meeting 2007 客户端中启用讲义功能，但无法上载或下载具有该扩展名的任何文件。如果针对“URL 筛选器”选项卡上列出的某个 URL 筛选器的设置选中“阻止带文件扩展名的 URL”复选框，则 URL 筛选器使用此相同的列表来阻止包含其中任何文件扩展名的活动超链接。要选择希望阻止的文件类型，请单击“选择”，然后在“选择文件类型”中，将这些文件类型扩展名添加到“选中的文件类型扩展名”列表中。
    
      - **全部阻止** 服务器将删除包含文件传输请求的所有即时消息并向该请求的发送方返回一条错误消息。Office Live Meeting 2007 客户端中的讲义功能被禁用。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>文件扩展名筛选仅限于标准文件名。筛选对于嵌入在其他名称中的文件扩展名不起作用。</td>
</tr>
</tbody>
</table>


## 本节内容

  - [修改默认文件传输筛选器](lync-server-2013-modify-the-default-file-transfer-filter.md)

  - [为特定站点创建新文件传输筛选器](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)

  - [修改默认 URL 筛选器](lync-server-2013-modify-the-default-url-filter.md)

  - [创建新 URL 筛选器以处理 IM 对话中的超链接](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)

## 另请参阅

#### 其他资源

[在 Lync Server 2013 中管理 IM 和状态设置](lync-server-2013-managing-im-and-presence-settings.md)

