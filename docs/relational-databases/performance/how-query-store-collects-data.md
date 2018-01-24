---
title: "クエリ ストアがデータを収集するしくみ | Microsoft Docs"
ms.custom: 
ms.date: 09/13/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Query Store, data collection
ms.assetid: 8d5eec36-0013-480a-9c11-183e162e4c8e
caps.latest.revision: "10"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50e8f4fdae89572403ec8e5b7a5575b6ea61b132
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="how-query-store-collects-data"></a>クエリ ストアがデータを収集するしくみ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  クエリ ストアは継続的に **フライト データ レコーダー** の役割を果たし、クエリおよびプランに関連するコンパイルおよびランタイムの情報を収集します。 クエリ関連のデータは内部テーブルに保存され、一連のビューでユーザーに表示されます。  
  
## <a name="views"></a>ビュー  
 次の図は、クエリ ストアのビューとその論理関係を示しています。コンパイル時間の情報は青のエンティティで表しています。  
  
 ![query-store-process-2views](../../relational-databases/performance/media/query-store-process-2views.png "query-store-process-2views")  
  
 **ビューの説明**  
  
|表示|Description|  
|----------|-----------------|  
|**sys.query_store_query_text**|データベースに対して実行された一意のクエリ テキストを表示します。 クエリ テキストの前後のコメントとスペースは無視されます。 テキスト内のコメントとスペースは無視されません。 バッチ内のすべてのステートメントが、個別のクエリ テキスト エントリを生成します。|  
|**sys.query_context_settings**|クエリが実行される設定に影響するプランの一意の組み合わせを表示します。 `context_settings_id` はクエリ キーの一部であるため、設定に影響する異なるプランで実行された同じクエリ テキストが、クエリ ストアでは個別のクエリ エントリを生成します。|  
|**sys.query_store_query**|クエリ ストアで個別に追跡され、強制されるクエリ エントリです。 1 つのクエリ テキストが異なるコンテキスト設定で実行される場合、または異なる [!INCLUDE[tsql](../../includes/tsql-md.md)] モジュール (ストアド プロシージャ、トリガーなど) の外側と内側で実行される場合は、複数のクエリ エントリが生成される場合があります。|  
|**sys.query_store_plan**|コンパイル時間の統計を含むクエリの見積もりプランを表示します。 保存されたプランは `SET SHOWPLAN_XML ON`で得られるものと同じです。|  
|**sys.query_store_runtime_stats_interval**|クエリ ストアは、自動的に生成される時間枠 (間隔) ごとに時間を分割し、すべての実行済みプランにその間隔で集計された統計を格納します。 間隔のサイズは、([!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の) 構成オプションの統計収集間隔、または [ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) を使用する `INTERVAL_LENGTH_MINUTES` によって制御されます。|  
|**sys.query_store_runtime_stats**|実行済みプランで集計されたランタイム統計です。 キャプチャされたすべてのメトリックが平均、最小、最大、標準偏差の 4 つの統計関数の形式で表されます。|  
  
 クエリ ストアのビューの詳細は、「 **クエリのストアを使用した、パフォーマンスの監視** 」の「 [関連するビュー、関数、プロシージャ](monitoring-performance-by-using-the-query-store.md)」のセクションを参照してください。  
  
## <a name="query-processing"></a>クエリ処理  
 クエリ ストアは次の重要な点についてクエリ処理のパイプラインと対話します。  
  
1.  クエリを初めてコンパイルすると、クエリ テキストと初期プランがクエリ ストアに送信されます。  
  
2.  クエリを再コンパイルすると、プランがクエリ ストアで更新されます。 新しいプランを作成すると、クエリ ストアがクエリに新しいプラン エントリを追加します。前のプランはその実行統計とともに保持されます。  
  
3.  クエリを実行すると、ランタイム統計がクエリ ストアに送信されます。 クエリ ストアは、現在アクティブになっている間隔内で実行されたすべてのプランに対して正確な集計統計を保持します。  
  
4.  コンパイルおよび再コンパイルの確認フェーズで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は現在実行中のクエリに適用するプランがクエリ ストアにあるかどうかを決定します。 強制プランがあり、プロシージャ キャッシュのプランが強制プランと異なる場合は、実質的には PLAN ヒントがそのクエリに適用されたかのように、クエリが再コンパイルされます。 この処理は、ユーザーのアプリケーションに透過的に行われます。  
  
 次の図は上記で説明した統合のポイントを示しています。  
  
 ![query-store-process-2processor](../../relational-databases/performance/media/query-store-process-2processor.png "query-store-process-2processor")  
  
 I/O のオーバーヘッドを最小限に抑えるため、新しいデータはメモリ内にキャプチャされます。 書き込み操作はキューに登録され、その後、ディスクにフラッシュされます。 クエリとプランの情報 (下図のプラン ストア) は最小の待機時間でフラッシュされます。 `DATA_FLUSH_INTERVAL_SECONDS` ステートメントの `SET QUERY_STORE` オプションで定義された一定期間、ランタイム統計 (Runtime Stats) がメモリに保存されます。 [SSMS Query Store (SSMS クエリ ストア)] ダイアログ ボックスで **[データのフラッシュ間隔 (分)]** を入力できます。これは秒に変換されます。  
  
 ![query-store-process-3plan](../../relational-databases/performance/media/query-store-process-3.png "query-store-process-3plan")  
  
 システムのクラッシュが発生した場合、クエリ ストアでは `DATA_FLUSH_INTERVAL_SECONDS`で定義した時間までのランタイム データが失われる場合があります。 クエリのキャプチャ パフォーマンスとデータの可用性のバランスのためには、既定の 900 秒 (15 分) が最も適しています。  
メモリ不足が発生した場合、 `DATA_FLUSH_INTERVAL_SECONDS`で定義した時間より前に、ランタイム統計をディスクにフラッシュすることができます。  
クエリ ストアのデータ読み取り中は、メモリ内のデータとディスク上のデータが透過的に統合されます。
セッションの終了時またはクライアント アプリケーションの再起動/クラッシュ時、クエリ統計は記録されません。  
  
 ![query-store-process-4planinfo](../../relational-databases/performance/media/query-store-process-4planinfo.png "query-store-process-4planinfo")    

  
## <a name="see-also"></a>参照  
 [関連するビュー、関数、プロシージャ](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [クエリ ストアを使用する際の推奨事項](../../relational-databases/performance/best-practice-with-the-query-store.md)   
 [クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  
  
  
