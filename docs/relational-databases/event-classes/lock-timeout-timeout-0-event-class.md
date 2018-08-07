---
title: Lock:Timeout (timeout &gt; 0) イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Timeout event class
ms.assetid: d755833a-d7eb-4973-9352-67a2fba2442a
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 9d7151cb4fb3ba3fe436ad201caf2122e3c5584d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39564206"
---
# <a name="locktimeout-timeout-gt-0-event-class"></a>Lock:Timeout (timeout &gt; 0) イベント クラス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **Lock:Timeout (timeout > 0)** イベント クラスは、要求したリソースで別のトランザクションがブロッキング ロックを保持しているために、ページなどのリソースのロック要求がタイムアウトしたことを示します。 このイベント クラスの動作は、タイムアウト値が 0 であるイベントを含まないことを除いて、**Lock:Timeout** イベント クラスと同じです。  
  
 タイムアウト値が 0 のロックのプローブやその他のプロセスを使用しているトレースに、**Lock:Timeout (timeout > 0)** イベント クラスを含めます。 これにより、タイムアウト値が 0 のイベントを除外して、実際にタイムアウトが発生しているイベントを確認できます。  
  
## <a name="locktimeout-timeout--0-event-class-data-columns"></a>Lock:Timeout (timeout > 0) イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|[ユーザー アカウント制御]|  
|BinaryData|**image**|ロック リソース ID。|2|[ユーザー アカウント制御]|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|[ユーザー アカウント制御]|  
|DatabaseID|**int**|タイムアウトが発生したデータベースの ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|DatabaseName|**nvarchar**|タイムアウトが発生したデータベースの名前。|35|[ユーザー アカウント制御]|  
|Duration|**bigint**|イベントにかかった時間 (マイクロ秒)。|13|[ユーザー アカウント制御]|  
|EndTime|**datetime**|イベントの終了時刻。 **SQL:BatchStarting** や **SP:Starting**などの開始イベント クラスについては、この列に値が格納されません。|15|[ユーザー アカウント制御]|  
|EventClass|**int**|イベントの種類 = 189。|27|いいえ|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
|HostName|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|[ユーザー アカウント制御]|  
|IntegerData2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|[ユーザー アカウント制御]|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|[ユーザー アカウント制御]|  
|LoginName|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|[ユーザー アカウント制御]|  
|LoginSid|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|[ユーザー アカウント制御]|  
|モード|**int**|イベントが受信された状態またはイベントを要求中の状態。<br /><br /> 0 = NULL<br /><br /> 1 = Sch-S<br /><br /> 2 = Sch-M<br /><br /> 3 = S<br /><br /> 4 = U<br /><br /> 5 = X<br /><br /> 6 = IS<br /><br /> 7 = IU<br /><br /> 8 = IX<br /><br /> 9 = SIU<br /><br /> 10 = SIX<br /><br /> 11 = UIX<br /><br /> 12 = BU<br /><br /> 13 = RangeS-S<br /><br /> 14 = RangeS-U<br /><br /> 15 = RangeI-N<br /><br /> 16 = RangeI-S<br /><br /> 17 = RangeI-U<br /><br /> 18 = RangeI-X<br /><br /> 19 = RangeX-S<br /><br /> 20 = RangeX-U<br /><br /> 21 = RangeX-X|32|[ユーザー アカウント制御]|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|[ユーザー アカウント制御]|  
|NTUserName|**nvarchar**|Windows のユーザー名。|6|[ユーザー アカウント制御]|  
|ObjectID|**int**|オブジェクトの ID (使用可能かつ適用可能な場合)。|22|[ユーザー アカウント制御]|  
|ObjectID2|**bigint**|関連するオブジェクトまたはエンティティの ID (使用可能かつ適用可能な場合)。|56|[ユーザー アカウント制御]|  
|OwnerID|**int**|1 = TRANSACTION<br /><br /> 2 = CURSOR<br /><br /> 3 = SESSION<br /><br /> 4 = SHARED_TRANSACTION_WORKSPACE<br /><br /> 5 = EXCLUSIVE_TRANSACTION_WORKSPACE|58|[ユーザー アカウント制御]|  
|RequestID|**int**|ステートメントが含まれている要求の ID。|49|[ユーザー アカウント制御]|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|トレースでキャプチャされたイベント クラスに依存するテキスト値。|1|[ユーザー アカウント制御]|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|[ユーザー アカウント制御]|  
|型|**int**|1 = NULL_RESOURCE<br /><br /> 2 = DATABASE<br /><br /> 3 = FILE<br /><br /> 5 = OBJECT<br /><br /> 6 = PAGE<br /><br /> 7 = KEY<br /><br /> 8 = EXTENT<br /><br /> 9 = RID<br /><br /> 10 = APPLICATION<br /><br /> 11 = METADATA<br /><br /> 12 = AUTONAMEDB<br /><br /> 13 = HOBT<br /><br /> 14 = ALLOCATION_UNIT|57|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [Lock:Timeout イベント クラス](../../relational-databases/event-classes/lock-timeout-event-class.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
  
