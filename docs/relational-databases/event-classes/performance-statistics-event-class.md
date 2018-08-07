---
title: Performance Statistics イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Performance Statistics event class
ms.assetid: da9cd2c4-6fdd-4ada-b74f-105e3541393c
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 3a7c23b83d0ddd5c923dec9c39e582103f538d7c
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39558662"
---
# <a name="performance-statistics-event-class"></a>Performance Statistics イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Performance Statistics イベント クラスは、実行中のクエリ、ストアド プロシージャ、およびトリガーのパフォーマンスを監視するために使用できます。 6 個のイベント サブクラスがあり、それぞれがシステム内のクエリ、ストアド プロシージャ、およびトリガーの有効期間内のイベントを示します。 これらのイベント サブクラスを、関連する sys.dm_exec_query_stats、sys.dm_exec_procedure_stats、および sys.dm_exec_trigger_stats 動的管理ビューと組み合わせて使用することで、クエリ、ストアド プロシージャ、トリガーのパフォーマンス履歴を再構成できます。  
  
## <a name="performance-statistics-event-class-data-columns"></a>Performance Statistics イベント クラスのデータ列  
 次の表では、EventSubClass 0、EventSubClass 1、EventSubClass 2、EventSubClass 3、EventSubClass 4、および EventSubClass 5 の各イベント サブクラスに関連するイベント クラスのデータ列について説明します。  
  
### <a name="eventsubclass-0"></a>EventSubclass 0  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BigintData1|**bigint**|NULL|52|[ユーザー アカウント制御]|  
|BinaryData|**image**|NULL|2|[ユーザー アカウント制御]|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 0 = 現在キャッシュ内にない新しいバッチ SQL テキスト。<br /><br /> アドホック バッチのトレースで、次の種類の EventSubClass が生成されます。<br /><br /> *n* 個のクエリを持つアドホック バッチでは、次のようになります。<br /><br /> 種類 0 が 1 個|21|[ユーザー アカウント制御]|  
|IntegerData2|**int**|NULL|55|[ユーザー アカウント制御]|  
|ObjectID|**int**|NULL|22|[ユーザー アカウント制御]|  
|Offset|**int**|NULL|61|[ユーザー アカウント制御]|  
|PlanHandle|**Image**|NULL|65|[ユーザー アカウント制御]|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**image**|sys.dm_exec_sql_text 動的管理ビューを使用してバッチ SQL テキストを取得するために使用できる SQL ハンドル。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|バッチの SQL テキスト。|1|[ユーザー アカウント制御]|  
  
### <a name="eventsubclass-1"></a>EventSubclass 1  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BigintData1|**bigint**|このプランが再コンパイルされた累積回数。|52|[ユーザー アカウント制御]|  
|BinaryData|**image**|コンパイル済みプランのバイナリ XML。|2|[ユーザー アカウント制御]|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 1 = ストアド プロシージャ内のクエリがコンパイルされました。<br /><br /> ストアド プロシージャのトレースで、次の種類の EventSubClass が生成されます。<br /><br /> *n* 個のクエリを持つストアド プロシージャでは、次のようになります。<br /><br /> 種類 1 が*n* 個|21|[ユーザー アカウント制御]|  
|IntegerData2|**int**|ストアド プロシージャ内のステートメントの最後。<br /><br /> ストアド プロシージャの最後に達すると -1 になります。|55|[ユーザー アカウント制御]|  
|ObjectID|**int**|システムによって割り当てられたオブジェクト ID。|22|[ユーザー アカウント制御]|  
|Offset|**int**|ストアド プロシージャ内またはバッチ内のステートメントの開始オフセット。|61|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**image**|dm_exec_sql_text 動的管理ビューを使用してストアド プロシージャの SQL テキストを取得するために使用できる SQL ハンドル。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|NULL|1|[ユーザー アカウント制御]|  
|PlanHandle|**image**|ストアド プロシージャのコンパイル済みプランのプラン ハンドル。 sys.dm_exec_query_plan 動的管理ビューを使用して XML プランを取得するために使用できます。|65|[ユーザー アカウント制御]|  
|ObjectType|**int**|イベントに関係するオブジェクトの種類を表す値。<br /><br /> 8272 = ストアド プロシージャ|28|[ユーザー アカウント制御]|  
|BigintData2|**bigint**|コンパイル中に使用されたメモリの合計 (KB 単位)。|53|[ユーザー アカウント制御]|  
|CPU|**int**|コンパイル中に使用された CPU 時間の合計 (ミリ秒単位)。|18|[ユーザー アカウント制御]|  
|Duration|**int**|コンパイル中に使用された時間の合計 (マイクロ秒単位)。|13|[ユーザー アカウント制御]|  
|IntegerData|**int**|コンパイル済みプランのサイズ (KB 単位)。|25|[ユーザー アカウント制御]|  
  
