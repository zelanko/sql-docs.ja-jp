---
title: (SQL Server データ Migration Assistant) 評価レポートの統合 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/16/2018
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
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 7192c055b4b9bfb6155f0963c598f9dc4a760c0a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32869647"
---
# <a name="consolidate-assessment-reports-data-migration-assistant"></a>(データ Migration Assistant) 評価レポートを統合します。

コマンドラインを使用して、データ Migration Assistant v2.1 で始まる無人モードでの移行の評価を実行することができます。 この機能では、大規模で、評価を実行することができます。 JSON または CSV ファイルの形式で評価の結果。

データ Migration Assistant のコマンド ライン ユーティリティの単一のインスタンス化で複数のデータベースを評価し、1 つの JSON ファイルにすべての評価結果をエクスポートすることができます。 または、一度に 1 つのデータベースを評価し、後で、SQL データベースにこれらの複数の JSON ファイルからの結果を統合することができます。

コマンドラインからのデータ移行のアシスタントを実行する方法については、次を参照してください。[実行データ Migration Assistant コマンドラインから](../dma/dma-commandline.md)です。 


## <a name="import-assessment-results-into-a-sql-server-database"></a>評価の結果を SQL Server データベースにインポートします。

これで使用できる PowerShell スクリプトを使用して[Github リポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant)評価の結果を JSON ファイルから SQL Server データベースにインポートします。

> [!NOTE]
> PowerShell v5 以上が必要です。

スクリプトを実行するときに、次の情報を提供する必要があります。 

- **serverName**: SQL Server インスタンス名の評価をインポートすることは、JSON ファイルから結果します。

- **databaseName**: 結果の取得にインポートするデータベース名。

- **jsonDirectory**: 1 つまたは複数の JSON ファイルで、評価の結果が保存されているフォルダーです。

- **プロセス**: SQLServer

よう「関数を実行する」セクションで、前の値を追加します。

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

PowerShell スクリプトは、オブジェクトがまだ存在しない場合、指定した SQL インスタンスで、次のオブジェクトを作成します。

- **データベース**– PowerShell パラメーターで指定された名前

  - メイン リポジトリ

- **テーブル**– ・ レポートデータ ・

  - レポートのデータ

- **テーブル**-BreakingChangeWeighting

  - すべての重大な変更についての参照テーブル。 ここでより正確な割合 (%) のアップグレードの成功の順位付けに影響を与える、独自の重み付け値を定義できます。

- **ビュー** – UpgradeSuccessRanking\_と内部設置型

  - 移行した内部設置型であるデータベースごとに成功要因を表示するビュー。

- **ビュー** – UpgradeSuccessRanking\_Azure

  - 移行した内部設置型であるデータベースごとに成功要因を表示するビュー。

- **ストアド プロシージャ**– JSONResults\_挿入

  - SQL Server に JSON ファイルからデータをインポートするために使用します。

- **ストアド プロシージャ**– AzureFeatureParityResults\_挿入

  - Azure の機能パリティの結果を JSON ファイルから SQL Server にインポートするために使用します。

- **テーブル型**– JSONResults

  - 内部設置型の評価の JSON 結果を保持して、JSONResults に渡すために使用\_ストアド プロシージャの挿入

- **テーブル型**– AzureFeatureParityResults

  - Azure の機能に azure の評価の結果をパリティを保持して、AzureFeatureParityResults に渡すために使用\_ストアド プロシージャの挿入

PowerShell スクリプトを作成、**処理**が処理される JSON ファイルを含む指定したディレクトリ内のディレクトリ。

スクリプトが完了したら、結果は、テーブル、・ レポートデータ ・にインポートされます。

### <a name="viewing-the-results-in-sql-server"></a>SQL Server で結果を表示します。

データが読み込まれた後は、SQL Server インスタンスに接続します。 次の図に示すように、画面が表示されます。

![SQL Server データベースに統合されたレポート](../dma/media/DMAReportingDatabase.png)

Dbo します。・ レポートデータ ・ テーブルには、その生の形式で JSON ファイルの内容が含まれています。

## <a name="on-premises-upgrade-success-ranking"></a>内部設置型のアップグレード成功の順位付け

データベースおよびパーセント (%) の成功ランクの一覧を表示するには、dbo を選択します。UpgradeSuccessRanking_OnPrem ビュー:

![UpgradeSuccessRaning_OnPrem ビュー内のデータ](../dma/media/UpgradeSuccessRankingView.png)

ここで確認できます、特定のデータベースを別の互換性レベルのアップグレードが成功する可能性は何です。 したがって、たとえば、HR データベースは 100、110、120 と 130 の互換性レベルに対して評価されたされます。 この評価では、データベースが現在実行している現在のバージョンからそれ以降のバージョンの SQL Server への移行に多大な労力が必要なを視覚的に確認できます。

通常メトリック関心のあるは、ある重大な変更の数は、特定のデータベースです。 前の例では、100、110、120 と 130 の互換性レベルを 50% のアップグレードの成功率が HR データベースに含まれるがわかります。

このメトリックは、dbo で重み付け値を変更することにより影響を受けることができます。BreakingChangeWeighting テーブルです。

次の例では、HR データベースでの構文の問題の解決に必要な作業と見なされる高ために 3 の値を割り当てる**労力**です。 値 1 が割り当てられている構文の問題を修正するのに時間がかかるはありません、ため**FixTime**です。 値 2 が割り当てられているいくつかのコストを変更を行ったに関係できるようになります、ため**コスト**です。 この値を使用して、ブレンド Changerank が 2 に変更します。

> [!NOTE]
> 1 ~ 5 のスケールでは、スコア付けします。  1 が不足していると、5 が高いです。 また、ChangeRank は、計算列です。

![作業、FixTime、およびコストは、構文の問題の値します。](../dma/media/SyntaxIssueEffort.png)

Dbo をクエリするときは、この例のようになりましたUpgradeSuccessRanking_OnPrem ビュー、重大な変更の HR データベースにアップグレードの成功率が削除されます。

![HR データベースのアップグレードの成功要因](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Azure のアップグレードの成功の順位付け

Azure SQL DB、および割合成功ランクに移行するデータベースの一覧を表示するには、dbo を選択します。UpgradeSuccessRanking_Azure を表示します。

![UpgradeSuccessRanking_Azure ビュー内のデータ](../dma/media/UpgradeSuccessRankingView_Azure.png)

ここで、興味のある MigrationBlocker 値。 100.00 では、Azure SQL Database v12 にデータベースを移動するための 100% の成功のランクがあることを意味します。

このビューとの違いがない現在移行ブロック規則に対する重み付けを変更するためのオーバーライドです。

Power BI を使用してこのデータをレポートする方法の詳細については、次を参照してください。 [PowerBI との統合、評価の報告](../dma/dma-powerbiassesreport.md)です。
