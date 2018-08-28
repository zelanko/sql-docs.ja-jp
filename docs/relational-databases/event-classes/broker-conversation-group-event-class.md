---
title: Broker:Conversation Group イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Broker:Conversation Group event class
ms.assetid: 6595bef6-9d40-42eb-a934-735622dd23fb
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ce82ac9ac7bc81a34d6d191913824d9f9f74ac8a
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43076245"
---
# <a name="brokerconversation-group-event-class"></a>Broker:Conversation Group イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Service Broker で新しいメッセージ交換グループが作成されたり、既存のメッセージ交換グループが削除されると、 **Broker:Conversation Group** イベントが生成されます。  
  
## <a name="brokerconversation-group-event-class-data-columns"></a>Broker:Conversation Group イベント クラスのデータ列  
  
|データ列|型|[説明]|列番号|フィルターの適用|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|[ユーザー アカウント制御]|  
|**ClientProcessID**|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターによって割り当てられた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|[ユーザー アカウント制御]|  
|**DatabaseID**|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|**EventClass**|**int**|キャプチャされたイベント クラスの種類。 **Broker:Conversation Group** の場合は、常に **136**です。|27|いいえ|  
|**EventSequence**|**int**|このイベントのシーケンス番号。|51|いいえ|  
|**EventSubClass**|**nvarchar**|イベント サブクラスの種類です。各イベント クラスについての詳細な情報を提供します。 この列には次の値が含まれます。<br /><br /> **[作成]**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、新しいメッセージ交換グループが作成されました。<br /><br /> **[削除]**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、メッセージ交換グループが削除されました。|21|[ユーザー アカウント制御]|  
|**GUID**|**uniqueidentifier**|このイベントが示すメッセージ交換グループのメッセージ交換グループ ID。|54|いいえ|  
|**HostName**|**nvarchar**|クライアントが実行しているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|[ユーザー アカウント制御]|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|いいえ|  
|**LoginSid**|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 各 SID はサーバーのログインごとに一意です。|41|[ユーザー アカウント制御]|  
|**NTDomainName**|**nvarchar**|ユーザーが属している Windows ドメイン。|7|[ユーザー アカウント制御]|  
|**NTUserName**|**nvarchar**|このイベントが生成された接続を所有するユーザーの名前。|6|[ユーザー アカウント制御]|  
|**ServerName**|**nvarchar**|トレースされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SPID**|**int**|クライアントに関連付けられているプロセスに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって割り当てられているサーバー プロセス ID。|12|[ユーザー アカウント制御]|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|**TransactionID**|**bigint**|トランザクションに対してシステムが割り当てた ID。|4|いいえ|  
  
  