### <a name="eventsubclass-2"></a>EventSubClass 2  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BigintData1|**bigint**|このプランが再コンパイルされた累積回数。|52|[ユーザー アカウント制御]|  
|BinaryData|**image**|コンパイル済みプランのバイナリ XML。|2|[ユーザー アカウント制御]|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 2 = アドホック SQL ステートメント内のクエリがコンパイルされました。<br /><br /> アドホック バッチのトレースで、次の種類の EventSubClass が生成されます。<br /><br /> *n* 個のクエリを持つアドホック バッチでは、次のようになります。<br /><br /> 種類 2 が*n* 個|21|[ユーザー アカウント制御]|  
|IntegerData2|**int**|バッチ内のステートメントの最後。<br /><br /> バッチの最後に達すると -1 になります。|55|[ユーザー アカウント制御]|  
|ObjectID|**int**|なし|22|[ユーザー アカウント制御]|  
|Offset|**int**|バッチ内のステートメントの開始オフセット。<br /><br /> バッチの開始時は 0 です。|61|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**image**|SQL ハンドル。 dm_exec_sql_text 動的管理ビューを使用してバッチ SQL テキストを取得するために使用できます。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|NULL|1|[ユーザー アカウント制御]|  
|PlanHandle|**image**|バッチのコンパイル済みプランのプラン ハンドル。 dm_exec_query_plan 動的管理ビューを使用してバッチ XML プランを取得するために使用できます。|65|[ユーザー アカウント制御]|  
|BigintData2|**bigint**|コンパイル中に使用されたメモリの合計 (KB 単位)。|53|[ユーザー アカウント制御]|  
|CPU|**int**|コンパイル中に使用された CPU 時間の合計 (マイクロ秒単位)。|18|[ユーザー アカウント制御]|  
|Duration|**int**|コンパイル中に使用された時間の合計 (ミリ秒単位)。|13|[ユーザー アカウント制御]|  
|IntegerData|**int**|コンパイル済みプランのサイズ (KB 単位)。|25|[ユーザー アカウント制御]|  
  
