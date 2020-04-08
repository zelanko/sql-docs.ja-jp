---
title: SQL Server 移行評価の実行
titleSuffix: Data Migration Assistant
description: 別の SQL Server または Azure SQL データベースに移行する前に、データ移行アシスタントを使用してオンプレミスの SQL Server を評価する方法を説明します。
ms.date: 01/15/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: 59dc8c96ebda5ac66fb6701d480cb6d633e83158
ms.sourcegitcommit: 48e259549f65f0433031ed6087dbd5d9c0a51398
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "80809748"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Data Migration Assistant を使用した SQL Server 移行評価の実行

次の手順は、データ移行アシスタントを使用して、オンプレミスの SQL Server、Azure VM で実行されている SQL Server、または Azure SQL データベースに移行するための最初の評価を実行する際に役立ちます。

   > [!NOTE]
   > データ移行アシスタント v5.0 では、データベース接続の分析と、アプリケーション コード内の組み込み SQL クエリのサポートが導入されています。 詳細については、ブログの記事「[データ移行アシスタントを使用してアプリケーションのデータ アクセス層を評価する](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Using-Data-Migration-Assistant-to-assess-an-application-s-data/ba-p/990430)」を参照してください。

## <a name="create-an-assessment"></a>評価を作成する

1. **[新規**](+)アイコンを選択し、**次に[評価**]プロジェクトタイプを選択します。

2. ソースとターゲットのサーバーの種類を設定します。

    オンプレミスの SQL Server インスタンスを最新のオンプレミスの SQL Server インスタンスにアップグレードする場合、または Azure VM でホストされている SQL Server にアップグレードする場合は、ソースとターゲット サーバーの種類を**SQL Server**に設定します。 Azure SQL データベースに移行する場合は、代わりにターゲット サーバーの種類を**Azure SQL データベース**に設定します。

3. **Create** をクリックしてください。

   ![評価を作成する](../dma/media/dma-assesssqlonprem/new-assessment.png)

## <a name="choose-assessment-options"></a>評価オプションの選択

1. 移行先の SQL Server のバージョンを選択します。

2. レポートの種類を選択します。

   オンプレミスの SQL Server または Azure VM ターゲットでホストされている SQL Server に移行するソース SQL Server インスタンスを評価する場合は、次の評価レポートの種類のいずれかまたは両方を選択できます。

    - **互換性の問題**
    - **新機能の推奨事項**

   ![SQL Server ターゲットの評価レポートの種類を選択します。](../dma/media/dma-assesssqlonprem/assessment-types.png)

   Azure SQL データベースに移行するソース SQL Server インスタンスを評価する際に、次の評価レポートの種類のいずれかまたは両方を選択できます。

    - **データベース互換性をチェックする**
    - **機能の類似性をチェックする**

    ![SQL データベース ターゲットの評価レポートの種類を選択します](../dma/media/dma-assesssqlonprem/assessment-types-azure.png)

## <a name="add-databases-and-extended-events-trace-to-assess"></a>データベースと拡張イベント トレースを追加して評価する

1. [**ソースの追加] を**選択して、接続ポップアップ メニューを開きます。

2. SQL Server インスタンス名を入力し、[認証の種類] を選択して、正しい接続プロパティを設定し、[**接続**] を選択します。

3. 評価するデータベースを選択し、[**追加**] を選択します。

    > [!NOTE]
    > 複数のデータベースを削除するには、Shift キーまたは Ctrl キーを押しながらデータベースを選択し、[**ソースの削除**] をクリックします。 [ソースの追加] を選択して、複数の SQL Server インスタンスからデータベースを**追加**することもできます。

4. アドホック SQL クエリまたは動的 SQL クエリ、またはアプリケーション データ 層を介して開始された DML ステートメントがある場合は、ソース SQL Server 上のワークロードをキャプチャするために収集したすべての拡張イベント セッション ファイルを配置したフォルダーへのパスを入力します。

     次の例は、アプリケーション データ層のワークロードをキャプチャするソース SQL Server で拡張イベント セッションを作成する方法を示しています。  ピークワークロードを表す期間のワークロードをキャプチャします。

    ```
    DROP EVENT SESSION [DatalayerSession] ON SERVER
    go
    CREATE EVENT SESSION [DatalayerSession] ON SERVER  
    ADD EVENT sqlserver.sql_batch_completed( 
        ACTION (sqlserver.sql_text,sqlserver.client_app_name,sqlserver.client_hostname,sqlserver.database_id))
    ADD TARGET package0.asynchronous_file_target(SET filename=N'C:\temp\Demos\DataLayerAppassess\DatalayerSession.xel')  
    WITH (MAX_MEMORY=2048 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=3 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=OFF)
    go
    ---Start the session
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = START;
    ---Wait for few minutes
    
    ---Query events
        
        SELECT 
        object_name,
        CAST(event_data as xml) as event_data,
        file_name, 
        file_offset
    FROM sys.fn_xe_file_target_read_file('C:\temp\Demos\DataLayerAppassess\DatalayerSession*xel', 
                'C:\\temp\\Demos\\DataLayerAppassess\\DatalayerSession*xem', 
                null,
                null)
    ---Stop the session after capturing the peak load.
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = STOP;
        
        go
    ```

