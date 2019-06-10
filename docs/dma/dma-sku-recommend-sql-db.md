---
title: (Data Migration Assistant)、オンプレミス データベースの適切な Azure SQL データベース SKU の識別 |Microsoft Docs
description: Data Migration Assistant を使用して、オンプレミス データベースの右側の Azure SQL データベースの SKU を特定する方法について説明します
ms.custom: ''
ms.date: 05/06/2019
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
ms.author: jtoland
manager: jroth
ms.openlocfilehash: 5effd31d37af5fbe119f1ad23781b994fa89c240
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794317"
---
# <a name="identify-the-right-azure-sql-databasemanaged-instance-sku-for-your-on-premises-database"></a>オンプレミス データベースの右側の Azure SQL Database/マネージ インスタンス SKU の識別します。

しようとして、データベースの最適な Azure のデータベース ターゲットと SKU を選択する場合は特に、データベース、クラウドへの移行が複雑になることができます。 目標に、Database Migration Assistant (DMA) は、これらの質問に対する回答や、操作をより簡単でわかりやすい出力をこれらの SKU の推奨事項を提供することで、データベースの移行を作成するためです。

この記事では、DMA の Azure SQL データベースの SKU の推奨事項の機能について説明します。 Azure SQL Database など、いくつかの展開オプションがあります。

- 1 つのデータベース
- エラスティック プール
- マネージ インスタンス

SKU の推奨事項機能では、Azure SQL Database の単一データベースの推奨最小両方を識別できます。 または、データベースをホストしているコンピューターから収集されたパフォーマンス カウンターに基づいて、SKU、マネージ インスタンス。 機能は、1 か月あたりの推定コストに加え、レベル、コンピューティング レベル、および最大データ サイズ、価格に関連する推奨事項を提供します。 単一データベースの一括プロビジョニングと推奨されるすべてのデータベースを Azure でのマネージ インスタンスに機能も提供します。

> [!NOTE]
> この機能は現在使用可能なのみを使用して、コマンド ライン インターフェイス (CLI) です。

Azure SQL データベースの SKU の推奨事項を特定し、対応する 1 つのデータベースまたは DMA を使用して Azure でのマネージ インスタンスをプロビジョニングするための手順を次に示します。

## <a name="prerequisites"></a>前提条件

