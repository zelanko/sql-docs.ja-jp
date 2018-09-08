---
title: (Data Migration Assistant)、オンプレミス データベースの適切な Azure SQL データベース SKU の識別 |Microsoft Docs
description: Data Migration Assistant を使用して、オンプレミス データベースの右側の Azure SQL データベースの SKU を特定する方法について説明します
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
ms.openlocfilehash: 84601b6a556df64d3708fd749af06be8e753048d
ms.sourcegitcommit: 010755e6719d0cb89acb34d03c9511c608dd6c36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43240150"
---
# <a name="identify-the-right-azure-sql-database-sku-for-your-on-premises-database"></a>オンプレミス データベースの適切な Azure SQL データベース SKU の識別します。

クラウドへのデータベースの移行のタスクは、複雑で時間がかかり、多数の変数です。 データベースの適切な Azure のデータベース ターゲットと SKU を選択すると、困難なことができます。 目標に、Database Migration Assistant (DMA) はこれらの質問に対処し、簡単で効果的なデータベースの移行が発生することです。

この記事では、主に、データベースをホストしているコンピューターから収集されたパフォーマンス カウンターに基づいて、Azure SQL データベース SKU の推奨最小値を識別するためには、DMA の Azure SQL データベースの SKU の推奨事項機能に重点を置いています。 この機能は、1 か月あたりの推定コストに加え、レベル、コンピューティング レベル、および最大データ サイズ、価格に関連する推奨事項を提供します。 一括で Azure にすべてのデータベースをプロビジョニングする機能も提供します。

> [!NOTE] 
> この機能は現在使用可能なのみを使用して、コマンド ライン インターフェイス (CLI) です。 DMA のユーザー インターフェイスを使用してこの機能のサポートは、今後のリリースで追加されます。

> [!IMPORTANT]
> Azure SQL Database の SKU の推奨事項は、現在使用できる SQL Server 2016 から、またはそれ以降の移行は。

次の手順では、Azure SQL データベースの SKU の推奨事項を特定し、Data Migration Assistant を使用して azure に関連付けられているデータベースをプロビジョニングできます。

## <a name="prerequisites"></a>Prerequisites

V4.0 の Database Migration Assistant をダウンロードまたはそれ以降、し、インストールします。 既にある場合、ツールがインストール、閉じると、もう一度開き、ツールのアップグレードを求められます。

## <a name="collect-performance-counters"></a>パフォーマンス カウンターを収集します。

プロセスの最初の手順では、データベースのパフォーマンス カウンターを収集します。 データベースをホストするコンピューターで PowerShell コマンドを実行して、パフォーマンス カウンターを収集できます。 DMA を使うと、この PowerShell のファイルのコピーがコンピューターからパフォーマンス カウンターをキャプチャする、独自のメソッドを使用することもできます。

このタスクを個別に各データベースに対して実行する必要はありません。 コンピューターでホストされているすべてのデータベースの SKU を推奨するコンピューターから収集されたパフォーマンス カウンターを使用できます。

> [!IMPORTANT]
> このコマンドを実行するコンピューターには、データベースをホストするコンピューターに管理者のアクセス許可が必要です。

1. DMA フォルダー内のパフォーマンス カウンターを収集するために必要な PowerShell ファイルがインストールされていることを確認します。

    ![DMA フォルダーに示すように PowerShell ファイル](../dma/media/dma-sku-recommend-data-collection-file.png)

