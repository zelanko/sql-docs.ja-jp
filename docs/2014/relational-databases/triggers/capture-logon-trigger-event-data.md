---
title: ログオン トリガーのイベント データのキャプチャ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
ms.openlocfilehash: b11323702d7468d07783b4d1c763dba691479d9c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043059"
---
# <a name="capture-logon-trigger-event-data"></a>ログオン トリガーのイベント データのキャプチャ
  ログオン トリガー内で使用するために LOGON イベントに関する XML データをキャプチャするには、 [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) 関数を使用します。 LOGON イベントは、次のイベントのデータ スキーマを返します。  
  
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
  
  
