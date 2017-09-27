---
title: "インポートおよびエクスポート ウィザードのこの簡単な例の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ea3db39b-698b-4a74-8eb8-21dc7252dc1a
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 59c7e1cc3c31f77652acb21d375e1294bdc93397
ms.openlocfilehash: 9eee58be471d8b39b051c1343f9eb26a2960b6d6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="get-started-with-this-simple-example-of-the-import-and-export-wizard"></a>インポートおよびエクスポート ウィザードのこの簡単な例の概要します。
SQL Server データベースへの Excel スプレッドシートからデータをインポートする - 一般的なシナリオを用いて、SQL Server インポートおよびエクスポート ウィザードに含まれる新機能について説明します。 別のソースと別の変換先を使用することを計画する場合でもこのトピックではほとんどのウィザードの実行について知っておく必要があります。

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>前提条件、お使いのコンピューターにインストールされているウィザードとは
ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「 [SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。

## <a name="heres-the-excel-source-data-for-this-example"></a>この例の Excel ソースのデータを次に示します
-WizardWalkthrough.xlsx Excel ブックの WizardWalkthrough ワークシートに 2 列の小さなテーブルにコピーしようとしているソース データを次に示します。

![Excel ソースのデータ](../../integration-services/import-export-data/media/excel-source-data.jpg)

## <a name="heres-the-sql-server-destination-database-for-this-example"></a>この例の SQL Server 変換先データベースを次に示します
ここで (で SQL Server Management Studio) は、SQL Server 変換先データベースにしようとしているソース データをコピーします。 コピー先のテーブルがない - するテーブルの作成ウィザードを使用する予定です。

![SQL Server 変換先のデータベース](../../integration-services/import-export-data/media/sql-server-destination-database.jpg)

## <a name="step-1---start-the-wizard"></a>手順 1 - ウィザードを開始します
Windows [スタート] メニュー上の Microsoft SQL Server 2016 グループからは、ウィザードを起動します。

![ウィザードを開始します。](../../integration-services/import-export-data/media/start-wizard.jpg)

> [!NOTE]
> この例では、インストールされている Microsoft Office の 32 ビット バージョンがあるため、32 ビットのウィザードを選択します。 その結果、Excel への接続に、32 ビット データ プロバイダーを使用する必要があります。 その他の多くのデータ ソースは、通常 64 ビットのウィザードを選択できます。
>
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するのには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのインストールのみです。

詳細については、「 [Start the SQL Server Import and Export Wizard](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)」(SQL Server インポートおよびエクスポート ウィザードを開始する) を参照してください。

## <a name="step-2---view-the-welcome-page"></a>手順 2 - [ようこそ] ページを表示
ウィザードの最初のページは、**ようこそ**ページ。 

おそらくしたくない、ようにしてください をクリックしては、このページを参照してください**もう一度この開始ページを表示しない**です。

![ウィザードへようこそ](../../integration-services/import-export-data/media/welcome-to-the-wizard.jpg)

## <a name="step-3---pick-excel-as-your-data-source"></a>手順 3 - データ ソースとして選択 Excel
次のページで**データ ソースを選択**、データ ソースとして Microsoft Excel を選択します。 Excel ファイルを参照します。 最後に、ファイルの作成に使用した Excel のバージョンを指定します。

![Excel データ ソースを選択します。](../../integration-services/import-export-data/media/choose-the-excel-data-source.jpg)

Excel への接続に関する詳細については、次を参照してください。 [Excel データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)です。 ウィザードのこのページの詳細については、次を参照してください。[データ ソースを選択](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)です。

## <a name="step-4---pick-sql-server-as-your-destination"></a>手順 4 - 先として SQL Server の選択
次のページで**変換先の選択**、Microsoft SQL Server を選択するように選択することによって、データ プロバイダーのいずれかの一覧でを変換先は SQL Server に接続します。 選択したこの例では、 **.Net Framework Data Provider for SQL Server**です。

ページには、プロバイダーのプロパティの一覧が表示されます。 これらの多くは、悪意のある名前と不明な設定です。 幸いにも、エンタープライズ データベースに接続するに通常必要があるのみの 3 種類の情報を提供します。 その他の設定の既定値は無視できます。

|必要な情報|.Net framework Data Provider for SQL Server プロパティ|
|---|---|
|サーバー名|**[データ ソース]**|
|認証 (ログイン) の情報|**統合セキュリティ**; または**ユーザー ID**と**パスワード**<br/>サーバー上のデータベースのドロップダウン リストを表示する場合は、まず、有効なログイン情報を提供する必要があります。|
|データベース名|**初期カタログ**|

![SQL Server 変換先を選択します。](../../integration-services/import-export-data/media/choose-the-sql-server-destination.jpg)

SQL Server への接続に関する詳細については、次を参照してください。 [SQL Server データ ソースへの接続](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)です。 ウィザードのこのページの詳細については、次を参照してください。[先選択](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)です。

## <a name="step-5---copy-a-table-instead-of-writing-a-query"></a>手順 5 - クエリを記述する代わりにテーブルをコピーします。
次のページで**テーブルのコピーを指定またはクエリ**、ソース データのテーブル全体をコピーすることを指定します。 コピーするデータを選択する SQL 言語でクエリを記述したくないです。

![テーブルをコピーするよう指定します。](../../integration-services/import-export-data/media/specify-to-copy-a-table.jpg)

ウィザードのこのページの詳細については、次を参照してください。[テーブルのコピーを指定またはクエリ](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)です。

## <a name="step-6---pick-the-table-to-copy"></a>手順 6 - コピー先テーブルの選択
次のページで**ソース テーブルおよびビュー**、テーブルまたはデータ ソースからコピーするテーブルを選択します。 各選択したソース テーブルを新規または既存のコピー先のテーブルにマップします。

この例では既定では、ウィザードがマップされている、 **WizardWalkthrough$**内のワークシート、**ソース**を SQL Server 変換先に同じ名前を持つ新しいテーブルの列です。 (Excel ブックのみを含む 1 つのワークシートです。)
-   ソース テーブルの名前にドル記号 ($) では、Excel ワークシートを示します。 (名前付き範囲は Excel 内で表されるその名前だけです。)
-   バクダンを変換先テーブルのアイコンには、ウィザードが新しいレプリケーション先テーブルを作成しようとしていることを示します。

![(この名前を変更するには) の前に、のテーブルを選択します。](../../integration-services/import-export-data/media/select-the-table-before-renaming.jpg)

おそらくを削除する、ドル記号 ($) 新しいレプリケーション先テーブルの名前から。

![(この名前を変更するには) した後、テーブルを選択します。](../../integration-services/import-export-data/media/select-the-table-after-renaming.jpg)

ウィザードのこのページの詳細については、次を参照してください。 [ソース テーブルおよびビュー](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)です。

## <a name="optional-step-7---review-the-column-mappings"></a>省略可能な手順 7 - 列マッピングを確認します。
ままにする前に、 **ソース テーブルおよびビュー**  ページで、必要に応じてクリックし、**マッピングの編集**を開く ボタン、**列マッピング** ダイアログ ボックス。 ここで、**マッピング**テーブル ソース ワークシート内の列を新しいレプリケーション先テーブル内の列にマップするウィザードを移動する方法を参照してください。

![列マッピングの表示](../../integration-services/import-export-data/media/view-column-mappings.jpg)

ウィザードのこのページの詳細については、次を参照してください。[列マッピング](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)です。

## <a name="optional-step-8---review-the-create-table-statement"></a>省略可能な手順 8 - CREATE TABLE ステートメントを確認します。
中に、**列マッピング** ダイアログ ボックスが開いて、必要に応じてクリックし、 **SQL の編集**を開く ボタン、**テーブル作成 SQL ステートメント** ダイアログ ボックス。 ここでは、 **CREATE TABLE**を新しいレプリケーション先テーブルを作成するウィザードで生成されるステートメントです。 通常、ステートメントを変更する必要はありません。

![ビューの CREATE TABLE ステートメント](../../integration-services/import-export-data/media/view-create-table-statement.jpg)

ウィザードのこのページの詳細については、次を参照してください。[テーブル作成 SQL ステートメント](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)です。

## <a name="optional-step-9---preview-the-data-to-copy"></a>省略可能な手順 9 - プレビュー データをコピーするには
クリックした後**ok**を閉じる、**テーブル作成 SQL ステートメント** ダイアログ ボックスの  **ok**を閉じます、**列マッピング**でバックアップするダイアログ ボックスで、 **ソース テーブルおよびビュー**ページ。 必要に応じてクリックし、**プレビュー**データのサンプルを表示するボタンをウィザードは、コピーする予定です。 この例では、[ok] を検索します。

![コピーするデータのプレビュー](../../integration-services/import-export-data/media/preview-data-to-copy.jpg)

ウィザードのこのページの詳細については、次を参照してください。[データのプレビュー](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)です。

## <a name="step-10---yes-you-want-to-run-the-import-export-operation"></a>手順 10 - を [はい]、インポートとエクスポート操作を実行します。
次のページで**の保存とパッケージの実行**のままにする**をすぐに実行**データをコピー をクリックするとすぐに有効になっている**完了**次のページです。 をクリックして、次のページをスキップするか**完了**上、**の保存とパッケージの実行**ページ。

![パッケージを実行します。](../../integration-services/import-export-data/media/run-the-package.jpg)

ウィザードのこのページの詳細については、次を参照してください。[パッケージの実行を保存して](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)です。

## <a name="step-11---finish-the-wizard-and-run-the-import-export-operation"></a>手順 11 - ウィザードを終了し、インポートとエクスポート操作を実行
をクリックした場合**次へ**の代わりに**完了**上、**の保存とパッケージの実行** ページで、次のページで、**ウィザードを完了**、新機能ウィザードで行われる処理の概要を参照してください。 をクリックして**完了**インポートとエクスポート操作を実行します。

![ウィザードの完了](../../integration-services/import-export-data/media/complete-the-wizard.jpg)

ウィザードのこのページの詳細については、次を参照してください。[ウィザードを完了](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)です。

## <a name="step-12---review-what-the-wizard-did"></a>手順 12 - ウィザードが何を確認
最後のページでは、ウィザードの各タスクの終了を観察し、結果を確認します。 強調表示された行は、ウィザードが正常にデータをコピーすることを示します。 完了したら!

![ウィザードが成功しました](../../integration-services/import-export-data/media/the-wizard-succeeded.jpg)

ウィザードのこのページの詳細については、次を参照してください。[を実行する操作](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md)です。

## <a name="heres-the-new-table-of-data-copied-to-sql-server"></a>SQL Server にコピーするデータの新しいテーブルを次に示します
ここで (SQL Server Management Studio) では、ウィザードで SQL Server で作成された新しいレプリケーション先テーブルを参照します。

![SQL Server にコピーするデータ](../../integration-services/import-export-data/media/data-copied-to-sql-server.jpg)

ここで (SSMS) でもう一度には、ウィザードは、SQL Server にコピーするデータを表示します。

![SQL Server 2 にコピーするデータ](../../integration-services/import-export-data/media/data-copied-to-sql-server-2.jpg)

## <a name="learn-more"></a>詳細情報  
ウィザードのしくみについて説明します。
-   **ウィザードの詳細についてを説明します。** ウィザードの概要をお探しの場合は、「 [SQL Server でサポートされるインポートとエクスポートのデータ ソース](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。

-   **ウィザードの手順について説明します。** ウィザードの手順についての情報を探している場合は、ここに一覧から目的のページを選択[、SQL Server インポートおよびエクスポート ウィザードの手順を](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md)です。 ウィザードの各ページ用のドキュメントの別のページもあります。

-   **データ ソースおよび変換先に接続する方法を説明します。** データに接続する方法についての情報を探している場合は、ここに一覧から、ページを選択[、SQL Server インポートおよびエクスポート ウィザードでデータ ソースへの接続](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md)です。 いくつかの一般的に使用されるデータ ソースごとにドキュメントの別のページがあります。



