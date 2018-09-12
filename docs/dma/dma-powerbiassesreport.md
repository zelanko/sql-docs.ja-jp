---
title: Data Migration Assistant 評価レポートを Power BI (SQL Server) の統合の分析 |Microsoft Docs
description: Power BI を使用して、インポートして、SQL Server に統合したデータ移行の評価レポートを分析する方法について説明します
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: fd265f1cf67d421ca7a21987b2d48c3f929f5873
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "43152623"
---
# <a name="analyze-consolidated-assessment-reports-created-by-data-migration-assistant-with-power-bi"></a>Data Migration Assistant を Power BI で作成された統合評価レポートを分析します。

この記事では、統合された移行評価を分析する Power BI レポートを作成する方法について説明します。

Data Migration Assistant によって作成された移行評価を統合する方法の詳細については、次を参照してください。[評価レポートの統合](../dma/dma-consolidatereports.md)します。

## <a name="sample-power-bi-reports"></a>Power BI のサンプル レポート

これから統合移行評価のための Power BI レポートの例をダウンロードする[Github リポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant)します。

次のレポートが含まれます。 

- [ダッシュ ボード](#dashboard--details)

  スナップショットの統計情報とドリル ダウン レポートが含まれています。

- [オンプレミスでアップグレードの準備完了](#on-premises-upgrade-readiness--details)

  データ ソースは UpgradeSuccessRanking 表示 DMAReporting データベースです。  このレポートは、評価した、データベースの割合のアップグレードの成功を示します。

- [オンプレミスで機能パリティ](#on-premise-feature-parity--details)

  ターゲット SQL Server のバージョンの機能の推奨事項を示しています。

- [Azure SQL DB アップグレードの準備完了](#azure-sql-db-upgrade-readiness--details)

  データ ソースは UpgradeSuccessRanking 表示 DMAReporting データベースです。  このレポートは、データベースを Azure SQL DB の移行の評価の割合のアップグレードの成功を示します。

- [Azure SQL DB がサポートされていない機能](#azure-sql-db-unsupported-features--details)

  Azure SQL DB (V12) でサポートされていない、既存のデータベース機能を示します。

これらのレポートを Power BI でデータ ソースを変更することで、環境で作業を変更することができます。 

1. 横の下矢印をオン**クエリを編集**、選択および**データ ソース設定**します。

   ![クエリ メニューの データ ソースの設定を編集します。](../dma/media/DataSourceSettings.png)

1. 選択**ソースを変更しています.** サーバーとデータベースの値を入力します。

   ![ソースの変更、サーバーおよびデータベース](../dma/media/ChangeSource.png)

1. 選択**OK**、し、**閉じる**します。

1. レポートを更新します。

   ![Power BI レポートを更新します。](../dma/media/RefreshReport.png)

### <a name="dashboard-report"></a>ダッシュ ボードのレポート

![ダッシュ ボードのレポート](../dma/media/DashboardReport.png)

ダッシュ ボードには、すべての評価を詳細が示されます。 左側にある、スライサーを使用して、インスタンスまたはデータベースでフィルター処理することができます。 横棒グラフを使用するには、問題の箇所を表示する特定のカテゴリにドリル ダウンします。

ドリルダウンすると、横棒グラフの右上隅にある下向きの矢印の付いた円を選択します。

![カテゴリのドリルダウン](../dma/media/CategoryDrillDown.png)

次の図のようにドリル ダウン シーケンスが設定されている (**軸**)。 シーケンスを変更するには、目的の順序に列をドラッグします。

![横棒グラフの軸の視覚化](../dma/media/VisualizationsAxis.png)

このビューは、最初に、特定のデータベースでフィルター処理し、特定のカテゴリの問題をドリルダウンするより強力なになります。 次の例では、HR データベースがインスタンスの選択**SQL01** (重大な変更) の移行を妨げているすべてのオブジェクトを表示します。

![HR データベースの重大な変更](../dma/media/BreakingChanges.png)

### <a name="on-premises-upgrade-readiness-report"></a>オンプレミスで準備レポートをアップグレードします。

![オンプレミスで準備レポートをアップグレードします。](../dma/media/OnPremisesUpgradeReadinessReport.png)

このレポートには、以降のバージョンの SQL Server への移行には、データベースが準備できているかのスナップショットが表示されます。 このレポートのデータは dbo です。UpgradeSuccessFactor\_DMAReporting のデータベース内のオンプレミスのビュー。

インスタンスとデータベースの名前でフィルター処理し、上部にあるスコア カードを使用して、確認できるバージョンすぎる、データベースを移行する可能性があります。 たとえば、AdventureWorks 2012 データベースをフィルター処理する場合に、データベースがレポートに表示されているすべての SQL Server バージョンに移動する準備が参照してください。 これは、そのデータベースとの互換性レベルの重大な変更がないようにすることで決定されます。

![AdventureWorks データベースのアップグレードの成功率](../dma/media/UpgradeSuccessFactor.png)

### <a name="on-premises-feature-parity-report"></a>オンプレミスで機能パリティ レポート

![オンプレミスで機能パリティ レポート](../dma/media/OnPremisesFeatureParityReport.png)

このレポートを使用すると、ターゲット SQL Server のバージョンでデータベースを使用できる新しい機能を強調表示します。

下部にあるデータでは、じょうごグラフで、機能を選択すると、オブジェクトが、機能によって影響を受ける強調表示されます。 次の例では、**記憶域の節約に Stretch database を**機能が選択されているし、テーブルが表示されているこの機能を活用できます。

![Stretch Database の機能の推奨事項](../dma/media/FeatureRecommend_StretchDatabase.png)

### <a name="azure-sql-db-upgrade-readiness-report"></a>Azure SQL DB のアップグレードの準備完了レポート

![Azure SQL DB のアップグレードの準備完了レポート](../dma/media/AzureSQLDBUpgradeReadinessReport.png)

このレポートには、Azure SQL Database V12 に移行するデータベースの準備状態が表示されます。 このレポートからのデータは dbo です。DMAReporting データベース UpgradeSuccessRanking ビュー。

### <a name="azure-features-parity-report"></a>Azure の機能パリティ レポート

![Azure の機能パリティ レポート](../dma/media/AzureFeaturesParityReport.png)

このレポートを使用して、強調表示、*インスタンス レベルの機能*Azure SQL Database V12 ではサポートされていません。

じょうごグラフで、機能を選択すると、下部にあるデータには、インスタンスとサポートされていないデータベース機能が一覧表示します。 次の例では、この機能が選択されている: **Azure SQL Database で Always on 可用性グループの構成はサポートされていません**します。  

![Alwayson の可用性グループ機能](../dma/media/Feature_AlwaysOnAvailability.png)

 
### <a name="azure-sql-db-unsupported-features-report"></a>Azure SQL DB には、機能のレポートがサポートされていません

![Azure SQL DB には、機能のレポートがサポートされていません](../dma/media/AzureSQLDBUnsupportedFeaturesReport.png)

このレポートの機能はサポートされていませんが強調表示を指定した**データベース**ターゲットが Azure SQL Database (V12) の場合。

じょうごグラフでデータベースの名前と機能の値によってフィルター処理でサポートされていない機能の詳細を確認できます。 詳細についてには、どのオブジェクトが影響を受けると、問題に対処するための推奨事項が含まれます。

DTC データベースでフィルター処理など、**読み取り専用データベースをアップグレードできません**、影響を受けるオブジェクトの一覧を確認できます。

![読み取り専用データベースにすることはできませんアップグレードの問題](../dma/media/ReadOnlyDatabases.png)

## <a name="see-also"></a>関連項目

[Data Migration Assistant の概要](../dma/dma-overview.md)

[Data Migration Assistant のダウンロード](https://www.microsoft.com/download/details.aspx?id=53595)

[Power BI のダウンロード](https://powerbi.microsoft.com/)
