---
title: "Power BI (SQL Server データ Migration Assistant) を使用して、統合の評価をレポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: 
ms.component: dma
ms.reviewer: 
ms.suite: sql
ms.technology: sql-dma
ms.tgt_pltfrm: 
ms.topic: article
keywords: 
helpviewer_keywords: Data Migration Assistant, Assess
ms.assetid: 
caps.latest.revision: 
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9bfe38d98ec1e34494b59d878cdf3a46987d6d1e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="report-on-your-consolidated-assessments-by-using-power-bi-data-migration-assistant"></a>Power BI (データ Migration Assistant) を使用して、統合の評価をレポートします。

この記事では、統合移行評価用の Power BI レポートを作成する方法について説明します。

データ Migration Assistant を使用して移行の評価を統合する方法の詳細については、次を参照してください。[評価レポートの統合](../dma/dma-consolidatereports.md)です。

## <a name="sample-power-bi-reports"></a>Power BI のサンプル レポート

統合移行評価用の Power BI レポートの例をダウンロードするにはこれから[Github リポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant)です。

レポートを次のとおりです。 

- [ダッシュ ボード](#dashboard--details)

  スナップショットの統計、およびドリル ダウン レポートが含まれます。

- [内部設置型のアップグレードの準備完了](#on-premises-upgrade-readiness--details)

  データ ソースは、DMAReporting データベースで UpgradeSuccessRanking ビューです。  このレポートは、評価、データベースの割合のアップグレードの成功を示します。

- [内部設置型の機能の類似性](#on-premise-feature-parity--details)

  ターゲット SQL Server のバージョンの機能の推奨事項を示します。

- [Azure SQL DB アップグレードの準備完了](#azure-sql-db-upgrade-readiness--details)

  データ ソースは、DMAReporting データベースで UpgradeSuccessRanking ビューです。  このレポートは、データベースの Azure SQL データベース移行の評価の割合のアップグレードの成功を示します。

- [Azure SQL DB がサポートされていない機能](#azure-sql-db-unsupported-features--details)

  Azure SQL DB (V12) でサポートされていない、既存のデータベースの機能を示します。

これらのレポートを Power BI でデータ ソースを変更することで、環境で作業を変更することができます。 

1. 下矢印を選択 の横に**クエリを編集**を選択して**データ ソース設定**です。

   ![クエリ] メニューの [データ ソースの設定を編集します。](../dma/media/DataSourceSettings.png)

1. 選択**ソースを変更しています.**サーバーとデータベースの値を入力します。

   ![ソースの変更、サーバーおよびデータベース](../dma/media/ChangeSource.png)

1. 選択**OK**、し、**閉じる**です。

1. レポートを更新します。

   ![Power BI レポートを更新します。](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>ダッシュ ボードのレポート

![ダッシュ ボードのレポート](../dma/media/DashboardReport.png)

詳細については、評価のすべてのダッシュ ボードに表示します。 左側のスライサーを使用すると、インスタンスまたはデータベースでフィルター処理します。 横棒グラフを使用すると、問題がある箇所を表示する特定のカテゴリにドリル ダウンします。

ドリル ダウンをするには、横棒グラフの右上隅にある下向きの矢印の付いた円を選択します。

![カテゴリのドリル ダウン](../dma/media/CategoryDrillDown.png)

次の図のように、ドリル ダウン シーケンスが設定されている (**軸**)。 シーケンスを変更するには、目的の順序に列をドラッグします。

![視覚エフェクトを横棒グラフ軸](../dma/media/VisualizationsAxis.png)

このビューは、まず特定のデータベースでフィルター処理し、特定のカテゴリの問題をドリルダウンするとより強力な手段になります。 次の例では、HR データベースが選択されているインスタンスの**SQL01** (重大な変更) の移行を妨げているすべてのオブジェクトを表示します。

![最新の HR データベースの変更](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>内部設置型のアップグレード準備レポート

![内部設置型のアップグレード準備レポート](../dma/media/OnPremisesUpgradeReadinessReport.png)

このレポートには、以降のバージョンの SQL Server に移行する準備がどのように、そのデータベースがのスナップショットが示されます。 このレポートのデータを dbo に由来します。UpgradeSuccessFactor\_と内部設置型データベース内のビュー DMAReporting です。

インスタンスとデータベース名でフィルター処理し、上部にあるスコアのカードを使用して参照しているバージョンは、データベースが移行すぎます。 たとえば、AdventureWorks 2012 データベースでフィルター処理する場合に、データベースが、レポートに表示されたすべての SQL Server バージョンに移行する準備が参照してください。 これは、そのデータベースとの互換性レベルの互換性に影響する変更がないようにすることで決定されます。

![AdventureWorks データベースのアップグレードの成功率](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>内部設置型機能パリティ レポート

![内部設置型機能パリティ レポート](../dma/media/OnPremisesFeatureParityReport.png)

このレポートを使用すると、ターゲット SQL Server のバージョンでデータベースを使用できる新機能を強調表示します。

じょうごグラフで、機能を選択すると、どのオブジェクトが、機能によって影響を受ける下部にあるデータが強調表示されます。 次の例で、**記憶域を節約するための Stretch database**機能が選択されているし、テーブルが表示されているこの機能を活用できます。

![Stretch Database の機能の推奨事項](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Azure SQL DB のアップグレードの準備完了レポート

![Azure SQL DB のアップグレードの準備完了レポート](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

このレポートには、Azure SQL Database V12 に移行するデータベースの準備が表示されます。 このレポートからのデータ ソース、dbo します。DMAReporting データベース UpgradeSuccessRanking ビュー。

### <a name="azure-features-parity-report"></a>Azure の機能パリティ レポート

![Azure の機能パリティ レポート](../dma/media/AzureFeaturesParityReport.png)

このレポートを強調表示を使用して、*インスタンス レベルの機能*Azure SQL Database V12 ではサポートされていません。

じょうごグラフで、機能を選択すると、インスタンスとデータベースがサポートされない機能を下部にあるデータが一覧表示します。 次の例では、この機能が選択されている: **Always on 可用性グループの構成は Azure SQL データベースでサポートされていません**です。  

![常に可用性グループ機能](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Azure SQL DB には、機能のレポートがサポートされていません

![Azure SQL DB には、機能のレポートがサポートされていません](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

このレポートでは、どの機能はサポートされていませんが強調表示されます、特定**データベース**ターゲットが Azure SQL Database (V12) の場合。

じょうごグラフでデータベースの名前と機能の値によってフィルター処理でサポートされていない機能の詳細を表示できます。 詳細についてには、どのオブジェクトが影響を受けると、問題に対処するための推奨事項が含まれます。

たとえば、DTC データベースによるフィルター処理と**読み取り専用データベースをアップグレードすることはできません**、影響を受けるオブジェクトの一覧を表示することができます。

![読み取り専用データベースできないアップグレード問題](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>参照

[Migration Assistant のデータの概要](../dma/dma-overview.md)

[データ移行のアシスタントをダウンロード](https://www.microsoft.com/download/details.aspx?id=53595)

[Power BI のダウンロード](https://powerbi.microsoft.com/)
