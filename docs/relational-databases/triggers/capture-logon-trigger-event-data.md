---
title: "ログオン トリガーのイベント データのキャプチャ | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
caps.latest.revision: 5
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 790a086c90eeeeb606a86056f239853d805cb091
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="capture-logon-trigger-event-data"></a>ログオン トリガーのイベント データのキャプチャ
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
  
  

