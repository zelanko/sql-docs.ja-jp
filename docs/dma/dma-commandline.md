---
title: コマンドライン (SQL Server) から Data Migration Assistant を実行 |Microsoft Docs
description: SQL Server データベースの移行を評価するためのコマンドラインから Data Migration Assistant を実行する方法について説明します
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 7d02ead6a601c47ba68bd12ece8fa444ceee5a9e
ms.sourcegitcommit: 170c275ece5969ff0c8c413987c4f2062459db21
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54226399"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>コマンドラインから Data Migration Assistant を実行します。
Data Migration Assistant をインストールするバージョン 2.1 以降で、ときで dmacmd.exe もインストールされます *%programfiles%\\Microsoft Data Migration Assistant\\*します。 Dmacmd.exe を使用して、無人モードでデータベースを評価し、JSON または CSV ファイルに結果を出力します。 このメソッドは、いくつかのデータベースや巨大なデータベースを評価するときに便利です。 

> [!NOTE]
> 評価のみを実行している Dmacmd.exe をサポートします。 この時点では、移行はサポートされていません。


## <a name="assessments-using-the-command-line-interface-cli"></a>コマンド ライン インターフェイス (CLI) を使用して評価

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```

|引数  |説明  | 必須 (はい/いいえ)
|---------|---------|---------------|
| `/help or /?`     | Dmacmd.exe ヘルプ テキストを使用する方法        | N
|`/AssessmentName`     |   評価プロジェクトの名前   | Y
|`/AssessmentDatabases`     | 接続文字列のスペースで区切られた一覧。 データベース名 (初期カタログ) と小文字は区別されます。 | Y
|`/AssessmentTargetPlatform`     | 評価では、サポートされている値のターゲット プラットフォーム:SqlServer2012、SqlServer2014、SqlServer2016、および AzureSqlDatabaseV12 します。 既定値は SqlServer2016   | N
|`/AssessmentEvaluateFeatureParity`  | 機能パリティ ルールを実行します。  | N
|`/AssessmentEvaluateCompatibilityIssues`     | 互換性規則を実行します。  | Y <br> (AssessmentEvaluateCompatibilityIssues または AssessmentEvaluateRecommendations が必要です)。
|`/AssessmentEvaluateRecommendations`     | 機能のお勧めを実行します。        | Y <br> (AssessmentEvaluateCompatibilityIssues または必要な AssessmentEvaluateRecommendationsis)
|`/AssessmentOverwriteResult`     | 結果ファイルを上書きします    | N
|`/AssessmentResultJson`     | JSON の結果ファイルへの完全パス     | Y <br> (AssessmentResultJson または AssessmentResultCsv のいずれかが必要)
|`/AssessmentResultCsv`    | CSV 結果ファイルへの完全パス   | Y <br>(AssessmentResultJson または AssessmentResultCsv のいずれかが必要)


## <a name="examples-of-assessments-using-the-cli"></a>CLI を使用して評価の例

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Windows 認証と実行の互換性規則を使用して単一データベースの評価**


```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**SQL Server 認証と実行機能の推奨事項を使用して単一データベースの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**ターゲット プラットフォームの SQL Server 2012 では、単一データベースの評価結果を .json および .csv のファイルに保存します。**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```

**ターゲット プラットフォームは、SQL Azure データベースの単一データベースの評価結果を .json および .csv のファイルに保存します。**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="AzureSqlDatabaseV12"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"
```

