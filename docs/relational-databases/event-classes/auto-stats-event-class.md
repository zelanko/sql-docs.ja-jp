---
title: Auto Stats イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Auto Stats event class
ms.assetid: cd613fce-01e1-4d8f-86cc-7ffbf0759f9e
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24ab2577ca22083c298b6f5b5099aee2a96b59c2
ms.sourcegitcommit: 01fccb8015644e75fd99fc5543d8216a1539f6ca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2018
ms.locfileid: "40405431"
---
# <a name="auto-stats-event-class"></a>Auto Stats イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **Auto Stats** イベント クラスは、インデックス統計と列統計が自動更新されたことを示します。  **Auto Stats** は、オプティマイザーで使用するために統計情報が読み込まれるときにも呼び出されます。
  
## <a name="auto-stats-event-class-data-columns"></a>Auto Stats イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|[ユーザー アカウント制御]|  
|**ClientProcessID**|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|[ユーザー アカウント制御]|  
|**DatabaseID**|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|**DatabaseName**|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|[ユーザー アカウント制御]|  
|**Duration**|**bigint**|イベントにかかった時間 (マイクロ秒)。|13|[ユーザー アカウント制御]|  
|**EndTime**|**datetime**|イベントの終了時刻。|15|[ユーザー アカウント制御]|  
|**Error**|**int**|特定のイベントのエラー番号。 多くの場合、 **sys.messages** カタログ ビューに保存されているエラー番号です。|31|[ユーザー アカウント制御]|  
|**EventClass**|**int**|イベントの種類 = 58。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**EventSubClass**|**int**|イベント サブクラスの種類。<br /><br /> 1: 統計の同期的な作成/更新。 **TextData** 列に、どの統計が作成または更新されたのか、あるいはされていないのかが示されます。<br /><br /> 2: 統計の非同期更新。ジョブがキューに登録されました。<br /><br /> 3: 統計の非同期更新。ジョブが開始しました。<br /><br /> 4: 統計の非同期更新。ジョブが完了しました。|21|[ユーザー アカウント制御]|  
|**GroupID**|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
|**HostName**|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|[ユーザー アカウント制御]|  
|**IndexID**|**int**|イベントの影響を受けるオブジェクトに付けられたインデックスまたは統計エントリの ID。 オブジェクトのインデックス ID を特定するには、 **sys.indexes** カタログ ビューの **index_id** 列を使用します。|24|[ユーザー アカウント制御]|  
|**IntegerData**|**int**|正常に更新された統計コレクションの数。|25|[ユーザー アカウント制御]|  
|**IntegerData2**|**int**|ジョブ シーケンス番号。|55|[ユーザー アカウント制御]|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|[ユーザー アカウント制御]|  
|**LoginName**|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の Windows ログイン資格情報)。|11|[ユーザー アカウント制御]|  
|**LoginSid**|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、 **sys.server_principals** カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|[ユーザー アカウント制御]|  
|**NTDomainName**|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|[ユーザー アカウント制御]|  
|**NTUserName**|**nvarchar**|Windows のユーザー名。|6|[ユーザー アカウント制御]|  
|**Exchange Spill**|**int**|システムによって割り当てられたオブジェクト ID。|22|[ユーザー アカウント制御]|  
|**RequestID**|**int**|ステートメントが含まれている要求の ID。|49|[ユーザー アカウント制御]|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|**成功**|**int**|0 = エラー。<br /><br /> 1 = 成功。<br /><br /> 2 = サーバーの絞込みによりスキップ (MSDE)。|23|[ユーザー アカウント制御]|  
|**TextData**|**ntext**|この列の内容は、統計が同期的に更新されたのか、または非同期に更新されたのかによって異なります。同期更新の場合**EventSubClass** は 1、非同期更新の場合**EventSubClass** は 2、3、または 4 になります。<br /><br /> 1: 更新または作成された統計をリストで示します。<br /><br /> 2、3、または 4: NULL。 **IndexID** 列には、更新された統計のインデックスまたは統計の ID が格納されます。|1|[ユーザー アカウント制御]|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|[ユーザー アカウント制御]|  
|**型**|**int**|ジョブの種類。|57|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
