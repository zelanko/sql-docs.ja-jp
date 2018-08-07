---
title: Broker:Forwarded Message Sent イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Broker:Forwarded Message Sent event class
ms.assetid: d0ef74d9-a4ef-4918-aa21-6b267e85569f
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ba053dfbcc3e3a15ccc587c99a953090f1ba6868
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553532"
---
# <a name="brokerforwarded-message-sent-event-class"></a>Broker:Forwarded Message Sent イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、Service Broker がメッセージを転送するときに、Broker:Forwarded Message Sent イベントを生成します。  
  
## <a name="brokerforwarded-message-sent-event-class-data-columns"></a>Broker:Forwarded Message Sent イベント クラスのデータ列  
  
|データ列|型|[説明]|列番号|フィルターの適用|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|[ユーザー アカウント制御]|  
|BigintData1|**bigint**|メッセージのシーケンス番号。|52|いいえ|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターによって割り当てられた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|[ユーザー アカウント制御]|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database*ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|DBUserName|**nvarchar**|メッセージ送信元のサービスのブローカー インスタンス ID。|40|いいえ|  
|EventClass|**int**|キャプチャされたイベント クラスの種類。 Broker:Forwarded Message Sent の場合は、常に 139 です。|27|いいえ|  
|EventSequence|**int**|このイベントのシーケンス番号。|51|いいえ|  
|FileName|**nvarchar**|メッセージの送信先のサービス名。|36|いいえ|  
|GUID|**uniqueidentifier**|ダイアログのメッセージ交換 ID。 この ID はメッセージの一部として転送され、メッセージ交換の両側で共有されます。|54|いいえ|  
|HostName|**nvarchar**|クライアントが実行しているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|[ユーザー アカウント制御]|  
|IndexID|**int**|転送されるメッセージに残っているホップの数。|24|いいえ|  
|IntegerData|**int**|転送されるメッセージのフラグメント番号。|25|いいえ|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|いいえ|  
|LoginSid|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 各 SID はサーバーのログインごとに一意です。|41|[ユーザー アカウント制御]|  
|NTDomainName|**nvarchar**|ユーザーが属している Windows ドメイン。|7|[ユーザー アカウント制御]|  
|NTUserName|**nvarchar**|このイベントが生成された接続を所有するユーザーの名前。|6|[ユーザー アカウント制御]|  
|ObjectId|**int**|メッセージが転送されたときの、その転送メッセージの有効期限の値。|22|いいえ|  
|ObjectName|**nvarchar**|転送されたメッセージのメッセージ ID。|34|いいえ|  
|OwnerName|**nvarchar**|メッセージ送信先のブローカー ID。|37|いいえ|  
|RoleName|**nvarchar**|メッセージ交換ハンドルのロール。 有効な値は、<br /><br /> Initiator。 このブローカーがメッセージ交換の発信側です。<br /><br /> Target。 このブローカーがメッセージ交換の発信先です。|38|いいえ|  
|ServerName|**nvarchar**|トレースされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|SPID|**int**|クライアントに関連付けられているプロセスに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって割り当てられているサーバー プロセス ID。|12|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|成功|**int**|転送処理にかかった時間。|23|いいえ|  
|TargetLoginName|**nvarchar**|このインスタンスがメッセージを送信したネットワーク アドレス。 このネットワーク アドレスはメッセージの最終送信先とは異なる場合があるので注意してください。|42|いいえ|  
|TargetUserName|**nvarchar**|メッセージを発信したサービスの名前。|39|いいえ|  
|TransactionID|**bigint**|トランザクションに対してシステムが割り当てた ID。|4|いいえ|  
  
  
