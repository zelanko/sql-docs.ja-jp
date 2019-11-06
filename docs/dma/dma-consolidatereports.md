---
title: エンタープライズを評価し、評価レポート (SQL Server) の統合 |Microsoft Docs
description: DMA を使用して、企業を評価し、Azure SQL Database に SQL Server をアップグレードまたは移行する前に評価レポートを統合する方法について説明します。
ms.custom: ''
ms.date: 06/21/2019
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
ms.openlocfilehash: 9538e66180fa401059135a5f8714ea39dd4e3f4a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058807"
---
# <a name="assess-an-enterprise-and-consolidate-assessment-reports-with-dma"></a>エンタープライズを評価し、DMA で評価レポートの統合

次の手順では、Data Migration Assistant を使用して、オンプレミスの SQL Server または Azure vm で SQL Server の実行をアップグレードするため、または Azure SQL Database に移行するために、成功したスケールの評価を実行することができます。

## <a name="prerequisites"></a>前提条件

- DMA の開始元となるネットワーク上のツールのコンピューターを指定します。 このコンピューターに、SQL Server のターゲットへの接続があることを確認します。
- ダウンロードしてインストールします。
  - [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) v3.6 以降。
  - [PowerShell](https://aka.ms/wmf5download) v5.0 以降。
  - [.NET framework](https://www.microsoft.com/download/details.aspx?id=30653) v4.5 以上。
  - [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17.0 以降。
  - [Power BI desktop](https://docs.microsoft.com/power-bi/desktop-get-the-desktop)します。
  - [Azure PowerShell モジュール](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-1.0.0)
- ダウンロードして抽出します。
  - [DMA レポートの Power BI テンプレート](https://techcommunity.microsoft.com/gxcuf89792/attachments/gxcuf89792/MicrosoftDataMigration/56/2/PowerBI-Reports.zip)します。
  - [LoadWarehouse スクリプト](https://techcommunity.microsoft.com/gxcuf89792/attachments/gxcuf89792/MicrosoftDataMigration/56/1/LoadWarehouse1.zip)します。

## <a name="loading-the-powershell-modules"></a>PowerShell モジュールの読み込み

PowerShell モジュールを PowerShell モジュールのディレクトリに保存するを使用する前にそれらを明示的に読み込むことがなくモジュールを呼び出すことができます。

モジュールを読み込むには、次の手順に従います。

1. C:\Program \windowspowershell\modules に移動し、という名前のフォルダーを作成し、 **DataMigrationAssistant**します。
2. 開く、 [PowerShell モジュール](https://techcommunity.microsoft.com/gxcuf89792/attachments/gxcuf89792/MicrosoftDataMigration/56/4/PowerShell-Modules2.zip)、し、作成したフォルダーに保存します。

      ![PowerShell モジュール](../dma/media//dma-consolidatereports/dma-powershell-modules.png)

    各フォルダーには、次の図に示すように、関連付けられている psm1 ファイルが含まれています。

   ![PowerShell モジュールの psm1 ファイル](../dma/media//dma-consolidatereports/dma-powershell-modules-psm1-files.png)

   > [!NOTE]
   > フォルダーとが含まれている psm1 ファイルには、同じ名前がある場合があります。

   > [!IMPORTANT]
   > PowerShell ファイルを正しく読み込むモジュールを確実に WindowsPowerShell ディレクトリに保存した後のブロックを解除する必要があります。 ファイルを右クリックし、PowerShell ファイルのブロックを解除するには、**プロパティ**を選択、**ブロックの解除**テキスト ボックス、および選択し**Ok**。

   ![psm1 ファイルのプロパティ](../dma/media//dma-consolidatereports/dma-psm1-file-properties.png)

    PowerShell が今すぐ自動的に読み込まこれらのモジュール、新しい PowerShell セッションの開始時にします。

## <a name="create-inventory"></a> SQL サーバーのインベントリを作成します。

SQL Server を評価する PowerShell スクリプトを実行する前に評価する SQL サーバーのインベントリを作成する必要があります。

このインベントリは、2 つの形式のいずれかにできます。

- Excel の CSV ファイル
- SQL Server テーブル

### <a name="if-using-a-csv-file"></a>CSV ファイルを使用する場合

> [!IMPORTANT]
> インベントリ ファイルがコンマ区切り (CSV) ファイルとして保存されたことを確認します。
>
> 既定のインスタンスには、MSSQLServer にインスタンス名を設定します。


を、データをインポートする csv ファイルを使用する場合は、データの 2 つの列があることを確認**インスタンス名**と**データベース名**、および列ヘッダー行があるはありません。

 ![csv ファイルの内容](../dma/media//dma-consolidatereports/dma-csv-file-contents.png)

### <a name="if-using-a-sql-server-table"></a>SQL Server テーブルを使用する場合

> [!IMPORTANT]
> 既定のインスタンスには、MSSQLServer にインスタンス名を設定します。

という名前のデータベースを作成する**EstateInventory**テーブルと呼ばれる、 **DatabaseInventory**します。 このインベントリ データを含むテーブルは、次の 4 つの列が存在する限り、列の任意の数を持つことができます。

- ServerName
- InstanceName
- DatabaseName
- AssessmentFlag

![SQL Server テーブルの内容](../dma/media//dma-consolidatereports/dma-sql-server-table-contents.png)

このデータベースがない場合、ツールのコンピューターで、ツールのコンピューターにこの SQL Server インスタンスへのネットワーク接続を確認します。

SQL Server テーブルを CSV ファイルを使用する利点は、インスタンスを制御]、[データベースの評価より小さいチャンクに分割しやすく、評価の取得が選択する評価のフラグ列を使用することができます。  複数の評価をまたがることができますし (セクションを参照で、この記事の後半で、評価を実行している)、複数の CSV ファイルを管理するより簡単であります。

でオブジェクトとその複雑さの数に応じて、評価が取る著しく長い時間 (時間 +) できるようになりますが、評価を管理しやすいチャンクに分割することをお勧め留意してください。

## <a name="running-a-scaled-assessment"></a>スケールの評価の実行

モジュール ディレクトリに PowerShell モジュールを読み込むと、インベントリの作成、スケールの評価を実行して PowerShell を開き、dmaDataCollector 関数を実行する必要があります。
 
  ![dmaDataCollector 関数の一覧](../dma/media//dma-consolidatereports/dma-dmaDataCollector-function-listing.png)

DmaDataCollector 関数に関連付けられているパラメーターは、次の表で説明します。

|パラメーター  |説明 |
|---------|---------|
|**getServerListFrom** | インベントリ。 指定できる値は**SqlServer**と**CSV**します。<br/>詳細については、次を参照してください。 [SQL サーバーのインベントリ作成](#create-inventory)です。 |
|**csvPath** | CSV インベントリ ファイルへのパス。  場合にのみ使用**getServerListFrom**に設定されている**CSV**します。 |
|**serverName** | SQL Server のインスタンス名を使用する場合は、在庫の**SqlServer**で、 **getServerListFrom**パラメーター。 |
|**databaseName** | インベントリ テーブルをホストするデータベース。 |
|**%Assessmentname** | DMA 評価の名前。 |
|**TargetPlatform** | 実行する評価対象の型。  指定できる値は**AzureSQLDatabase**、 **SQLServer2012**、 **SQLServer2014**、 **SQLServer2016**、 **SQLServerLinux2017**、 **SQLServerWindows2017**、および**ManagedSqlServer**します。 |
|**AuthenticationMethod** | 評価する SQL Server のターゲットに接続するための認証方法。 指定できる値は**SQLAuth**と**WindowsAuth**します。 |
|**OutputLocation** | 評価の出力ファイル、JSON を格納するディレクトリ。 評価されているデータベースの数と、データベース内のオブジェクトの数に応じて、評価に異常に長い時間がかかることができます。 すべての評価が完了した後、ファイルが書き込まれます。 |

予期しないエラーがある場合は、このプロセスによって開始されたコマンド ウィンドウを終了します。  失敗の理由を特定のエラー ログを確認します。
 
  ![エラー ログの場所](../dma/media//dma-consolidatereports/dma-error-log-file-location.png)

## <a name="consuming-the-assessment-json-file"></a>評価の JSON ファイルの使用

評価が完了すると、分析のための SQL Server にデータをインポートする準備がするようになりました。 評価の JSON ファイルを使用するには、PowerShell を開き、dmaProcessor 関数を実行します。
 
  ![dmaProcessor 関数の一覧](../dma/media//dma-consolidatereports/dma-dmaProcessor-function-listing.png)

DmaProcessor 関数に関連付けられているパラメーターは、次の表で説明します。

|パラメーター  |説明 |
|---------|---------|
|**プロセス** | JSON ファイルの処理される場所です。 指定できる値は**SQLServer**と**AzureSQLDatabase**します。 |
|**serverName** | SQL Server インスタンスは、データを処理します。  指定した場合**AzureSQLDatabase**の**プロセス**パラメーターでは、SQL Server の名前のみを含める (は含まれていません。 database.windows.net)。 求められます 2 つのログインの Azure SQL データベースを対象とする場合最初の 2 つ目は、Azure の SQL Server の管理者ログイン中に、Azure テナントの資格情報です。 |
|**CreateDMAReporting** | JSON ファイルを処理するために作成するステージング データベースです。  既に指定したデータベースが存在する、いずれかにこのパラメーターを設定すると、オブジェクトを作成取得はありません。  このパラメーターは、削除された 1 つのオブジェクトを再作成するために便利です。 |
|**CreateDataWarehouse** | Power BI レポートで使用されるデータ ウェアハウスを作成します。 |
|**databaseName** | DMAReporting データベースの名前。 |
|**warehouseName** | データ ウェアハウス データベースの名前。 |
|**jsonDirectory** | 評価の JSON ファイルを含むディレクトリ。  ディレクトリに複数の JSON ファイルがあるかどうかは、それらを処理している 1 つずつです。 |

DmaProcessor 関数は 1 つのファイルを処理するまで数秒かかる場合のみ必要があります。

## <a name="loading-the-data-warehouse"></a>Data warehouse の読み込み

DmaProcessor は、評価ファイルの処理の完了をデータは DMAReporting ・ レポートデータ ・ テーブル データベースに読み込まれます。 この時点では、data warehouse を読み込む必要があります。

1. LoadWarehouse スクリプトを使用して、次元内のすべての欠損値の設定。

    このスクリプトは DMAReporting データベースの・ レポートデータ ・ テーブルからデータを取得し、ウェアハウスに読み込むこと。  この読み込みプロセス中にエラーがある場合は、ディメンション テーブル内の不足しているエントリの結果と可能性です。

2. データ ウェアハウスを読み込みます。
 
      ![読み込まれた LoadWarehouse 内容](../dma/media//dma-consolidatereports/dma-LoadWarehouse-loaded.png)

## <a name="set-your-database-owners"></a>データベースの所有者を設定します。

必須ではありませんが、レポートから最大限の価値をお勧めデータベースの所有者を設定すること、 **dimDBOwner**ディメンション、および更新**DBOwnerKey**で、 **FactAssessment**テーブル。  このプロセスに従うと、スライスと特定のデータベース所有者に基づく Power BI レポートをフィルター処理が許可されます。

データベース所有者を設定するための基本的な TSQL ステートメントを提供するのに LoadWarehouse スクリプトを使用することもできます。

  ![LoadWarehouse 設定所有者](../dma/media//dma-consolidatereports/dma-LoadWarehouse-set-owners.png)

## <a name="dma-reports"></a>DMA レポート

1. Power BI Desktop では、DMA レポートの Power BI テンプレートを開きます。
2. をポイント サーバーの詳細を入力、 **DMAWarehouse**データベースし、**ロード**します。

   ![読み込まれた DMA レポートの Power BI テンプレート](../dma/media//dma-consolidatereports/dma-reports-powerbi-template-loaded.png)

   レポートがからデータを更新した後、 **DMAWarehouse**データベース、次のようなレポートに表示されます。

   ![DMAWarehouse レポート ビュー](../dma/media//dma-consolidatereports/dma-DMAWarehouse-report1.png)

   > [!TIP]
   > 予想したデータが表示されない場合は、アクティブなブックマークを変更してみてください。  詳細については、次のセクションで詳細を参照してください。

## <a name="working-with-dma-reports"></a>DMA レポートの使用

DMA レポートを操作するには、ブックマークとスライサーを使用してフィルター処理します。

- 評価の種類 (Azure SQL DB、Azure SQL MI、SQL、オンプレミス) 
- [インスタンス名]
- データベース名
- チーム名

ブックマークとフィルター ブレードにアクセスするには、メイン レポートのページにフィルターのブックマークを選択します。

![DMA レポートのブックマークとフィルター](../dma/media//dma-consolidatereports/dma-report-bookmarks-filters.png)

フィルターのブックマークを選択するには、次のブレードが有効にします。

![DMA レポート ビュー ブレード](../dma/media//dma-consolidatereports/dma-report-views-blade.png)

ブックマークを使用して、レポート間でコンテキストを切り替えることができます。

- Azure SQL DB クラウドの評価
- Azure SQL MI クラウドの評価
- オンプレミスの評価

![DMA レポート ビューのブックマーク](../dma/media//dma-consolidatereports/dma-report-bookmarks1.png)

フィルター ブレードで、ctrl キーを押し、[戻る] ボタンをクリックを非表示にします。

![DMA レポート ビューに戻る ボタン](../dma/media//dma-consolidatereports/dma-report-bookmarks-back.png)

次の項目のいずれかで現在、フィルターが適用されているかどうかを表示するレポート ページの左下にあるが、プロンプトがあります。

- FactAssessment-InstanceName
- FactAssessment-DatabaseName
- dimDBOwner - DBOwner

![適用されるフィルターのプロンプト](../dma/media//dma-consolidatereports/dma-filter-applied-prompt.png)

> [!NOTE]
> Azure SQL Database の評価のみ実行すると、クラウド レポートのみが設定されます。 逆に、評価をオンプレミスでのみ実行すると、オンプレミスのレポートのみが設定されます。 ただし、Azure とオンプレミスの評価の両方を実行し、ウェアハウスに両方の評価を読み込む場合は切り替えることクラウドおよびオンプレミスのレポート ctrl キーをクリックして、関連付けられているアイコン。

## <a name="reports-visuals"></a>レポートのビジュアル

次のセクションでは、Power BI レポートに表示される詳細に表示されます。

### <a name="readiness-"></a>準備の %

  ![DMA の準備完了の割合](../dma/media//dma-consolidatereports/dma-readiness-percentage.png)

このビジュアルは選択コンテキストに基づく更新 (すべてのインスタンス、データベース [の倍数])。

### <a name="readiness-count"></a>準備状態の数

  ![DMA の準備完了数](../dma/media//dma-consolidatereports/dma-readiness-count.png)

このビジュアルには、移行する準備ができていないデータベースの数を移行する準備ができているデータベースの数が表示されます。

### <a name="readiness-bucket"></a>バケットの準備

  ![DMA Readiness バケット](../dma/media//dma-consolidatereports/dma-readiness-bucket.png)

このビジュアルは、次の準備のバケットによってデータベースの内訳を示しています。

- 100% の準備完了
- 75 ~ 99% の準備完了
- 50 ~ 75% の準備完了
- 準備ができていません

### <a name="issues-word-cloud"></a>ワード クラウドの問題
 
  ![DMA 問題 WordCloud](../dma/media//dma-consolidatereports/dma-issues-word-cloud.png)

このビジュアルでの選択コンテキスト内で現在発生している問題を示しています (すべてのインスタンス、データベース [の倍数])。 大きいほど、word はそのカテゴリ内の問題のより多くが画面に表示される、します。 単語にマウス ポインターを合わせると、そのカテゴリ内に発生した問題数が表示されます。

### <a name="database-readiness"></a>データベースの準備

  ![DMA データベース準備レポート](../dma/media//dma-consolidatereports/dma-database-readiness-report.png)

このセクションでは、インスタンスのデータベースの準備状態を表示すると、レポートの主な部分です。 このレポートには、ドリル ダウン階層があります。

- InstanceDatabase
- ChangeCategory
- タイトル
- ObjectType
- ImpactedObjectName

 ![DMA データベース準備レポートのドリルダウン](../dma/media//dma-consolidatereports/dma-database-readiness-report-drilldown.png)

このレポートは、修復計画レポートを作成するためのフィルターの点としても機能します。

修復計画レポートをドリルダウンして、このグラフのデータ ポイントを右クリックをポイントして**ドリルスルー**、し、**修復プラン**します。

このタスクは、ドリルスルー オプションを選択した位置の点に基づく現在の階層レベルの修復計画レポートをフィルター処理します。

  ![フィルター処理された DMA データベース準備レポートのドリルダウン](../dma/media//dma-consolidatereports/dma-database-readiness-report-drilldown-filtered.png)

  ![DMA 修復計画レポート](../dma/media//dma-consolidatereports/dma-remediation-plan-report.png)

内のフィルターを使用して、カスタムの修復を構築するための独自のプランで修復プランのレポートを使用することもできます、**視覚エフェクト フィルター**ブレード。
 
  ![レポートのフィルター オプションの DMA 修復の計画](../dma/media//dma-consolidatereports/dma-remediation-plan-report-filter-options.png)

### <a name="script-disclaimer"></a>スクリプトの免責事項

*この記事で説明するサンプル スクリプトは、Microsoft の標準サポート プログラムまたはサービスではサポートされていません。すべてのスクリプトは、いかなる保証も伴わず IS として提供されます。さらに、Microsoft は黙示の保証を含め、これらに限定の商品性または特定目的に対する適合性の保証も行いません暗黙的に指定します。すべての使用または性能のドキュメントとサンプル スクリプトによって生じるリスクなります。イベントなしで Microsoft、その作成者、またはそれ以外の場合、作成、生産、またはスクリプトの配信に関連するすべてのユーザー負いませんのいかなる損害を含め、制限の損失、業務利益、業務の中断の喪失、ビジネス情報、またはその他の金銭損失) Microsoft がこのような損害の可能性について知らされていた場合でも、サンプル スクリプトまたはドキュメントについては、使用すること、または使用から生じる。その他のサイト/リポジトリ/ブログでこれらのスクリプトを再構成する前に権限をシークします。*
