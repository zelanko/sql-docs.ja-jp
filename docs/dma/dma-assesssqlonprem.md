---
title: エンタープライズを評価し、評価レポート (SQL Server) の統合 |Microsoft Docs
description: DMA を使用して、企業を評価し、Azure SQL Database に SQL Server をアップグレードまたは移行する前に評価レポートを統合する方法について説明します。
ms.custom: ''
ms.date: 08/21/2018
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
ms.openlocfilehash: 9f8deae9dc7f31eaa41c5e4261a2848648f60090
ms.sourcegitcommit: 42455727824e2bfa0173d9752f4ae6839ee6031f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "40396417"
---
# <a name="assess-an-enterprise-and-consolidate-assessment-reports-with-dma"></a>エンタープライズを評価し、DMA で評価レポートの統合

次の手順では、Data Migration Assistant を使用して、オンプレミスの SQL Server または Azure vm で SQL Server の実行をアップグレードするため、または Azure SQL Database に移行するために、成功したスケールの評価を実行することができます。

## <a name="prerequisites"></a>前提条件

- DMA の開始元となるネットワーク上のツールのコンピューターを指定します。 このコンピューターに、SQL Server のターゲットへの接続があることを確認します。
- ダウンロードしてインストールします。
    - [Data Migration Assistant](https://www.microsoft.com/en-us/download/details.aspx?id=53595) v3.6 以降。
    - [PowerShell](http://aka.ms/wmf5download) v5.0 以降。
    - [.NET framework](https://www.microsoft.com/download/details.aspx?id=30653) v4.5 以上。
    - [SSMS](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) 17.0 以降。
    - [PowerBI desktop](https://docs.microsoft.com/power-bi/desktop-get-the-desktop)します。
- ダウンロードして抽出します。
    - [DMA レポートの Power BI テンプレート](https://msdnshared.blob.core.windows.net/media/2018/04/PowerBI-Reports1.zip)します。
    - [LoadWarehouse スクリプト](https://msdnshared.blob.core.windows.net/media/2018/03/LoadWarehouse.zip)します。

## <a name="loading-the-powershell-modules"></a>PowerShell モジュールの読み込み
PowerShell モジュールを PowerShell モジュールのディレクトリに保存するを使用する前にそれらを明示的に読み込むことがなくモジュールを呼び出すことができます。

モジュールを読み込むには、次の手順に従います。
1. C:\Program \windowspowershell\modules に移動し、という名前のフォルダーを作成し、 **DataMigrationAssistant**します。
2. 開く、 [PowerShell モジュール](https://msdnshared.blob.core.windows.net/media/2018/03/PowerShell-Modules.zip)、し、作成したフォルダーに保存します。

      ![PowerShell モジュール](../dma/media//dma-assesssqlonprem/dma-powershell-modules.png)

    各フォルダーには、次の図に示すように、関連付けられている psm1 ファイルが含まれています。

   ![PowerShell モジュールの psm1 ファイル](../dma/media//dma-assesssqlonprem/dma-powershell-modules-psm1-files.png)

   > [!NOTE]
   > フォルダーとが含まれている psm1 ファイルには、同じ名前がある場合があります。

   > [!IMPORTANT]
   > PowerShell ファイルを正しく読み込むモジュールを確実に WindowsPowerShell ディレクトリに保存した後のブロックを解除する必要があります。 ファイルを右クリックし、PowerShell ファイルのブロックを解除するには、**プロパティ**を選択、**ブロックの解除**テキスト ボックス、および選択し**Ok**。

   ![psm1 ファイルのプロパティ](../dma/media//dma-assesssqlonprem/dma-psm1-file-properties.png)

    PowerShell が今すぐ自動的に読み込まこれらのモジュール、新しい PowerShell セッションの開始時にします。

## <a name="create-an-inventory-of-sql-servers"></a>SQL サーバーのインベントリを作成します。
SQL Server を評価する PowerShell スクリプトを実行する前に評価する SQL サーバーのインベントリを作成する必要があります。

このインベントリは、2 つの形式のいずれかにできます。
- Excel の CSV ファイル
- SQL Server テーブル

### <a name="if-using-a-csv-file"></a>CSV ファイルを使用する場合
を、データをインポートする csv ファイルを使用する場合は、データの 2 つの列があることを確認**インスタンス名**と**データベース名**、および列ヘッダー行があるはありません。
 
 ![csv ファイルの内容](../dma/media//dma-assesssqlonprem/dma-csv-file-contents.png)

### <a name="if-using-sql-server-table"></a>SQL Server テーブルを使用する場合
という名前のデータベースを作成する**EstateInventory**テーブルと呼ばれる、 **DatabaseInventory**します。 このインベントリ データを含むテーブルは、次の 4 つの列が存在する限り、列の任意の数を持つことができます。
- ServerName
- InstanceName
- DatabaseName
- AssessmentFlag
 
 ![SQL Server テーブルの内容](../dma/media//dma-assesssqlonprem/dma-sql-server-table-contents.png)

ツール コンピューターにこのデータベースでない場合は、ツールのコンピューターにこの SQL Server インスタンスへのネットワーク接続を確認します。

SQL Server テーブルを CSV ファイルを使用する利点は、インスタンスを制御]、[データベースの評価より小さいチャンクに分割しやすく、評価の取得が選択する評価のフラグ列を使用することができます。  複数の評価をまたがることができますし (この記事の後半で、評価の実行に関するセクションを参照します) (セクションを参照で、この記事の後半で、評価を実行している)、複数の CSV ファイルを管理するより簡単であります。

でオブジェクトとその複雑さの数に応じて、評価が取る著しく長い時間 (時間 +) できるようになりますが、評価を管理しやすいチャンクに分割することをお勧め留意してください。

## <a name="running-a-scaled-assessment"></a>スケールの評価の実行
モジュール ディレクトリに PowerShell モジュールを読み込むと、インベントリの作成、スケールの評価を実行して PowerShell を開き、dmaDataCollector 関数を実行する必要があります。
 
  ![dmaDataCollector 関数の一覧](../dma/media//dma-assesssqlonprem/dma-dmaDataCollector-function-listing.png)

DmaDataCollector 関数に関連付けられているパラメーターは、次の表で説明します。

|パラメーター  |説明
|---------|---------|
|**getServerListFrom** | インベントリ。 指定できる値は**SqlServer**と**CSV**します。 |
|**サーバー名** | SQL Server のインスタンス名を使用する場合は、在庫の**SqlServer**で、 **getServerListFrom**パラメーター。 |
|**DatabaseName** | インベントリ テーブルをホストするデータベース。 |
|**%Assessmentname** | DMA 評価の名前。 |
|**TargetPlatform** | 実行する評価対象の型。  指定できる値は**AzureSQLDatabase**、 **SQLServer2012**、 **SQLServer2014**、 **SQLServer2016**、 **SQLServerLinux2017**、および**SQLServerWindows2017**します。 |
|**AuthenticationMethod** | 評価する SQL Server のターゲットに接続するための認証方法。 指定できる値は**SQLAuth**と**WindowsAuth**します。 |
|**OutputLocation** | 評価の出力ファイル、JSON を格納するディレクトリ。 評価されているデータベースの数と、データベース内のオブジェクトの数に応じて、評価に異常に長い時間がかかることができます。 すべての評価が完了した後、ファイルが書き込まれます。 |

予期しないエラーがある場合は、このプロセスによって開始されたコマンド ウィンドウを終了します。  失敗の理由を特定のエラー ログを確認します。
 
  ![エラー ログの場所](../dma/media//dma-assesssqlonprem/dma-error-log-file-location.png)

## <a name="consuming-the-assessment-json-file"></a>評価の JSON ファイルの使用

評価が完了した後は、する分析のため、データを SQL Server にインポートする準備ができました。 評価の JSON ファイルを使用するには、PowerShell を開き、dmaProcessor 関数を実行します。
 
  ![dmaProcessor 関数の一覧](../dma/media//dma-assesssqlonprem/dma-dmaProcessor-function-listing.png)

DmaProcessor 関数に関連付けられているパラメーターは、次の表で説明します。

|パラメーター  |説明
|---------|---------|
|**プロセス**  | JSON ファイルの処理される場所です。 指定できる値は**SQLServer**と**AzureSQLDatabase**します。 |
|**サーバー名** | SQL Server インスタンスは、データを処理します。  指定した場合**AzureSQLDatabase**の**プロセス**パラメーター、SQL Server の名前のみを含める (含まれていません。 database.windows.net)。 Azure SQL データベースを対象とする場合に 2 つのログインする要求します。最初の 2 つ目は、Azure の SQL Server の管理者ログイン中に、Azure テナントの資格情報です。 |
|**CreateDMAReporting** | JSON ファイルを処理するために作成するステージング データベースです。  既に指定したデータベースが存在する、いずれかにこのパラメーターを設定すると、し、オブジェクトは作成できません。  このパラメーターは、削除された 1 つのオブジェクトを再作成するために便利です。 |
|**CreateDataWarehouse** | Power BI レポートで使用されるデータ ウェアハウスを作成します。 |
|**DatabaseName** | DMAReporting データベースの名前。 |
|**warehouseName** | データ ウェアハウス データベースの名前。 |
|**jsonDirectory** | 評価の JSON ファイルを含むディレクトリ。  ディレクトリに複数の JSON ファイルがある場合は、それらは 1 つずつ処理します。 |

DmaProcessor 関数は 1 つのファイルを処理するまで数秒かかる場合のみ必要があります。

## <a name="loading-the-data-warehouse"></a>Data warehouse の読み込み
DmaProcessor は、評価ファイルの処理の完了をデータは DMAReporting ・ レポートデータ ・ テーブル データベースに読み込まれます。 この時点では、data warehouse を読み込む必要があります。

1. LoadWarehouse スクリプトを使用して、次元内のすべての欠損値の設定。

    このスクリプトは DMAReporting データベースの・ レポートデータ ・ テーブルからデータを取得し、ウェアハウスに読み込むこと。  この読み込みプロセス中にエラーがある場合は、ディメンション テーブル内の不足しているエントリの結果と可能性があります。

2. データ ウェアハウスを読み込みます。
 
      ![読み込まれた LoadWarehouse 内容](../dma/media//dma-assesssqlonprem/dma-LoadWarehouse-loaded.png)

## <a name="set-your-database-owners"></a>データベースの所有者を設定します。
必須ではありませんが、レポートから最大限の価値をお勧めデータベースの所有者を設定すること、 **dimDBOwner**ディメンション、および更新**DBOwnerKey**で、 **FactAssessment**テーブル。  このプロセスに従うと、スライスと特定のデータベース所有者に基づく Power BI レポートをフィルター処理が許可されます。

データベース所有者を設定するための基本的な TSQL ステートメントを提供するのに LoadWarehouse スクリプトを使用することもできます。

  ![LoadWarehouse 設定所有者](../dma/media//dma-assesssqlonprem/dma-LoadWarehouse-set-owners.png)

## <a name="dma-reports"></a>DMA レポート

1. Power BI Desktop では、DMA レポートの Power BI テンプレートを開きます。
2. をポイント サーバーの詳細を入力、 **DMAWarehouse**データベースし、**ロード**します。

    > [!IMPORTANT]
    > 値をそのままにしてを押さないでください。

      ![読み込まれた DMA レポートの Power BI テンプレート](../dma/media//dma-assesssqlonprem/dma-reports-powerbi-template-loaded.png)

   レポートがからデータを更新した後、 **DMAWarehouse**データベースでは、次のようなレポートが表示されます。

   ![DMAWarehouse レポート ビュー](../dma/media//dma-assesssqlonprem/dma-DMAWarehouse-report.png)

   > [!TIP]
   > 予想したデータが表示されない場合は、アクティブなブックマークを変更してみてください。  詳細については、機能のセクションを参照してください。

## <a name="working-with-dma-reports"></a>DMA レポートの使用
DMA レポートを使用するには、スライサーを使用してフィルター処理します。
- [インスタンス名]
- データベース名
- チーム名

レポート間でコンテキストを切り替えるブックマークを使用することもできます。
- クラウドの評価
- オンプレミスの評価

  ![DMA レポートのブックマーク](../dma/media//dma-assesssqlonprem/dma-report-bookmarks.png)

> [!NOTE]
> Azure SQL Database の評価のみ実行すると、クラウド レポートのみが設定されます。 逆に、評価をオンプレミスでのみ実行すると、オンプレミスのレポートのみが設定されます。 ただし、Azure とオンプレミスの評価の両方を実行し、ウェアハウスに両方の評価を読み込む場合は切り替えることクラウドおよびオンプレミスのレポート ctrl キーをクリックして、関連付けられているアイコン。

## <a name="reports-visuals"></a>レポートのビジュアル
次のセクションでは、Power BI レポートに表示される詳細に表示されます。

### <a name="readiness-"></a>準備の %

  ![DMA の準備完了の割合](../dma/media//dma-assesssqlonprem/dma-readiness-percentage.png)

このビジュアルは選択コンテキストに基づく更新 (すべてのインスタンス、データベース [の倍数])。

### <a name="readiness-count"></a>準備状態の数

  ![DMA の準備完了数](../dma/media//dma-assesssqlonprem/dma-readiness-count.png)

このビジュアルには、移行する準備ができていないデータベースの数を移行する準備ができているデータベースの数が表示されます。

### <a name="readiness-bucket"></a>バケットの準備

  ![DMA Readiness バケット](../dma/media//dma-assesssqlonprem/dma-readiness-bucket.png)

このビジュアルは、次の準備のバケットによってデータベースの内訳を示しています。
- 100% の準備完了
- 75 ~ 99% の準備完了
- 50 ~ 75% の準備完了
- 準備ができていません

### <a name="issues-word-cloud"></a>ワード クラウドの問題
 
  ![DMA 問題 WordCloud](../dma/media//dma-assesssqlonprem/dma-issues-word-cloud.png)

このビジュアルでの選択コンテキスト内で現在発生している問題を示しています (すべてのインスタンス、データベース [の倍数])。 大きいほど、単語が表示される、大きい画面で、そのカテゴリで問題の数。 単語にマウス ポインターを合わせると、そのカテゴリ内に発生した問題数が表示されます。

### <a name="database-readiness"></a>データベースの準備

  ![DMA データベース準備レポート](../dma/media//dma-assesssqlonprem/dma-database-readiness-report.png)

このセクションでは、インスタンスのデータベースの準備状態を表示すると、レポートの主な部分です。 このレポートには、ドリル ダウン階層があります。
- InstanceDatabase
- ChangeCategory
- [タイトル]
- ObjectType
- ImpactedObjectName

 ![DMA データベース準備レポートのドリルダウン](../dma/media//dma-assesssqlonprem/dma-database-readiness-report-drilldown.png)

このレポートは、修復計画レポートを作成するためのフィルターの点としても機能します。

修復計画レポートをドリルダウンして、このグラフのデータ ポイントを右クリックをポイントして**ドリルスルー**、し、**修復プラン**します。

このタスクは、ドリルスルー オプションを選択した位置の点に基づく現在の階層レベルの修復計画レポートをフィルター処理します。

  ![フィルター処理された DMA データベース準備レポートのドリルダウン](../dma/media//dma-assesssqlonprem/dma-database-readiness-report-drilldown-filtered.png)

  ![DMA 修復計画レポート](../dma/media//dma-assesssqlonprem/dma-remediation-plan-report.png)

内のフィルターを使用して、カスタムの修復を構築するための独自のプランで修復プランのレポートを使用することもできます、**視覚エフェクト フィルター**ブレード。
 
  ![レポートのフィルター オプションの DMA 修復の計画](../dma/media//dma-assesssqlonprem/dma-remediation-plan-report-filter-options.png)

### <a name="script-disclaimer"></a>スクリプトの免責事項
*この記事で説明するサンプル スクリプトは、Microsoft の標準サポート プログラムまたはサービスではサポートされていません。すべてのスクリプトは、いかなる保証も伴わず IS として提供されます。さらに、Microsoft は黙示の保証を含め、これらに限定の商品性または特定目的に対する適合性の保証も行いません暗黙的に指定します。すべての使用または性能のドキュメントとサンプル スクリプトによって生じるリスクなります。イベントなしで Microsoft、その作成者、またはそれ以外の場合、作成、生産、またはスクリプトの配信に関連するすべてのユーザー負いませんのいかなる損害を含め、制限の損失、業務利益、業務の中断の喪失、ビジネス情報、またはその他の金銭損失) Microsoft がこのような損害の可能性について知らされていた場合でも、サンプル スクリプトまたはドキュメントについては、使用すること、または使用から生じる。その他のサイト/リポジトリ/ブログでこれらのスクリプトを再構成する前に権限をシークします。*