2. 次の引数には、PowerShell スクリプトを実行します。
    - **ComputerName**: データベースをホストするコンピューターの名前。
    - **OutputFilePath**: 出力ファイルのパスを収集したカウンターを保存します。
    - **CollectionTimeInSeconds**: パフォーマンス カウンター データを収集する場合、時間数。
      意味のある推奨事項を取得するには少なくとも 40 分のパフォーマンス カウンターをキャプチャします。 がキャプチャ期間を長く、より正確な推奨事項になります。
    - **DbConnectionString**: 元のパフォーマンス カウンター データを収集しているコンピューターでホストされている master データベースを指す接続文字列。
     
    呼び出しの例を次に示します。

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 10
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```
    
    コマンドを実行した後、プロセスは指定した場所でのパフォーマンス カウンターを持つファイルを出力します。 このファイルは、次のセクションでは、SKU の推奨事項のコマンドの入力として使用できます。

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>DMA CLI を使用して、SKU の推奨事項の取得

この手順の入力として前の手順からパフォーマンス カウンターの出力ファイルを使用します。 DMA は提供する、Azure SQL Database の推奨事項の価格レベル、コンピューティング レベル、および各データベースの最大データ サイズのコンピューターにします。 DMA も月額料金の見積もりでの提供の各データベース。

次の引数、dmacmd.exe を実行します。

- **/Action = SkuRecommendation**: SKU の評価を実行するには、この引数を入力します。
- **/SkuRecommendationInputDataFilePath**: 前のセクションで収集されたカウンター ファイルへのパス。
- **/SkuRecommendationTsvOutputResultsFilePath**: TSV 形式で出力結果を書き込むパス。
- **/SkuRecommendationJsonOutputResultsFilePath**: JSON 形式で出力結果を書き込むパス。
- **/SkuRecommendationHtmlResultsFilePath**: HTML 形式で出力結果を書き込むパス。

さらに、次の引数のいずれかを選択する必要があります。
- 価格の更新されないようにします。
    - **/SkuRecommendationPreventPriceRefresh**: 価格の更新が発生していることを防ぎます。 オフライン モードで実行されている場合に使用します。
- 最新の価格を取得します。 
    - **/SkuRecommendationCurrencyCode**: (例: 価格を表示する通貨"USD")。
    - **/SkuRecommendationOfferName**: プランの名前 (例。"MS-解決しない場合、0003 P")。 詳細については、次を参照してください。、 [Microsoft Azure プランの詳細](https://azure.microsoft.com/support/legal/offer-details/)ページ。
    - **/SkuRecommendationRegionName**: 領域の名前 (例。「米国西部」)。
    - **/SkuRecommendationSubscriptionId**: サブスクリプション id。
    - **/AzureAuthenticationTenantId**: 認証テナント。
    - **/AzureAuthenticationClientId**: 認証に使用される AAD アプリのクライアント ID。
    - 次の認証オプションのいずれか:
        - Interactive
            - **AzureAuthenticationInteractiveAuthentication**: 認証のポップアップ ウィンドウに対して true に設定します。
        - 証明書ベース
            - **AzureAuthenticationCertificateStoreLocation**: (例: 証明書ストアの場所に設定"CurrentUser")。
            - **AzureAuthenticationCertificateThumbprint**: 証明書のサムプリントに設定します。
        - トークン ベース
            - **AzureAuthenticationToken**: 証明書トークンに設定します。

いくつかのサンプル呼び出しを次に示します。

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
/AzureAuthenticationInteractiveAuthentication=true
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

TSV の出力ファイルには次の図に表示される列が含まれます。

   ![DMA フォルダーに示すように PowerShell ファイル](../dma/media/dma-tsv-file-column.png)

各列の説明に従います。

- **DatabaseName** – データベースの名前。
- **MetricName** – メトリックが実行されたかどうか。
- **MetricType** -Azure SQL Database の推奨レベルです。
- **MetricValue** -Azure SQL Database の SKU をお勧めします。
- **SQLMiEquivalentCores** -Azure SQL Database マネージ インスタンスに移動する場合は、コア数のこの値を使用できます。
- **IsTierRecommended**の各レベルの最小 SKU の推奨事項をいたします。 データベースの適切なレベルを決定するためのヒューリスティックを適用します。 
- **ExclusionReasons** -この値は、階層が推奨される場合は空白です。 各層は推奨されませんが、なぜこれが選択されません。 上の理由から提供されています。
- **AppliedRules** -適用された規則の短い表記します。

推奨値は、Azure、オンプレミス データベースのような成功率で実行するようにクエリに必要な最小の SKU。 たとえば、S3 を選択し、または以下の推奨される SKU の最小の standard レベルの S4 場合をにより、クエリがタイムアウトまたは実行に失敗します。

HTML ファイルには、グラフィカルな形式では、この情報が含まれています。 HTML ファイルを使用して、Azure サブスクリプションの情報を入力、価格レベルの選択、データベース、レベルとデータの最大サイズを計算し、データベースをプロビジョニングするスクリプトを生成することができます。 このスクリプトは、PowerShell を使用して実行できます。

## <a name="provision-your-databases-to-azure"></a>Azure へのデータベースをプロビジョニングします。
ほんの数回のクリックで、データベースを移行する Azure でターゲット データベースの準備には、前の手順からの推奨事項を使用できます。 次のように HTML ファイルを更新することで推奨事項は、変更を行うこともできます。

1. HTML ファイルを開き、次の情報を入力します。
    - **サブスクリプション ID** – データベースをプロビジョニングする Azure サブスクリプションのサブスクリプション ID。
    - **リージョン**– データベースをプロビジョニングするリージョン。 サブスクリプションが選択領域をサポートしていることを確認します。
    - **リソース グループ**– データベースをデプロイするリソース グループ。 存在するリソース グループを入力します。
    - **サーバー名**– Azure SQL Database サーバーのデータベースをデプロイします。 存在しないサーバー名を入力すると、それが作成されます。
    - **管理者ユーザー名とパスワード**– サーバー管理者ユーザー名とパスワード。

2. データベースごとの推奨事項を確認し、価格レベルを変更、レベル、および必要に応じて、最大データ サイズを計算します。 現在しないプロビジョニングするすべてのデータベースの選択を解除してください。

3. 選択**プロビジョニング スクリプトの生成**スクリプトを保存および PowerShell でこれを実行します。

    このプロセスは、HTML ページで選択したすべてのデータベースを作成する必要があります。

すべての手順を実行するには 1 台のコンピューター上でこのプロセスでまたは大規模の SKU の推奨事項を決定する複数のコンピューター上で実行することができます。 DMA によって、コマンド ライン インターフェイスを使用してこれらすべての手順をサポートすることで、シンプルかつスケーラブルなエクスペリエンスがなります。 ここでも、DMA のユーザー インターフェイスを使用してこの機能のサポートは、今年の後半で使用してになります。

## <a name="next-steps"></a>次の手順
- 最新バージョンのダウンロード[Data Migration Assistant](https://aka.ms/get-dma)します。
- 記事をご覧ください[実行 Data Migration Assistant、コマンドラインから](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017)CLI から DMA を実行するためのコマンドの完全な一覧についてはします。
