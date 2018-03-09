---
title: "クエリ ストアを使用するときの推奨事項 | Microsoft Docs"
ms.custom: 
ms.date: 11/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Store, best practices
ms.assetid: 5b13b5ac-1e4c-45e7-bda7-ebebe2784551
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7e41e78e7e4ffc1699a79bee2e7ed6236210e52d
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="best-practice-with-the-query-store"></a>クエリ ストアを使用するときの推奨事項
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  このトピックでは、ワークロードでクエリ ストアを使用する際の推奨事項について説明します。  
  
##  <a name="SSMS"></a> 最新の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用する  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、クエリ ストアを構成するためのユーザー インターフェイスと、ワークロードについて収集されたデータを使用するためのユーザー インターフェイスが用意されています。  
最新バージョンの [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] は[ここ](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)からダウンロードしてください。  
  
 [クエリ ストアに関する @Azure ブログ](https://azure.microsoft.com/en-us/blog/query-store-a-flight-data-recorder-for-your-database/)の記事で、トラブルシューティングのシナリオでクエリ ストアを使用する方法について簡単に説明しています。  
  
##  <a name="Insight"></a> UseAzure SQL Database で Query Performance Insight を使用する  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] でクエリ ストアを実行する場合、 **Query Performance Insight** を使用して、時間の経過に応じた DTU 消費量を分析できます。  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用してすべてのクエリの詳細なリソースの消費量を取得することもできますが (CPU、メモリ、IO など)、Query Performance Insight を使用すると、迅速かつ効率的な方法で、データベースの全体的な DTU 消費量に与える影響を判断できます。  
詳細については、「 [Azure SQL Database Query Performance Insight](https://azure.microsoft.com/documentation/articles/sql-database-query-performance/)」を参照してください。    

##  <a name="using-query-store-with-elastic-pool-databases"></a>エラスティック プール データベースでクエリ ストアを使用する
クエリ ストアは、すべてのデータベースで (高密度でパックされたプールであっても) 問題なく使用できます。 エラスティック プール内の多数のデータベースに対してクエリ ストアを有効にすると発生する可能性があった、リソースの過剰使用に関連するすべての問題は解決されました。

##  <a name="Configure"></a> ワークロードに合わせてクエリ ストアを調整する  
 ワークロードとパフォーマンスのトラブルシューティングの要件に基づいて、クエリ ストアを構成します。   
最初は既定のパラメーターを使用してもよいですが、時間の経過と共にクエリ ストアの動作がどのように変化するかを監視して、必要に応じて構成を調整する必要があります。  
  
 ![クエリ ストア プロパティ](../../relational-databases/performance/media/query-store-properties.png "query-store-properties")  
  
 次に、パラメーター値を設定する際のガイドラインを示します。  
  
 **最大サイズ (MB):** クエリ ストアが使用するデータベース内のデータ領域の制限を指定します。  これは、クエリ ストアの操作モードに直接影響する最も重要な設定です。  
  
 クエリ ストアがクエリや実行プラン、統計情報を収集する間、データベース内でクエリ ストアのサイズが増え続けます。 サイズが制限に達すると、クエリ ストアの操作モードが自動的に読み取り専用に切り替わり、新しいデータの収集が停止します。以降、パフォーマンス分析は正確ではなくなります。  
  
 既定値は 100 MB ですが、ワークロードが多数のクエリとプランを生成する場合や、クエリ履歴を長期間保持する必要がある場合は、より大きなサイズが必要になる可能性があります。 クエリ ストアが読み取り専用モードに移行しないよう、現在の使用量を追跡して最大サイズ (MB) を増やしてください。  クエリ ストアのサイズに関する最新の情報を取得するには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用するか、次のスクリプトを実行します。  
  
```sql 
USE [QueryStoreDB];  
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason  
FROM sys.database_query_store_options;  
```  
  
 次のスクリプトは、新しい最大サイズ (MB) を設定します。  
  
```sql  
ALTER DATABASE [QueryStoreDB]  
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = 1024);  
```  
  
 **統計情報の収集間隔:** 実行時統計情報を収集する間隔を定義します (既定値は 1 時間)。 この間隔を短くして、問題を検出して軽減するまでの時間を短縮したい場合は、値を小さくすることを検討してください。ただし、クエリ ストアのデータのサイズに直接影響があるので注意が必要です。 統計情報の収集間隔に別の値を設定するには、SSMS または TRANSACT-SQL を使用します。  
  
```sql  
ALTER DATABASE [QueryStoreDB] SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 60);  
```  
  
 **古いクエリのしきい値 (日):** 保存する実行時統計と非アクティブ クエリの保有期間を制御する、時間ベースのクリーンアップ ポリシーです。  
既定では、クエリ ストアはデータを 30 日間保持するよう構成されていますが、シナリオによっては必要以上に長すぎることもあります。  
  
 使用予定のない履歴データは保持しないようにしてください。 そうすることで、クエリ ストアが読み取り専用モードになる可能性を減らせます。 また、クエリ ストアのデータのサイズと、問題を検出して軽減するまでの時間を予測しやすくなります。 時間ベースのクリーンアップ ポリシーを構成するには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] または次のスクリプトを使用します。  
  
```sql  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 90));  
```  
  
 **サイズ ベースのクリーンアップ モード:** クエリ ストアのデータ サイズが制限に達したときに、データの自動クリーンアップを行うかどうかを指定します。  
  
 クエリ ストアが常に読み取り/書き込みモードで実行して最新のデータを収集するよう、サイズ ベースのクリーンアップを有効にすることを強くお勧めします。  
  
```sql  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (SIZE_BASED_CLEANUP_MODE = AUTO);  
```  
  
 **クエリ ストアのキャプチャ モード:** クエリ ストアのクエリ キャプチャ ポリシーを指定します。  
  
-   **All** – すべてのクエリをキャプチャします。 既定のオプションです。  
  
-   **Auto** – 頻度の低いクエリと、コンパイルと実行時間の短いクエリは無視されます。 実行回数、コンパイル、実行時間のしきい値は内部的に決定されます。  
  
-   **None** – クエリ ストアが新しいクエリのキャプチャを停止します。  
  
 次のスクリプトは、クエリ キャプチャ モードを Auto に設定します。  
  
```sql  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (QUERY_CAPTURE_MODE = AUTO);  
```  
  
## <a name="how-to-start-with-query-performance-troubleshooting"></a>クエリ パフォーマンスのトラブルシューティングを開始する方法  
 次の図に示すように、クエリ ストアでのトラブルシューティングのワークフローはシンプルです。  
  
 ![クエリ ストアのトラブルシューティング](../../relational-databases/performance/media/query-store-troubleshooting.png "query-store-troubleshooting")  
  
 前のセクションで説明したように、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用してクエリ ストアを有効にするか、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。  
  
```sql  
ALTER DATABASE [DatabaseOne] SET QUERY_STORE = ON;  
```  
  
 クエリ ストアがワークロードを正確に表すデータ セットを収集するまでに、しばらく時間がかかります。 通常は、非常に複雑なワークロードの場合でも 1 日で十分です。 ただし、機能を有効にした後すぐにデータの探索を開始して、注意が必要なクエリを特定することもできます。   
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のオブジェクト エクスプローラーでデータベース ノードの下にある Query Store サブ フォルダーに移動し、特定のシナリオのトラブルシューティングのビューを開きます。   
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のクエリ ストア ビューの操作には、一連の実行メトリックを使用します。メトリックはそれぞれ、次のいずれかの統計関数で表されます。  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョン|実行メトリック|統計関数|  
|----------------------|----------------------|------------------------|  
|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|CPU 時間、実行時間、実行回数、論理読み取り、論理書き込み、メモリ消費量、物理読み取り、CLR 時間、並列処理の次数 (DOP)、行数|Average、Maximum、Minimum、Standard Deviation、Total|
|[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]|CPU 時間、実行時間、実行回数、論理読み取り、論理書き込み、メモリ消費量、物理読み取り、CLR 時間、並列処理の次数 (DOP)、行数、ログ メモリ、TempDB メモリ、待機時間|Average、Maximum、Minimum、Standard Deviation、Total|
  
 次の図は、クエリ ストアのビューの場所を示しています。  
  
 ![クエリ ストア ビュー](../../relational-databases/performance/media/query-store-views.png "query-store-views")  
  
 次の表では、各クエリ ストア ビューの用途を説明します。  
  
|SSMS ビュー|シナリオ|  
|---------------|--------------|  
|機能低下したクエリ|実行メトリックが最近低下した (悪化した) クエリを特定します。 <br />このビューを使用して、アプリケーションで確認されたパフォーマンスの問題と、実際に修正や改善の必要があるクエリを関連付けます。|  
|全体的なリソース消費量|実行メトリックのいずれかについて、データベースの全体的なリソース消費量を分析します。<br />このビューを使用して、リソースのパターン (日中または夜間のワークロード) を特定し、データベースの全体的な消費量を最適化します。|  
|最もリソースを消費するクエリ|対象となる実行メトリックを選択し、対象期間内で最も極端な値を持つクエリを特定します。 <br />このビューを使用して、データベースのリソース消費量に最も大きな影響を与えているクエリに焦点を絞ります。|  
|強制適用されたプランのあるクエリ|クエリ ストアを使って以前に強制適用されたプランを一覧表示します。 <br />このビューを使って、現在強制適用されているすべてのプランに簡単にアクセスします。|  
|高バリエーションのクエリ|目的の期間内の継続時間、CPU 時間、IO、メモリ使用率など、使用可能なディメンションのいずれかに関連して実行バリエーションが高いクエリを分析します。<br />このビューを使用して、アプリケーション全体のユーザー エクスペリエンスに影響を及ぼす可能性のある、パフォーマンスの差異が大きいクエリを特定します。|  
|追跡対象のクエリ|最も重要なクエリの実行をリアルタイムで追跡します。 このビューは通常、強制適用されたプランを持つクエリがあり、クエリのパフォーマンスを安定させる必要がある場合に使用します。|
  
> [!TIP]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して最もリソースを消費するクエリを特定し、プラン変更により機能低下したクエリを修正する方法の詳細については、[クエリ ストアに関する @Azure ブログの記事](https://azure.microsoft.com/blog/query-store-a-flight-data-recorder-for-your-database/)を参照してください。  
  
 パフォーマンスが低下したクエリを特定する際に必要なアクションは、問題の性質によって異なります。  
  
-   クエリの実行プランが複数あり、最後のプランのパフォーマンスが前のプランよりも大幅に悪いような場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が今後は常に最適なプランを使用するよう、プランの強制適用メカニズムを使用することができます。  
  
     ![クエリ ストアのプランの強制](../../relational-databases/performance/media/query-store-force-plan.png "query-store-force-plan")  

> [!NOTE]  
> 上の図では特定のクエリ プランに異なる図形が使われている場合があり、考えられる各状態の意味を次に示します。<br />  
> |図形|意味|  
> |-------------------|-------------|
> |Circle|クエリ完了 (通常の実行が正常に終了しました)|
> |Square|キャンセル (クライアントが開始した実行中止)|
> |Triangle|失敗 (例外による実行中止)|
> また、図形のサイズは指定期間内でのクエリ実行回数を反映し、実行回数が多いほどサイズが大きくなります。  

-   クエリが最適に実行するために必要なインデックスが欠落している場合があります。 この情報は、クエリの実行プラン内で確認できます。 クエリ ストアを使用して欠落しているインデックスを作成し、クエリのパフォーマンスを確認します。  
  
     ![クエリ ストアのプラン表示](../../relational-databases/performance/media/query-store-show-plan.png "query-store-show-plan")  
  
     [!INCLUDE[ssSDS](../../includes/sssds-md.md)]でワークロードを実行している場合、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Index Advisor にサインアップすると、推奨されるインデックスを自動的に取得できます。  
  
-   実行プランの推定行数と実際の行数に大きな差がある場合は、統計情報を強制的に再コンパイルすることもできます。  
  
-   問題のあるクエリを書き直します。 たとえば、クエリのパラメーター化を利用したり、より最適なロジックを実装したりする場合などです。  
  
##  <a name="Verify"></a> クエリ ストアがクエリ データを収集していることを定期的に確認する  
 クエリ ストアの操作モードは、通知なしに変更されることがあります。 クエリ ストアの状態を定期的に監視して、クエリ ストアが問題なく動作していることを確認し、回避できたはずのエラーが発生しないようにしてください。 操作モードを確認して最も重要なパラメーターを表示するには、次のクエリを実行します。  
  
```sql
USE [QueryStoreDB];  
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason, interval_length_minutes,   
    stale_query_threshold_days, size_based_cleanup_mode_desc,   
    query_capture_mode_desc  
FROM sys.database_query_store_options;  
```  
  
 `actual_state_desc` と `desired_state_desc` が一致していない場合、それは操作モードが自動的に変更されていることを示します。 最も一般的な変更は、クエリ ストアが通知なしで読み取り専用モードに切り替わることです。 非常にまれなケースとしては、クエリ ストアが内部エラーにより最終的にエラー状態になることがあります。  
  
 実際の状態が読み取り専用になっている場合は、 **readonly_reason** 列で根本原因を調べます。 通常は、クエリ ストアがサイズの制限を超えたために読み取り専用モードに移行したことが原因です。 その場合、**readonly_reason** は 65536 に設定されています。 他の理由については、「[sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)」を参照してください。  
  
 クエリ ストアを読み取り/書き込みモードに戻してデータの収集を再開するには、次の手順を実行します。  
  
-   **ALTER DATABASE** の **MAX_STORAGE_SIZE_MB**オプションを使用して、ストレージの最大サイズを増やします。  
  
-   次のステートメントを使用して、クエリ ストアのデータをクリーンアップする。  
  
    ```sql  
    ALTER DATABASE [QueryStoreDB] SET QUERY_STORE CLEAR;  
    ```  
  
操作モードを明示的に読み取り/書き込みモードに戻す次のステートメントを実行することで、これらの手順のいずれか (または両方) を適用できます。  
  
```sql  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);  
```  
  
 操作モードが変更されないよう事前に対処するには、次の手順を実行します。  
  
-   推奨事項を取り入れることで、操作モードが通知なしに変更されることを防ぐことができます。 クエリ ストアのサイズが許可される最大値を常に下回っていれば、読み取り専用モードに変更される可能性が大幅に下がります。 [クエリ ストアの構成](#Configure) に関するセクションの説明に従ってサイズ ベースのポリシーを有効にし、クエリ ストアがサイズ制限に近づくと自動的にデータがクリーンアップされるようにします。  
  
-   最新のデータを確実に保持するには、時間ベースのポリシーを構成して古くなった情報を定期的に削除します。  
  
-   最後に、クエリ キャプチャ モードを Auto に設定することを検討してください。そうすれば、ワークロードにとって重要でないクエリを除外できます。  
  
### <a name="error-state"></a>エラー状態  
 クエリ ストアを復旧するには、明示的に読み取り/書き込みモードに設定し、実際の状態を再度確認します。  
  
```sql  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);    
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason, interval_length_minutes,   
    stale_query_threshold_days, size_based_cleanup_mode_desc,   
    query_capture_mode_desc  
FROM sys.database_query_store_options;  
```  
  
 それでも問題が解決しない場合、ディスクに破損したクエリ ストア データが存在しています。
 
 影響を受けたデータベース内で **sp_query_store_consistency_check** ストアド プロシージャを実行することで、クエリ ストアを復旧できる場合があります。
 
 復旧できない場合は、読み取り/書き込みモードを要求する前にクエリ ストアのクリアを試すことができます。  
  
```sql  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE CLEAR;  
GO  
  
ALTER DATABASE [QueryStoreDB]   
SET QUERY_STORE (OPERATION_MODE = READ_WRITE);    
GO  
  
SELECT actual_state_desc, desired_state_desc, current_storage_size_mb,   
    max_storage_size_mb, readonly_reason, interval_length_minutes,   
    stale_query_threshold_days, size_based_cleanup_mode_desc,   
    query_capture_mode_desc  
FROM sys.database_query_store_options;  
```  
  
## <a name="set-the-optimal-query-capture-mode"></a>最適なクエリ ャプチャ モードを設定する  
 最も重要なデータをクエリ ストアに保存します。 次の表では、各クエリ キャプチャ モードの一般的なシナリオについて説明します。  
  
|クエリ キャプチャ モード|シナリオ|  
|------------------------|--------------|  
|All|すべてのクエリの形式とその実行頻度やその他の統計情報の観点から、ワークロードを詳しく分析します。<br /><br /> ワークロードの新しいクエリを特定します。<br /><br /> ユーザーまたは自動パラメーター化の機会を識別するためにアドホック クエリが使用されているかどうかを検出します。|  
|Auto|定期的に実行されるクエリや大量にリソースを消費するクエリなど、対応が必要な重要なクエリに焦点を絞ります。|  
|None|実行時に監視する必要があるクエリ セットを既にキャプチャしており、他のクエリによる影響を受けたくない場合に使用します。<br /><br /> このモードは、テストやベンチマークの環境に適しています。<br /><br /> このモードは、アプリケーションのワークロードを監視するよう構成したクエリ ストアの構成を販売するソフトウェア ベンダーにも適しています。<br /><br /> 重要な新しいクエリを追跡して最適化する機会を見逃す可能性があるので、このモードを使用する際は注意してください。 シナリオで必要な特別な場合を除き、このモードは使用しないでください。|  
  
## <a name="keep-the-most-relevant-data-in-query-store"></a>最も重要なデータをクエリ ストアに保存する  
 重要なデータのみを格納するようクエリ ストアを構成すると、通常のワークロードへの影響も最小限に抑えながら、効果的にトラブルシューティングを行えます。  
次の表に、推奨事項を示します。  
  
|推奨事項|設定|  
|-------------------|-------------|  
|保存する履歴データに制限を設ける。|時間ベースのポリシーを構成して自動クリーンアップを有効にします。|  
|重要でないクエリを除外する。|クエリ キャプチャ モードを Auto に設定します。|  
|最大サイズに達したときに、重要でないクエリを削除する。|サイズ ベースのクリーンアップ ポリシーを有効にします。|  
  
##  <a name="Parameterize"></a> パラメーター化されていないクエリを使用しない  
 アドホック分析など必ずしも必要でない場面でパラメーター化されていないクエリを使用することはお勧めしません。  キャッシュされたプランは再利用できません。再利用すると、クエリ オプティマイザーによって一意のクエリ テキストごとにクエリが強制的にコンパイルされます。 このトピックの詳細については、「[強制パラメータ化使用のガイドライン](../../relational-databases/query-processing-architecture-guide.md#ForcedParamGuide)」を参照してください。  
  また、クエリ テキストの数が増えると類似する実行プランの数も増えるため、クエリ ストアのサイズがすぐに制限を超えてしまう可能性があります。  
その結果、ワークロードのパフォーマンスが最適化されず、クエリ ストアが読み取り専用モードに切り替わったり、後続のクエリに対応するためにデータが常に削除されるようになったりする可能性があります。  
  
 次のオプションを検討してください。  

  -   可能であればクエリをパラメーター化します (例: sp_executesql などのストアド プロシージャ内にクエリをラップする)。 このトピックの詳細については、「[パラメーターと実行プランの再利用](../../relational-databases/query-processing-architecture-guide.md#PlanReuse)」を参照してください。    
  
-   ワークロードに 1 回限りのアドホック バッチが多数含まれており、そこで異なるクエリ プランが使用されている場合は、[**[アドホック ワークロードの最適化]**](../../database-engine/configure-windows/optimize-for-ad-hoc-workloads-server-configuration-option.md) オプションを使用します。  
  
    -   個々の query_hash 値の数と、sys.query_store_query 内のエントリの総数を比較します。 この比率が 1 に近い場合、アドホック ワークロードは異なるクエリを生成します。  
  
-   異なるクエリ プランの数がそれほど多くない場合は、データベースまたはクエリのサブセットに対して[**強制パラメーター化**](../../relational-databases/query-processing-architecture-guide.md#ForcedParam)を適用します。  
  
    -   選択したクエリに対してのみパラメータ化を強制するには、[プラン ガイド](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)を使用します。  
  
    -   sys.query_store_query の個々の query_hash の数と、エントリの総数の比率が 1 を下回り、ワークロードに含まれる異なるクエリ プランが少ない場合は、[パラメーター化データベース オプション](../../relational-databases/databases/database-properties-options-page.md#miscellaneous)を使用して強制パラメーター化を構成します。  
  
-   リソース消費の少ないアドホック クエリを自動的に除外するには、 **クエリ キャプチャ モード** を AUTO に設定します。  
  
##  <a name="Drop"></a> クエリの親オブジェクトを保持する場合は DROP と CREATE のパターンを避ける  
 クエリ ストアは、クエリ エントリと親オブジェクト (ストアド プロシージャ、関数、トリガー) を関連付けます。  親オブジェクトを再作成すると、同じクエリ テキストに対して新しいクエリ エントリが生成されます。 これにより、クエリのパフォーマンス統計情報を継続して追跡できなくなるので、プランの強制適用メカニズムを使用することになります。 これを回避するには、可能な限り `ALTER <object>` プロセスを使用して親オブジェクトの定義を変更します。  
  
##  <a name="CheckForced"></a> 強制適用されたプランの状態を定期的に確認する  

 プランの強制適用は、重要なクエリのパフォーマンスを修正してより正確な予測を可能にするための便利なメカニズムです。 ただし、プラン ヒントやプラン ガイドと同様に、強制的に適用されたプランがその後の実行でも確実に使用されるとは限りません。 通常、実行プランによって参照されるオブジェクトが変更または削除されたことによってデータベース スキーマが変更された場合、プランを強制的に適用できなくます。 その場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はクエリの再コンパイルに戻りますが、強制適用が失敗した実際の理由は [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) に示されます。 次のクエリは、強制適用されたプランに関する情報を返します。  
  
```sql  
USE [QueryStoreDB];  
GO  
  
SELECT p.plan_id, p.query_id, q.object_id as containing_object_id,  
    force_failure_count, last_force_failure_reason_desc  
FROM sys.query_store_plan AS p  
JOIN sys.query_store_query AS q on p.query_id = q.query_id  
WHERE is_forced_plan = 1;  
```  
  
 理由の一覧については、「[sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)」を参照してください。 **query_store_plan_forcing_failed** XEvent を使用して、プラン強制の失敗のトラブルシューティングを追跡することもできます。  
  
##  <a name="Renaming"></a> 強制適用されたプランを持つクエリがある場合はデータベースの名前を変更しない  

 実行プランは、3 つの要素で構成される名前 (`database.schema.object`) を使用してオブジェクトを参照します。   

データベース名を変更すると、プランの強制適用が失敗し、その後のすべてのクエリ実行で再コンパイルが発生します。  

##  <a name="Recovery"></a> ミッション クリティカルなサーバーにトレース フラグを使用して、障害からの回復を向上させる
 
  高可用性とディザスター リカバリーのシナリオでクエリ ストアのパフォーマンスを向上させるには、グローバル トレース フラグ 7745 と 7752 を使用できます。 詳細については、「[Trace Flags](../..//t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」(トレース フラグ) を参照してください
  
  トレース フラグ 7745 では、SQL Server がシャットダウンされる前に、クエリ ストアによってディスクにデータを書き込む既定の動作が行われないようにします。
  
  トレース フラグ 7752 を使用すると、クエリ ストアの非同期読み込みが可能になります。また、クエリ ストアを完全に読み込む前に SQL Server でクエリを実行することができます。 クエリ ストアの既定の動作は、クエリ ストアが回復する前に、クエリが実行ないようにします。

## <a name="see-also"></a>参照  
 [クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [インメモリ OLTP でのクエリ ストアの使用](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)   
 [関連するビュー、関数、プロシージャ](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [クエリ処理アーキテクチャ ガイド](../../relational-databases/query-processing-architecture-guide.md)  
  
