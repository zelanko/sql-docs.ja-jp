---
title: Broker:Activation イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2562f3931f98c040bb3dc475e3863bb6396dbbf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62664348"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation イベント クラス
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で **Broker:Activation** イベントが生成されるのは、キュー モニターがアクティブ化ストアド プロシージャを開始して QUEUE_ACTIVATION 通知を送信するとき、またはキュー モニターによって開始されたアクティブ化ストアド プロシージャが終了するときです。  
  
## <a name="brokeractivation-event-class-data-columns"></a>Broker:Activation イベント クラスのデータ列  
  
|データ列|種類|[説明]|列番号|フィルターの適用|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|`int`|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターによって割り当てられた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|はい|  
|**DatabaseID**|`int`|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database*ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]では、 **ServerName**データ列がトレースにキャプチャされ、そのサーバーが使用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|**EventClass**|`int`|キャプチャされたイベント クラスの種類。 
  **Broker:Activation** の場合は、常に **163**です。|27|いいえ|  
|**EventSequence**|`int`|このイベントのシーケンス番号。|51|いいえ|  
|**EventSubClass**|`nvarchar`|このイベントが報告する特定の操作。 次のいずれかの値:<br /><br /> **開始**: <br />                
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がアクティブ化ストアド プロシージャを開始しました。<br /><br /> **終了**: アクティブ化ストアドプロシージャが正常に終了しました。<br /><br /> **aborted**: アクティブ化ストアドプロシージャがエラーで終了しました。|21|いいえ|  
|**名**|`nvarchar`|クライアントが実行しているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|**IntegerData**|`int`|このキューでアクティブなタスクの数。|25|いいえ|  
|**Issystem で**|`int`|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|いいえ|  
|**LoginSid**|`image`|ログイン ユーザーのセキュリティ ID 番号 (SID)。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|**NTDomainName**|`nvarchar`|ユーザーが属している Windows ドメイン。|7|はい|  
|**NTUserName**|`nvarchar`|このイベントが生成された接続を所有するユーザーの名前。|6|はい|  
|**ObjectID**|`int`|このイベントに関連付けられたキュー。|22|いいえ|  
|**Server**|`nvarchar`|トレースされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**調べる**|`int`|クライアントに関連付けられているプロセスに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって割り当てられているサーバー プロセス ID。|12|はい|  
|**StartTime**|`datetime`|イベントの開始時刻 (取得できた場合)。|14|はい|  
|**TransactionID**|`bigint`|トランザクションに対してシステムが割り当てた ID。|4|いいえ|  
  
  
