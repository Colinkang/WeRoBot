消息
==========
目前WeRoBot共有以下几种Message： `TextMessage` ， `ImageMessage` ， `LocationMessage` ， `EventMessage` 和 `UnknownMessage` 。他们都继承自 WeChatMessage 。

TextMessage
------------

TextMessage的属性：


======== ===================================
name      value
======== ===================================
id        消息id，64位整型 [2]_
type      'text'
target    信息的目标用户。通常是机器人用户。
source    信息的来源用户。通常是发送信息的用户。
time      信息发送的时间，一个UNIX时间戳。
content   信息的内容
======== ===================================

ImageMessage
-------------

ImageMessage的属性：

======= ==================================
name     value
======= ==================================
id       消息id，64位整型 [2]_
type     'image'
target   信息的目标用户。通常是机器人用户。
source   信息的来源用户。通常是发送信息的用户。
time     信息发送的时间，一个UNIX时间戳。
img      图片网址。你可以从这个网址下到图片
======= ==================================

LinkMessage
------------
============    ==================================
name             value
============    ==================================
id               消息id，64位整型 [2]_
type             'link'
target           信息的目标用户。通常是机器人用户。
source           信息的来源用户。通常是发送信息的用户。
time             信息发送的时间，一个UNIX时间戳。
title            消息标题
description      消息描述
url              消息链接
============    ==================================


LocationMessage
----------------

LocationMessage的属性：

========= ===================================
name       value
========= ===================================
id         消息id，64位整型 [2]_
type       'location'
target     信息的目标用户。通常是机器人用户。
source     信息的来源用户。通常是发送信息的用户。
time       信息发送的时间，一个UNIX时间戳。
location   一个元组。(纬度, 经度)
scale      地图缩放大小
label      地理位置信息
========= ===================================

EventMessage
--------------

EventMessage的属性：

========= =====================================
name       value
========= =====================================
type       'subscribe' 'unsubscribe' 或 'click' [1]_
target     信息的目标用户。通常是机器人用户。
source     信息的来源用户。通常是发送信息的用户。
time       信息发送的时间，一个UNIX时间戳。
key        事件 key 值。当 type = 'click' 时存在。
========= =====================================

UnknownMessage
---------------

UnknownMessage的属性：

========= =====================================
name       value
========= =====================================
type       'unknown'
content    请求的正文部分。标准的XML格式。
========= =====================================

.. note:: 如果你不为 WeRoBot 贡献代码，你完全可以无视掉 UnknownMessage 。在正常的使用中，WeRoBot应该不会收到 `UnknownMessage` ——除非 WeRoBot 停止开发。

.. [1] 当你被用户关注时，会收到 type='subscribe' 的事件； 被取消关注时是 type='unsubscribe'  。
.. [2] 截至目前（ 2013.03.16 ），微信机器人所收到的消息中都不包含 MsgID.