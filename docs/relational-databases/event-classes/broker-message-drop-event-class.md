---
title: "Broker:Message Drop イベント クラス | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker:Message Drop event class
ms.assetid: f532b7c9-ca34-4bac-8dc3-53f9895fd6af
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 47fd82b02e3d808d2609e5c9830099d11627795f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="brokermessage-drop-event-class"></a>Broker:Message Drop イベント クラス
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] このインスタンスのサービスに配信する必要のある受信メッセージを、Service Broker が保持できないときに、 **Broker:Message Drop** イベントを生成します。 転送されたメッセージの場合は、「 [Broker:Forwarded Message Dropped イベント クラス](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)」を参照してください。  
  
## <a name="brokermessage-drop-event-class-data-columns"></a>Broker:Message Drop イベント クラスのデータ列  
  
|データ列|型|説明|列番号|フィルターの適用|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**Application Name**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|**BigintData1**|**bigint**|削除されたメッセージのシーケンス番号。|52|いいえ|  
|**BigintData2**|**bigint**|最後に正常に受信確認されたメッセージのシーケンス番号。|53|いいえ|  
|**ClientProcessID**|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターによって割り当てられた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|はい|  
|**DatabaseID**|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|**[エラー]**|**int**|イベント内のテキストの、 **sys.messages** 内でのメッセージ ID 番号。|31|いいえ|  
|**EventClass**|**int**|キャプチャされたイベント クラスの種類。 **Broker:MessageDrop** の場合は、常に **160**です。|27|いいえ|  
|**EventSequence**|**int**|このイベントのシーケンス番号。|51|いいえ|  
|**EventSubClass**|**nvarchar**|削除されたメッセージがシーケンス番号付きメッセージであるかどうかを示します。 次の 2 つの値のいずれかになります。<br /><br /> **Sequenced Message**。 削除されたメッセージはシーケンス番号付きメッセージです。<br /><br /> **Unsequenced Message**。 削除されたメッセージはシーケンス番号付きメッセージではありません。|21|はい|  
|**GUID**|**uniqueidentifier**|削除されたメッセージが所属するメッセージ交換のメッセージ交換 ID。 この ID はメッセージの一部として転送され、メッセージ交換の両側で共有されます。|54|いいえ|  
|**HostName**|**nvarchar**|クライアントが実行しているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|**IntegerData**|**int**|削除されたメッセージのフラグメント番号。|25|いいえ|  
|**IntegerData2**|**int**|削除されたメッセージが受信確認していたメッセージ フラグメント番号。|55|いいえ|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|いいえ|  
|**LoginName**|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\Username という形式の Windows ログイン資格情報)。|11|いいえ|  
|**LoginSid**|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|**NTDomainName**|**nvarchar**|ユーザーが属している Windows ドメイン。|7|はい|  
|**NTUserName**|**nvarchar**|このイベントが生成された接続を所有するユーザーの名前。|6|はい|  
|**ObjectName**|**nvarchar**|ダイアログのメッセージ交換ハンドル。|34|いいえ|  
|**RoleName**|**nvarchar**|メッセージ交換ハンドルのロール。 **initiator** または **target**のいずれかです。|38|いいえ|  
|**ServerName**|**nvarchar**|トレースされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**Severity**|**int**|イベントのテキストの重大度を表す数値。|29|いいえ|  
|**SPID**|**int**|クライアントに関連付けられているプロセスに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって割り当てられているサーバー プロセス ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|可|  
|**状態**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のソース コード内のイベントが生成された場所を示します。 イベントが生成された場所によって、状態コードが異なることがあります。 マイクロソフトのサポート エンジニアはこの状態コードを使用して、イベントが生成されたソース コード内の場所を特定することができます。|30|いいえ|  
|**TextData**|**ntext**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってメッセージが削除された理由。|1|可|  
|**TransactionID**|**bigint**|トランザクションに対してシステムが割り当てた ID。|4|いいえ|  
  
## <a name="see-also"></a>参照  
 [SQL Server Service Broker (SQL Server Service Broker)](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
