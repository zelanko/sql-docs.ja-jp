---
title: ログオン トリガーのイベント データのキャプチャ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 4a33ca316ee0732782eaddb62ff076b1230771bf
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39565206"
---
# <a name="capture-logon-trigger-event-data"></a>ログオン トリガーのイベント データのキャプチャ
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  ログオン トリガー内で使用するために LOGON イベントに関する XML データをキャプチャするには、 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md) 関数を使用します。 LOGON イベントは、次のイベントのデータ スキーマを返します。  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 `LOGON`を格納します。  
  
 `<PostTime>`  
 セッションの確立が要求される時刻を格納します。  
  
 `<SID>`  
 指定されたログイン名のセキュリティ ID 番号 (SID) の Base 64 エンコード形式のバイナリ ストリームを格納します。  
  
 `<ClientHost>`  
 接続を確立したクライアントのホスト名を格納します。 クライアントとサーバーの名前が同じ場合、この値は '`<local_machine>`' になります。 これらの名前が異なる場合、この値はクライアントの IP アドレスになります。  
  
 `<IsPooled>`  
 接続プールを使用して接続が再利用される場合は `1` になります。 それ以外の場合、値は `0`に設定されます。  
  
  
