---
title: "拡張イベントのツール | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
  - "xevents"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "拡張イベント [SQL Server]、使用"
  - "拡張イベント [SQL Server]、使用するオプション"
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
caps.latest.revision: 19
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 19
---
# 拡張イベントのツール
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張イベント セッションの作成と管理には、次のツールを使用できます。  
  
-   データ定義言語 (DDL) ステートメント。 拡張イベント セッションの作成および変更に使用できます。  
  
-   動的管理ビュー、カタログ ビュー、およびシステム テーブル。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、セッション データやメタデータを取得することができます。 システム テーブルを使用すると、SQL トレース イベントのクラスや列と等価な既存の拡張イベントを特定できます。  
  
-   オブジェクト エクスプローラーの **[拡張イベント]** ノード。 セッションの開始、停止、削除のほか、セッション テンプレートのインポートとエクスポートを行うことができます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダー。 拡張イベント セッションの作成、変更、および管理に使用できる強力なツールです。 詳細については、「[拡張イベントへの PowerShell プロバイダーの使用](../../relational-databases/extended-events/use-the-powershell-provider-for-extended-events.md)」を参照してください。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]」を参照してください。 拡張イベントのトピックに用意されているコード サンプルを作成し、実行することができます。 詳細については、「[オブジェクト エクスプローラー](../../ssms/object/object-explorer.md)」を参照してください。  
  
 自分が作成したセッション以外にも、サーバーには、既定のシステム正常性セッションが存在します。 このセッションは、パフォーマンスの問題をトラブルシューティングするのに役立つシステム データを収集します。 詳細については、「[system_health セッションの使用](../../relational-databases/extended-events/use-the-system-health-session.md)」を参照してください。  
  
## DDL ステートメント  
 拡張イベント セッションを作成、変更、および削除するには、次の DDL ステートメントを使用します。  
  
|名前|説明|  
|----------|-----------------|  
|[CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)|イベントのソース、イベント セッション ターゲット、およびイベント セッション パラメーターを識別する拡張イベント セッション オブジェクトを作成します。|  
|[ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)|イベント セッションの開始および停止、またはイベント セッションの構成変更を行います。|  
|[DROP EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-event-session-transact-sql.md)|イベント セッションを削除します。|  
  
## カタログ ビュー  
 イベント セッションの作成時に作成されたメタデータを取得するには、次のカタログ ビューを使用します。  
  
|名前|説明|  
|----------|-----------------|  
|[sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)|すべてのイベント セッションの定義を一覧表示します。|  
|[sys.server_event_session_actions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-actions-transact-sql.md)|イベント セッションの各イベントのアクションごとに 1 行のデータを返します。|  
|[sys.server_event_session_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-events-transact-sql.md)|イベント セッションのイベントごとに 1 行のデータを返します。|  
|[sys.server_event_session_fields &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-fields-transact-sql.md)|イベントおよびターゲットに明示的に設定されたカスタマイズ可能な列ごとに 1 行のデータを返します。|  
|[sys.server_event_session_targets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-targets-transact-sql.md)|イベント セッションのイベント ターゲットごとに 1 行のデータを返します。|  
  
## 動的管理ビュー  
 セッション メタデータおよびセッション データを取得するには、次の動的管理ビューを使用します。 メタデータはカタログ ビューから取得され、セッション データはイベント セッションの開始時と実行時に作成されます。  
  
> [!NOTE]  
>  これらのビューには、セッションが開始されるまでセッション データは格納されません。  
  
|名前|説明|  
|----------|-----------------|  
|[sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql.md)|セッション ディスパッチャー プールに関する情報を返します。|  
|[sys.dm_xe_objects &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)|イベント パッケージによって公開されるオブジェクトごとに 1 行のデータを返します。|  
|[sys.dm_xe_object_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)|すべてのオブジェクトのスキーマ情報を返します。|  
|[sys.dm_xe_packages &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql.md)|拡張イベント エンジンに登録されているすべてのパッケージを一覧表示します。|  
|[sys.dm_xe_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql.md)|アクティブな拡張イベント セッションに関する情報を返します。|  
|[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql.md)|セッション ターゲットに関する情報を返します。|  
|[sys.dm_xe_session_events &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-events-transact-sql.md)|セッション イベントに関する情報を返します。|  
|[sys.dm_xe_session_event_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-event-actions-transact-sql.md)|イベント セッション アクションに関する情報を返します。|  
|[sys.dm_xe_map_values &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-map-values-transact-sql.md)|内部数値キーをユーザーが判読できるテキストにマッピングします。|  
|[sys.dm_xe_session_object_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-object-columns-transact-sql.md)|セッションにバインドされたオブジェクトの構成値を示します。|  
  
## システム テーブル  
 次のシステム テーブルを使用して、SQL トレース イベントのクラスおよび列と等価な拡張イベントの情報を取得します。  
  
|名前|説明|  
|----------|-----------------|  
|[trace_xe_event_map &#40;Transact-SQL&#41;](../Topic/trace_xe_event_map%20\(Transact-SQL\).md)|SQL トレース イベント クラスに割り当てられている拡張イベントのイベントごとに 1 行のデータを格納します。|  
|[trace_xe_action_map &#40;Transact-SQL&#41;](../Topic/trace_xe_action_map%20\(Transact-SQL\).md)|SQL トレース列 ID に割り当てられている拡張イベントのアクションごとに 1 行のデータを格納します。|  
  
## 参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](../Topic/Dynamic%20Management%20Views%20and%20Functions%20\(Transact-SQL\).md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server 拡張イベント テーブル &#40;Transact-SQL&#41;](../Topic/SQL%20Server%20Extended%20Events%20Tables%20\(Transact-SQL\).md)   
 [system_health セッションの使用](../../relational-databases/extended-events/use-the-system-health-session.md)   
 [拡張イベントへの PowerShell プロバイダーの使用](../../relational-databases/extended-events/use-the-powershell-provider-for-extended-events.md)  
  
  