**複数データベースの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
***/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"***
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```

## <a name="azure-sql-database-sku-recommendations-using-the-cli"></a>CLI を使用して azure の SQL データベースの SKU の推奨事項

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|引数  |説明  | 必須 (はい/いいえ)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | DMA のコマンドラインを使用して SKU 評価を実行します。 | Y
|`/SkuRecommendationInputDataFilePath`  | 収集されたパフォーマンス カウンターのファイル、データベースをホストするコンピューターの完全なパス |    Y
|`/SkuRecommendationTsvOutputResultsFilePath`   | TSV 結果ファイルの完全なパス |    Y <br>(TSV または JSON または HTML ファイルのパスが必要)
|`/SkuRecommendationJsonOutputResultsFilePath`  | JSON の結果ファイルへの完全パス |   Y <br>(TSV または JSON または HTML ファイルのパスが必要)
|`/SkuRecommendationHtmlResultsFilePath` |  結果の HTML ファイルへの完全パス | Y <br>(TSV または JSON または HTML ファイルのパスが必要)
|`/SkuRecommendationPreventPriceRefresh` |  価格の更新が発生するを防ぎます。 オフライン モードで実行されている場合に使用します。 |    Y <br>(静的な価格についてはこの引数が選択されているまたは下のすべての引数が最新の価格を取得するために選択する必要があります)
|`/SkuRecommendationCurrencyCode` | (例: 価格を表示する通貨「(米ドル)」) | Y <br>(この場合、最新の価格を取得するには)
|`/SkuRecommendationOfferName` |    プランの名前 (例。"MS-解決しない場合、0003 P")。 詳細については、次を参照してください。、 [Microsoft Azure プランの詳細](https://azure.microsoft.com/support/legal/offer-details/)ページ。 |   Y <br>(この場合、最新の価格を取得するには)
|`/SkuRecommendationRegionName` |   領域の名前 (例。「米国西部」) |   Y <br>(この場合、最新の価格を取得するには)
|`/SkuRecommendationSubscriptionId` | サブスクリプション ID です。 |    Y <br>(この場合、最新の価格を取得するには)
|`/AzureAuthenticationTenantId` | 認証のテナント。 |  Y <br>(この場合、最新の価格を取得するには)
|`/AzureAuthenticationClientId` | 認証に使用される AAD アプリのクライアント ID。 | Y <br>(この場合、最新の価格を取得するには)
|`/AzureAuthenticationInteractiveAuthentication`    | ウィンドウがポップアップする場合は true に設定します。 |   Y <br>(この場合、最新の価格を取得するには) <br>(オプション 1 - 3 の認証オプションのいずれかを選択)
|`/AzureAuthenticationCertificateStoreLocation` | (例: 証明書ストアの場所に設定します。"CurrentUser")。 | Y <br>(この場合、最新の価格を取得するには) <br>(オプション 2 - 3 の認証オプションのいずれかを選択)
|`/AzureAuthenticationCertificateThumbprint`    | 証明書の拇印に設定します。 | Y <br>(この場合、最新の価格を取得するには) <br>(オプション 2 - 3 の認証オプションのいずれかを選択)
|`/AzureAuthenticationToken` |  証明書トークンに設定します。 | Y <br>(この場合、最新の価格を取得するには) <br>(オプション 3 - 3 の認証オプションのいずれかを選択)

## <a name="examples-of-sku-assessments-using-the-cli"></a>CLI を使用して SKU 評価の例

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**価格の更新 (get 最新の価格) - azure SQL DB の SKU の推奨事項対話型認証** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationInteractiveAuthentication=true 
```

**価格の更新 (get 最新の価格) - azure SQL DB の SKU の推奨事項の証明書認証**
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationCertificateStoreLocation=<Your Certificate Store Location>
/AzureAuthenticationCertificateThumbprint=<Your Certificate Thumbprint>  
```

**価格の更新 (get 最新の価格) - azure SQL DB の SKU の推奨事項のトークン認証**  
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationToken=<Your Authentication Token> 
```

**価格の更新 (静的な価格を使用) ことがなく azure SQL DB の SKU の推奨事項** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>関連項目
- [Data Migration Assistant](https://aka.ms/get-dma)をダウンロードします。
- この記事[オンプレミス データベースの適切な Azure SQL データベース SKU を特定](https://aka.ms/dma-sku-recommend-sqldb)します。
