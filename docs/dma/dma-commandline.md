---
title: コマンドライン (SQL Server) から Data Migration Assistant を実行 |Microsoft Docs
description: SQL Server データベースの移行を評価するためのコマンドラインから Data Migration Assistant を実行する方法について説明します
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 575c456736242bebfe23544c430efe414d5097d2
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57974181"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>コマンドラインから Data Migration Assistant を実行します。
Data Migration Assistant をインストールするバージョン 2.1 以降で、ときで dmacmd.exe もインストールされます *%programfiles%\\Microsoft Data Migration Assistant\\*します。 Dmacmd.exe を使用して、無人モードでデータベースを評価し、JSON または CSV ファイルに結果を出力します。 このメソッドは、いくつかのデータベースや巨大なデータベースを評価するときに便利です。 

> [!NOTE]
> 評価のみを実行している Dmacmd.exe をサポートします。 この時点では、移行はサポートされていません。


## <a name="assessments-using-the-command-line-interface-cli"></a>コマンド ライン インターフェイス (CLI) を使用して評価

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentSourcePlatform="SourcePlatform"]
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
|`/AssessmentSourcePlatform`     | 評価では、サポートされている値のソースのプラットフォーム:SqlOnPrem、RdsSqlServer します。 ターゲットの準備状態評価は、ソースのプラットフォームとしても Cassandra をサポートします。 既定値は SqlOnPrem   | N
|`/AssessmentTargetPlatform`     | 評価では、サポートされている値のターゲット プラットフォーム:AzureSqlDatabase、ManagedSqlServer、SqlServer2012、SqlServer2014、SqlServer2016、SqlServerLinux2017 および SqlServerWindows2017 します。 ターゲットの準備状態評価は、ターゲット プラットフォームとしても cosmos Db をサポートします。 既定値は SqlServerWindows2017   | N
|`/AssessmentEvaluateFeatureParity`  | 機能パリティ ルールを実行します。 ターゲット プラットフォーム AzureSqlDatabase の機能パリティの評価はサポートされていませんソースのプラットフォームが RdsSqlServer の場合は、  | N
|`/AssessmentEvaluateCompatibilityIssues`     | 互換性規則を実行します。  | Y <br> (AssessmentEvaluateCompatibilityIssues または AssessmentEvaluateRecommendations が必要です)。
|`/AssessmentEvaluateRecommendations`     | 機能のお勧めを実行します。        | Y <br> (AssessmentEvaluateCompatibilityIssues または必要な AssessmentEvaluateRecommendationsis)
|`/AssessmentOverwriteResult`     | 結果ファイルを上書きします    | N
|`/AssessmentResultJson`     | JSON の結果ファイルへの完全パス     | Y <br> (AssessmentResultJson または AssessmentResultCsv のいずれかが必要)
|`/AssessmentResultCsv`    | CSV 結果ファイルへの完全パス   | Y <br>(AssessmentResultJson または AssessmentResultCsv のいずれかが必要)
|`/Action`    | SkuRecommendation を使用して、SKU の推奨事項の取得、AssessTargetReadiness を使用して、ターゲットの準備状態評価を実行します。   | N
|`/SourceConnections`    | 接続文字列のスペースで区切られた一覧。 データベース名 (初期カタログ) は省略可能です。 データベース名が指定されていない場合は、ソース上のすべてのデータベースは評価します。   | Y <br>(必須のかどうか、操作は 'AssessTargetReadiness')
|`/TargetReadinessConfiguration`    | 結果ファイルの名前、およびソースへの接続の値を記述する XML ファイルの完全パスです。   | Y <br>(TargetReadinessConfiguration または SourceConnections のいずれかが必要)
|`/FeatureDiscoveryReportJson`    | 機能探索 JSON レポートへのパス。 このファイルが生成される場合は、ソースに接続しなくても、ターゲットの準備状態評価を再実行に使用できます。   | N
|`/ImportFeatureDiscoveryReportJson`    | 先ほど作成した機能検出 JSON レポートへのパス。 ソースの接続ではなく、このファイルが使用されます。   | N

## <a name="examples-of-assessments-using-the-cli"></a>CLI を使用して評価の例

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Windows 認証と実行の互換性規則を使用して単一データベースの評価**


```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**SQL Server 認証と実行機能の推奨事項を使用して単一データベースの評価**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;User Id=myUsername;Password=myPassword;"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**ターゲット プラットフォームの SQL Server 2012 では、単一データベースの評価結果を .json および .csv のファイルに保存します。**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2012"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
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
/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```

**Windows 認証を使用して単一データベースのターゲットの準備状態評価**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"
```

**SQL Server 認証を使用して単一データベースのターゲットの準備状態評価**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;User Id=myUsername;Password=myPassword;" /AssessmentEvaluateRecommendations 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json" 

```

**ターゲット プラットフォームは、SQL Azure データベースの単一データベースの評価結果を .json および .csv のファイルに保存します。**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentSourcePlatform="SqlOnPrem"
/AssessmentTargetPlatform="AzureSqlDatabase"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"

```

**複数データベースのターゲットの準備状態評価**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/AssessmentSourcePlatform=SourcePlatform
/AssessmentTargetPlatform=TargetPlatform
/SourceConnections="Server=SQLServerInstanceName1;Initial Catalog=DatabaseName1;Integrated Security=true" "Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated Security=true" "Server=SQLServerInstanceName2;Initial Catalog=DatabaseName3;Integrated Security=true" 
/AssessmentOverwriteResult  
/AssessmentResultJson="C:\Results\test2016.json"

(/AssessmentSourcePlatform and /AssessmentTargetPlatform are optional.)
```

**Windows 認証を使用してサーバー上のすべてのデータベースのターゲットの準備状態評価**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**先ほど作成した機能の検出レポートをインポートすることでターゲットの準備状態評価**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/ImportFeatureDiscoveryReportJson="c:\temp\feature_report.json" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**構成ファイルを指定してターゲットの準備状態評価**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/TargetReadinessConfiguration=.\Config.xml

```
ソース接続の構成ファイルの内容を使用する場合。
```
<?xml version="1.0" encoding="utf-8" ?>
<TargetReadinessConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <SourcePlatform>Source Platform</SourcePlatform> <!-- Optional. The default is SqlOnPrem -->
  <TargetPlatform>TargetPlatform</TargetPlatform> <!-- Optional. The default is ManagedSqlServer -->
  <SourceConnections>
    <SourceConnection>connection string 1</SourceConnection>
    <SourceConnection>connection string 2</SourceConnection>
    <!-- ... -->
    <SourceConnection>connection string n</SourceConnection>
  </SourceConnections>
  <AssessmentResultJson>path\to\file.json</AssessmentResultJson>
  <FeatureDiscoveryReportJson>path\to\featurediscoveryreport.json</FeatureDiscoveryReportJson>
  <OverwriteResult>true</OverwriteResult> <!-- or false -->
</TargetReadinessConfiguration>
```

構成ファイルの内容をインポートするときに機能の検出レポート。
```
<TargetReadinessConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <ImportFeatureDiscoveryReportJson>path\to\featurediscoveryfile.json</ImportFeatureDiscoveryReportJson>
  <AssessmentResultJson>path\to\resultfile.json</AssessmentResultJson>
  <OverwriteResult>true</OverwriteResult><!-- or false -->
</TargetReadinessConfiguration>
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