5. **[次へ]** をクリックして評価を開始します。

    ![ソースの追加と評価の開始](../dma/media/dma-assesssqlonprem/select-database1.png)

> [!NOTE]
> 複数の評価を同時に実行し、**[All Assessments]\(すべての評価\)** ページを開いて評価の状態を表示できます。

## <a name="view-results"></a>結果の表示

評価の期間は、追加されるデータベースの数と各データベースのスキーマ サイズによって異なります。 結果は、データベースが使用可能になるとすぐに各データベースに表示されます。

1. 評価を完了したデータベースを選択し、スイッチャーを使用して**互換性の問題**と**機能の推奨事項**を切り替えます。

2. **[オプション]** ページで選択した対象の SQL Server バージョンでサポートされているすべての互換性レベルの互換性の問題を確認します。

互換性の問題を確認するには、影響を受けるオブジェクトとその詳細を分析し、変更**の切り込み**、動作の**変更**、**および非推奨の機能**で特定されたすべての問題に対する修正を行う可能性があります。

![評価結果の表示](../dma/media/dma-assesssqlonprem/review-results.png)

同様に、**パフォーマンス**、**ストレージ**、**およびセキュリティ**の各領域で機能の推奨事項を確認できます。

機能の推奨事項では、インメモリ OLTP、列ストア、ストレッチ データベース、常時暗号化、動的データ マスク、透過的なデータ暗号化などのさまざまな機能について説明します。

![機能の推奨事項を表示する](../dma/media/dma-assesssqlonprem/feature-recommendations.png)

Azure SQL Database の場合、評価では移行のブロックの問題と機能のパリティの問題が提供されます。特定のオプションを選択して、両方のカテゴリの結果を確認します。

- **SQL Server 機能のパリティ**カテゴリには、包括的な推奨事項、Azure で利用可能な代替アプローチ、および手順の緩和が用意されています。 移行プロジェクトでこの作業を計画する際に役立ちます。

  ![SQL Server 機能のパリティに関する情報を表示する](../dma/media/dma-assesssqlonprem/sql-feature-parity.png)

- **互換性の問題**カテゴリには、オンプレミスの SQL Server データベースを Azure SQL データベースに移行することをブロックする部分的にサポートされている機能またはサポートされていない機能が用意されています。次に、これらの問題に対処するための推奨事項を示します。

  ![互換性の問題を表示する](../dma/media/dma-assesssqlonprem/compatibility-issues.png)

## <a name="assess-a-data-estate-for-target-readiness"></a>データ・エステートのターゲット準備状況の評価

これらの評価をさらにデータ の全体に拡張し、Azure SQL データベースへの移行に関する SQL Server インスタンスとデータベースの相対的な準備状況を見つける場合は、[Azure 移行**にアップロード**] を選択して、結果を Azure Migrate ハブにアップロードします。

これにより、Azure Migrate ハブ プロジェクトで統合された結果を表示できます。

ターゲット準備評価の詳細なステップバイステップガイダンスは[、こちらをご覧ください](https://docs.microsoft.com/sql/dma/dma-assess-sql-data-estate-to-sqldb?view=sql-server-2017)。

   ![結果を Azure 移行にアップロードする](../dma/media/dma-assesssqlonprem/upload-to-azure-migrate.png)

## <a name="export-results"></a>結果のエクスポート

すべてのデータベースが評価を完了したら、[**レポートのエクスポート]** を選択して結果を JSON ファイルまたは CSV ファイルにエクスポートします。 その後、自分の都合でデータを分析できます。

## <a name="save-and-load-assessments"></a>評価の保存と読み込み

評価の結果をエクスポートするだけでなく、評価の詳細をファイルに保存し、評価ファイルをロードして後でレビューすることもできます。  詳細については、「[データ移行アシスタントを使用した評価の保存と読み込み](../dma/dma-save-load-assessments.md)」を参照してください。