- 最新バージョンのインストールをダウンロードして[DMA](https://aka.ms/get-dma)します。 ツールの以前のバージョンが既にある、それを開いてし、DMA のアップグレードを求められます。
- コンピューターにインストールすることを確認[PowerShell バージョン 5.1](https://www.microsoft.com/download/details.aspx?id=54616)または後で、すべてのスクリプトの実行に必要です。 コンピューターにどのバージョンの PowerShell がインストールされている findoug については、記事を参照してください。[をダウンロードして Windows PowerShell 5.1 をインストール](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-5-1)します。
- お使いのコンピューターに、Azure Powershell モジュールをインストールしてください。 詳細については、この記事を参照してください。 [Azure PowerShell モジュールをインストール](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-1.8.0)します。
- いることを確認、PowerShell ファイル**SkuRecommendationDataCollectionScript.ps1**、DMA フォルダーにインストールされますが、パフォーマンス カウンターを収集するために必要な。
- このプロセスを実行しますコンピューターのデータベースをホストしているコンピューターに管理者のアクセス許可があることを確認してください。

## <a name="collect-performance-counters"></a>パフォーマンス カウンターを収集します。

プロセスの最初の手順では、データベースのパフォーマンス カウンターを収集します。 データベースをホストするコンピューターで PowerShell コマンドを実行して、パフォーマンス カウンターを収集できます。 DMA を使うと、この PowerShell のファイルのコピーがコンピューターからパフォーマンス カウンターをキャプチャする、独自のメソッドを使用することもできます。

このタスクを個別に各データベースに対して実行する必要はありません。 コンピューターでホストされているすべてのデータベースの SKU を推奨するコンピューターから収集されたパフォーマンス カウンターを使用できます。

1. DMA フォルダーでは、PowerShell ファイル SkuRecommendationDataCollectionScript.ps1 を見つけます。 パフォーマンス カウンターを収集するには、このファイルが必要です。

    ![DMA フォルダーに示すように PowerShell ファイル](../dma/media/dma-sku-recommend-data-collection-file.png)

2. 次の引数には、PowerShell スクリプトを実行します。
    - **ComputerName**:データベースをホストするコンピューターの名前。
    - **OutputFilePath**:収集したカウンターを保存する出力ファイルのパス。
    - **CollectionTimeInSeconds**:この中にパフォーマンス カウンター データを収集する時間数。 意味のある推奨事項を取得するには少なくとも 40 分のパフォーマンス カウンターをキャプチャします。 がキャプチャ期間を長く、より正確な推奨事項になります。 またより正確な推奨事項を有効にする必要なデータベース ワークロードを実行していることを確認します。
    - **DbConnectionString**:元のパフォーマンス カウンター データを収集しているコンピューターでホストされている master データベースを指す接続文字列。

    呼び出しの例を次に示します。

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 2400
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```

    コマンドを実行した後、プロセスは指定した場所にパフォーマンス カウンターを含むファイルを出力します。 このファイルは、1 つのデータベースとマネージ インスタンス オプションの両方の SKU の推奨事項を提供すると、プロセスの次の部分の入力として使用できます。

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>DMA CLI を使用して、SKU の推奨事項の取得

このプロセスの入力として作成したパフォーマンス カウンターの出力ファイルを使用します。

1 つのデータベース オプションの DMA では価格レベル、コンピューティング レベル、および各データベースの最大データ サイズのコンピューターに Azure SQL Database の単一データベースの推奨事項を提供します。 をコンピューターに複数のデータベースがある場合は、推奨事項の対象となるデータベースも指定できます。 DMA も月額料金の見積もりでの提供の各データベース。

マネージ インスタンスの場合は、推奨事項は、リフト アンド シフト シナリオをサポートします。 その結果、DMA が表示されます、価格レベル、コンピューティング レベル、およびデータベースのセットの最大データ サイズのコンピューターに Azure SQL Database マネージ インスタンスの推奨事項。 もう一度、コンピューターに複数のデータベースがあれば、推奨事項の対象となるデータベースも指定できます。 DMA に対するも提供する月額料金の見積もりをマネージ インスタンス。

DMA CLI を使用して、コマンド プロンプトで、SKU の推奨事項を取得する、次の引数で dmacmd.exe を実行します。

- **/Action = SkuRecommendation**:SKU の評価を実行するには、この引数を入力します。
- **/SkuRecommendationInputDataFilePath**:前のセクションで収集されたカウンター ファイルへのパス。
- **/SkuRecommendationTsvOutputResultsFilePath**:TSV 形式で出力結果を書き込むパス。
- **/SkuRecommendationJsonOutputResultsFilePath**:JSON 形式で出力結果を書き込むパス。
- **/SkuRecommendationHtmlResultsFilePath**:HTML 形式で出力結果を書き込むパス。

さらに、次の引数のいずれかを選択します。

- 価格の更新されないようにします。
  - **/SkuRecommendationPreventPriceRefresh**:場合は True に設定され、価格の更新が発生していることを防止、既定の価格を前提としています。 オフライン モードで実行されている場合に使用します。 このパラメーターを使用しない場合は、指定した領域に基づいた最新の価格を取得するのには、次のパラメーターを指定する必要があります。
- 最新の価格を取得します。
  - **/SkuRecommendationCurrencyCode**:(例: 価格を表示する通貨"USD")。
  - **/SkuRecommendationOfferName**:プランの名前 (例。"MS-解決しない場合、0003 P")。 詳細については、次を参照してください。、 [Microsoft Azure プランの詳細](https://azure.microsoft.com/support/legal/offer-details/)ページ。
    - **/SkuRecommendationRegionName**:リージョン名 (「米国西部」など)。
    - **/SkuRecommendationSubscriptionId**:サブスクリプション ID です。
    - **/AzureAuthenticationTenantId**:認証のテナント。
    - **/AzureAuthenticationClientId**:認証に使用される AAD アプリのクライアント ID。
    - 次の認証オプションのいずれか:
      - Interactive
        - **AzureAuthenticationInteractiveAuthentication**:認証のポップアップ ウィンドウに対して true に設定します。
      - 証明書ベース
        - **AzureAuthenticationCertificateStoreLocation**:証明書ストアの場所 (例:"CurrentUser") に設定します。
        - **AzureAuthenticationCertificateThumbprint**:証明書のサムプリントに設定します。
      - トークン ベース
        - **AzureAuthenticationToken**:証明書トークンに設定します。

> [!NOTE]
> 対話型認証のクライアント Id とテナント Id を取得するには、新しい AAD アプリケーションを構成する必要があります。 認証と、情報の記事でこれらの資格情報の取得の詳細については[Microsoft Azure Billing API コード サンプル。RateCard API](https://azure.microsoft.com/resources/samples/billing-python-ratecard-api/)の説明に従い**手順 1。AAD テナントでネイティブ クライアント アプリケーションを構成する**します。

最後に、推奨事項の対象となるデータベースを指定する際、省略可能な引数があります。 

- **/SkuRecommendationDatabasesToRecommend**:推奨事項を作成する対象のデータベースの一覧。 データベース名は大文字小文字を区別し、(1) する必要がありますが、入力 .csv に記載されて、二重引用符で囲む (2) 各および名の間で 1 つのスペースで区切る (3) 各 (例:/SkuRecommendationDatabasesToRecommend"Database1"="Database2""Database3"). このパラメーターを省略すると、推奨事項が入力 .csv ファイルで識別されたすべてのユーザー データベースに指定されていることを確認します。  

いくつかのサンプル呼び出しを次に示します。

**例 1:既定の価格に関する推奨事項を取得します。認証の資格情報を持っていない場合またはオフライン モードで実行するときに使用します。**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

**例 2:指定した領域 (例:"UKWest") の最新の価格に関する推奨事項の取得。**

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

**例 3:(例: 特定のデータベースに関する推奨事項を取得します。"TPCDS1G、EDW_3G、TPCDS10G")。**

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
/SkuRecommendationDatabasesToRecommend=“TPCDS1G” “EDW_3G” “TPCDS10G” 
/AzureAuthenticationInteractiveAuthentication=true 
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId> 
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

1 つのデータベースの推奨事項は、TSV の出力ファイルは、次のようになります。

![DMA フォルダーに示すように PowerShell 単一 db ファイル](../dma/media/dma-sku-recommend-single-db-recommendations.png)

マネージ インスタンスの推奨事項は、TSV の出力ファイルは、次のようになります。

![DMA フォルダーに示すように PowerShell マネージ インスタンスのファイル](../dma/media/dma-sku-recommend-mi-recommendations.png)

出力ファイル内の各列の説明に従います。

- **DatabaseName** -データベースの名前。
- **MetricType** -Azure SQL Database の推奨される 1 つ database/マネージ インスタンスのレベル。
- **MetricValue** -SKU を Azure SQL Database の推奨される 1 つ database/マネージ インスタンスします。
- **PricePerMonth** : 対応する SKU の 1 か月あたりの見積価格。
- **RegionName** : 対応する SKU のリージョン名。 
- **IsTierRecommended**の各レベルの最小 SKU の推奨事項をいたします。 データベースの適切なレベルを決定するためのヒューリスティックを適用します。 これは、どのレベルは、データベースの推奨が反映されます。 
- **ExclusionReasons** -この値は、階層が推奨される場合は空白です。 各層はお勧めしませんが、理由が選択されなかった理由を提供されています。
- **AppliedRules** -適用された規則の短い表記します。

最終的な推奨されるレベル (つまり、 **MetricType**) と値 (つまり、 **MetricValue**) の場所が見つかりません、 **IsTierRecommended** SKU の最小列が TRUE - が反映されますAzure、オンプレミス データベースのような成功率で実行するようにクエリで必要です。 マネージ インスタンスは、DMA は現在 40vcore Sku に最もよく使用される 8vcore に関する推奨事項をサポートします。 たとえば、S3 を選択し、または以下の推奨される SKU の最小の standard レベルの S4 場合をにより、クエリがタイムアウトまたは実行に失敗します。

HTML ファイルには、グラフィカルな形式では、この情報が含まれています。 最終的な推奨設定を表示して、プロビジョニング プロセスの次の部分のわかりやすい手段を提供します。 HTML 出力の詳細については、次のセクションでは。

## <a name="provision-recommended-skus-to-azure"></a>プロビジョニングは、azure Sku をお勧めします

数回クリックするだけでは、プロビジョニング対象のデータベースを移行する Azure の Sku に特定された推奨事項を使用できます。 Azure サブスクリプションは; を入力するのに HTML ファイルを使用することができます。価格レベルの選択、レベル、および、データベースのデータの最大サイズを計算します。データベースをプロビジョニングするためのスクリプトを生成します。 PowerShell を使用してこのスクリプトを実行することができます。

このプロセスを実行するには、1 台のコンピューターまたは大規模の SKU の推奨事項を決定する複数のコンピューターで行うことができます。 DMA 現在とシンプルでスケーラブルなの経験によって、コマンド ライン インターフェイスを使用してプロセス全体をサポートしています。

プロビジョニング情報を入力して、推奨事項は、変更するには、次のように HTML ファイルを更新します。

**1 つのデータベースの推奨事項**

![Azure SQL DB SKU に関する推奨事項 画面](../dma/media/dma-sku-recommend-single-db-recommendations1.png)

1. HTML ファイルを開き、次の情報を入力します。
    - **サブスクリプション ID** -データベースをプロビジョニングする Azure サブスクリプションのサブスクリプション ID。
    - **リソース グループ**-データベースをデプロイするリソース グループ。 存在するリソース グループを入力します。
    - **リージョン**-データベースをプロビジョニングするリージョン。 サブスクリプションが選択領域をサポートしていることを確認します。
    - **サーバー名**-Azure SQL Database サーバーのデータベースをデプロイします。 存在しないサーバー名を入力すると、それが作成されます。
    - **管理者のユーザー名**-サーバー管理者のユーザー名。
    - **管理者パスワード**-サーバー管理者のパスワード。 パスワードは、8 文字以上および 128 個の文字の長さである必要があります。 パスワードは、次のカテゴリの 3 つの文字を含める必要があります: 大文字の文字、英語の小文字、数字 (0 ~ 9)、および英数字以外の文字 (!、$、#、% など。)。 パスワードは、すべてを含めることはできませんまたはユーザー名の一部 (3 + 文字以上連続して)。

2. データベースごとの推奨事項を確認し、価格レベルを変更、レベル、および必要に応じて、最大データ サイズを計算します。 現在しないプロビジョニングするすべてのデータベースの選択を解除してください。

3. 選択**プロビジョニング スクリプトの生成**スクリプトを保存および PowerShell でこれを実行します。

    このプロセスは、HTML ページで選択したすべてのデータベースを作成する必要があります。

**マネージ インスタンスの推奨事項**

![Azure SQL MI SKU に関する推奨事項 画面](../dma/media/dma-sku-recommend-mi-recommendations1.png)

1. HTML ファイルを開き、次の情報を入力します。
    - **サブスクリプション ID** -データベースをプロビジョニングする Azure サブスクリプションのサブスクリプション ID。
    - **リソース グループ**-データベースをデプロイするリソース グループ。 存在するリソース グループを入力します。
    - **リージョン**-データベースをプロビジョニングするリージョン。 サブスクリプションが選択領域をサポートしていることを確認します。
    - **インスタンス名**– データベースを移行する、Azure SQL マネージ インスタンスのインスタンス。 インスタンス名は、数字、小文字アルファベットを含めることができ、'-'、先頭し、末尾にそのことはできませんが、'-' 文字を 63 を超えること。
    - **管理者のユーザー名をインスタンス**– インスタンスの管理者ユーザー名。 ユーザーのログイン名は、次の要件を満たす - な SQL 識別子としない (管理者、管理者、sa、root、dbmanager、loginmanager など) などの一般的なシステム名または組み込みのデータベース ユーザーまたはロール (dbo、guest、public など) などがかどうかを確認します。 自分の名前には、空白文字、Unicode 文字、または非英字が含まれていないし、数字または記号での先頭にないことを確認してください。 
    - **インスタンスの管理者パスワード**-インスタンスの管理者パスワード。 パスワードは、16 文字以上および 128 個の文字の長さにする必要があります。 パスワードは、次のカテゴリの 3 つの文字を含める必要があります: 大文字の文字、英語の小文字、数字 (0 ~ 9)、および英数字以外の文字 (!、$、#、% など。)。 パスワードは、すべてを含めることはできませんまたはユーザー名の一部 (3 + 文字以上連続して)。
    - **Vnet 名**– マネージ インスタンスをプロビジョニングすること、VNet の名前。 既存の VNet の名前を入力します。
    - **サブネット名**– マネージ インスタンスをプロビジョニングすること、サブネット名。 既存のサブネット名を入力します。

2. 各インスタンスについて、推奨事項を確認および価格レベルを変更、レベル、および必要に応じて、最大データ サイズを計算します。 推奨事項は、40vcore Sku に 8vcore に制限されてはまだ必要な場合は、64vcore および 80vcore Sku をプロビジョニングするオプション。 現在しないプロビジョニングするすべてのインスタンスの選択を解除してください。

    このプロセスは、HTML ページで選択したすべてのデータベースを作成する必要があります。

    > [!NOTE]
    > (特に最初の時刻) のサブネット上のマネージ インスタンスを作成すると、完了に数時間がかかる場合があります。 を PowerShell を使用してプロビジョニング スクリプトを実行した後に、Azure Portal で、展開の状態を確認することができます。

## <a name="next-step"></a>次の手順

- CLI から DMA を実行するためのコマンドの完全な一覧は、記事を参照してください。[実行 Data Migration Assistant、コマンドラインから](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017)します。
