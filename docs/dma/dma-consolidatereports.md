---
title: インポートして、Data Migration Assistant の評価レポート (SQL Server) の統合 |Microsoft Docs
description: Data Migration Assistant から評価レポートを SQL Server データベースにインポートして、複数のレポートを統合する方法について説明します
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
ms.openlocfilehash: be9fc224093f0d5ae14372d4674a52589a2d4801
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781773"
---
# <a name="import-and-consolidate-data-migration-assistant-assessment-reports"></a>インポートして、Data Migration Assistant の評価レポートの統合

コマンドラインを使用して、Data Migration Assistant v2.1 以降無人モードでの移行の評価を実行することができます。 この機能を使用して、スケールで評価を実行するのに役立ちます。 JSON または CSV ファイルの形式で評価の結果。

Data Migration Assistant のコマンド ライン ユーティリティの 1 つのインスタンス化で複数のデータベースを評価し、すべての評価結果を 1 つの JSON ファイルにエクスポートできます。 または、時に 1 つのデータベースを評価し、後で SQL データベースにこれら複数の JSON ファイルからの結果を統合できます。

コマンドラインから Data Migration Assistant を実行する方法については、次を参照してください。[実行 Data Migration Assistant のコマンドラインから](../dma/dma-commandline.md)します。 

## <a name="import-assessment-results-into-a-sql-server-database"></a>評価の結果、SQL Server データベースにインポートします。

この PowerShell スクリプトを使用して[Github リポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant)評価の結果を JSON ファイルから SQL Server データベースにインポートします。

> [!NOTE]
> PowerShell v5 以上が必要です。

スクリプトを実行するときに、次の情報を提供する必要があります。 

- **serverName**: 評価をインポートする SQL Server インスタンス名が JSON ファイルから結果します。

- **databaseName**: 結果のインポートを取得するデータベース名。

- **jsonDirectory**: 評価の結果が、1 つまたは複数の JSON ファイルに保存されているフォルダー。

- **プロセス**: SQLServer

「関数を実行する」セクションよう上記値を追加します。

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

PowerShell スクリプトでは、オブジェクトがまだ存在しない場合に、指定した SQL インスタンスで、次のオブジェクトを作成します。

- **データベース**– PowerShell パラメーターで指定された名前

  - メイン リポジトリ

- **テーブル**– ・ レポートデータ ・

  - レポートのデータ

- **テーブル**-BreakingChangeWeighting

  - 参照テーブルのすべての重大な変更。 ここでより正確な割合 (%) アップグレードの成功のランクに影響する独自の重み付け値を定義できます。

- **ビュー** – UpgradeSuccessRanking\_OnPrem

  - オンプレミスに移行するのには、各データベースの成功の鍵を表示するビュー。

- **ビュー** – UpgradeSuccessRanking\_Azure

  - オンプレミスに移行するのには、各データベースの成功の鍵を表示するビュー。

- **ストアド プロシージャ**– JSONResults\_挿入

  - SQL Server に JSON ファイルからデータをインポートするために使用します。

- **ストアド プロシージャ**– AzureFeatureParityResults\_挿入

  - Azure の機能パリティの結果を JSON ファイルから SQL Server にインポートするために使用します。

- **テーブル型**– JSONResults

  - オンプレミスの評価のための JSON 結果を保持し、JSONResults に渡すために使用\_ストアド プロシージャの挿入

- **テーブル型**– AzureFeatureParityResults

  - Azure の機能に azure 評価の結果をパリティを保持して、AzureFeatureParityResults に渡すために使用\_ストアド プロシージャの挿入

PowerShell スクリプトを作成、**処理**が処理される JSON ファイルを含む指定したディレクトリ内のディレクトリ。

スクリプトが完了すると、結果は、テーブル、・ レポートデータ ・にインポートされます。

### <a name="viewing-the-results-in-sql-server"></a>SQL Server で結果を表示します。

データが読み込まれた後は、SQL Server インスタンスに接続します。 画面は、次の図に示すように表示されます。

![SQL Server データベースに統合されたレポート](../dma/media/DMAReportingDatabase.png)

Dbo します。・ レポートデータ ・ テーブルには、未加工の形式で JSON ファイルの内容が含まれています。

## <a name="on-premises-upgrade-success-ranking"></a>オンプレミスでアップグレードの成功の順位付け

データベースとその割合 (%) の成功の順位の一覧を表示するには、dbo を選択します。UpgradeSuccessRanking_OnPrem ビュー:

![UpgradeSuccessRaning_OnPrem 内のデータを表示します。](../dma/media/UpgradeSuccessRankingView.png)

ご覧のとおり、特定のデータベースを別の互換性レベルのアップグレードの成功の可能性とは何です。 そのため、たとえば、HR データベースは 100、110、120 と 130 の互換性レベルに対して評価されました。 この評価では、どの程度の労力は、データベースが現在実行している現在のバージョンからそれ以降のバージョンの SQL Server への移行に関係を視覚的に確認できます。

通常、メトリックの関心のあるでは、特定のデータベースの数の重大な変更がありますが、です。 前の例では、HR データベースに 100、110、120 と 130 の互換性レベルの 50% のアップグレードの成功要因がわかります。

このメトリックは、dbo で重み値を変更することで影響を受けることができます。BreakingChangeWeighting テーブルです。

次の例では、HR データベース内の構文の問題の修正に必要な作業と見なされます高に値 3 が割り当てられるように**労力**します。 値 1 が割り当てられているため、構文の問題を解決するのに時間がかかるでしょう、 **FixTime**します。 値 2 が割り当てられているため、若干のコストを変更を行ったに関連するは、**コスト**します。 この値を使用してブレンドされた Changerank を 2 に変更します。

> [!NOTE]
> 1 ~ 5 の小数点以下桁数には、スコア付けします。  1 が低いと 5 が増加します。 また、ChangeRank は計算列です。

![構文の問題の作業、FixTime、およびコストの値します。](../dma/media/SyntaxIssueEffort.png)

Dbo を照会する際に、この例のようになりましたUpgradeSuccessRanking_OnPrem ビューでは、重大な変更の HR データベースのアップグレードの成功の鍵は削除します。

![HR データベースのアップグレードの成功の鍵](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Azure のアップグレードの成功の順位付け

Azure SQL DB と順位成功に移行するデータベースの一覧を表示するには、dbo を選択します。UpgradeSuccessRanking_Azure を表示します。

![UpgradeSuccessRanking_Azure 内のデータを表示します。](../dma/media/UpgradeSuccessRankingView_Azure.png)

ここで関心がある MigrationBlocker 値。 100.00 では、Azure SQL Database v12 へのデータベースを移動するための 100% の成功のランクがあることを意味します。

このビューとの違いがない現在移行ブロック規則に対する重み付けを変更するためにオーバーライドします。

Power BI を使用してこのデータの報告方法の詳細については、次を参照してください。[レポートを power Bi との統合、評価](../dma/dma-powerbiassesreport.md)します。