### <a name="eventsubclass-3"></a>EventSubClass 3  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BigintData1|**bigint**|このプランが再コンパイルされた累積回数。|52|[ユーザー アカウント制御]|  
|BinaryData|**image**|NULL|2|[ユーザー アカウント制御]|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 3 = キャッシュされたクエリが破棄され、プランに関連付けられたパフォーマンス履歴データが破棄されようとしています。<br /><br /> トレースで、次の種類の EventSubClass が生成されます。<br /><br /> *n* 個のクエリを持つアドホック バッチでは、次のようになります。<br /><br /> クエリがキャッシュからフラッシュされるときは種類 3 が 1 個<br /><br /> *n* 個のクエリを持つストアド プロシージャでは、次のようになります。<br /><br /> クエリがキャッシュからフラッシュされるときは種類 3 が 1 個。|21|[ユーザー アカウント制御]|  
|IntegerData2|**int**|ストアド プロシージャまたはバッチ内のステートメントの最後。<br /><br /> ストアド プロシージャまたはバッチの最後に達すると -1 になります。|55|[ユーザー アカウント制御]|  
|ObjectID|**int**|NULL|22|[ユーザー アカウント制御]|  
|Offset|**int**|ストアド プロシージャ内またはバッチ内のステートメントの開始オフセット。<br /><br /> ストアド プロシージャまたはバッチの開始時は 0 です。|61|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**image**|dm_exec_sql_text 動的管理ビューを使用してストアド プロシージャまたはバッチ SQL テキストを取得するために使用できる SQL ハンドル。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|クエリ実行の統計情報。|1|[ユーザー アカウント制御]|  
|PlanHandle|**image**|ストアド プロシージャまたはバッチのコンパイル済みプランのプラン ハンドル。 dm_exec_query_plan 動的管理ビューを使用して XML プランを取得するために使用できます。|65|[ユーザー アカウント制御]|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
  
### <a name="eventsubclass-4"></a>EventSubClass 4  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BigintData1|**bigint**|NULL|52|[ユーザー アカウント制御]|  
|BinaryData|**image**|NULL|2|[ユーザー アカウント制御]|  
|DatabaseID|**int**|指定されたストアド プロシージャが存在するデータベースの ID。|3|[ユーザー アカウント制御]|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 4 = キャッシュされたストアド プロシージャがキャッシュから削除されており、そのストアド プロシージャに関連付けられたパフォーマンス履歴データが破棄されようとしています。|21|[ユーザー アカウント制御]|  
|IntegerData2|**int**|NULL|55|[ユーザー アカウント制御]|  
|ObjectID|**int**|ストアド プロシージャの ID。 sys.procedures の object_id 列と同じです。|22|[ユーザー アカウント制御]|  
|Offset|**int**|NULL|61|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**image**|dm_exec_sql_text 動的管理ビューを使用して実行されたストアド プロシージャ SQL テキストを取得するために使用できる SQL ハンドル。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|ProcedureExecutionStats|1|[ユーザー アカウント制御]|  
|PlanHandle|**image**|ストアド プロシージャのコンパイル済みプランのプラン ハンドル。 dm_exec_query_plan 動的管理ビューを使用して XML プランを取得するために使用できます。|65|[ユーザー アカウント制御]|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
  
### <a name="eventsubclass-5"></a>EventSubClass 5  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BigintData1|**bigint**|NULL|52|[ユーザー アカウント制御]|  
|BinaryData|**image**|NULL|2|[ユーザー アカウント制御]|  
|DatabaseID|**int**|指定されたトリガーが存在するデータベースの ID。|3|[ユーザー アカウント制御]|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|EventSubClass|**int**|イベント サブクラスの種類。<br /><br /> 5 = キャッシュされたトリガーがキャッシュから削除されており、そのトリガーに関連付けられたパフォーマンス履歴データが破棄されようとしています。|21|[ユーザー アカウント制御]|  
|IntegerData2|**int**|NULL|55|[ユーザー アカウント制御]|  
|ObjectID|**int**|トリガーの ID。 sys.triggers/sys.server_triggers カタログ ビューの object_id 列と同じです。|22|[ユーザー アカウント制御]|  
|Offset|**int**|NULL|61|[ユーザー アカウント制御]|  
|SPID|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|SqlHandle|**image**|dm_exec_sql_text 動的管理ビューを使用してトリガーの SQL テキストを取得するために使用できる SQL ハンドル。|63|[ユーザー アカウント制御]|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|TextData|**ntext**|TriggerExecutionStats|1|[ユーザー アカウント制御]|  
|PlanHandle|**image**|トリガーのコンパイル済みプランのプラン ハンドル。 dm_exec_query_plan 動的管理ビューを使用して XML プランを取得するために使用できます。|65|[ユーザー アカウント制御]|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Showplan XML for Query Compile イベント クラス](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)   
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
