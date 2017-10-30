---
title: "SQL Server インポートおよびエクスポート ウィザードの手順 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 816fb1bd-7bb9-450d-ad65-e4c2d02eaff8
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 22d1f4b78fadab6d7b6659104b54a564f11da308
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="steps-in-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードの手順
このトピックでは、一連のインポートおよび SQL Server インポートおよびエクスポート ウィザードを使用してデータをエクスポートするための手順について説明します。 また、各ページについて説明するドキュメントまたはウィザードに表示 ダイアログ ボックスの個々 のページへのリンクも含まれます。

このトピックの内容についてのみ説明します、**手順**ウィザード。 他のものを探しの場合は、次を参照してください。[関連のタスクおよびコンテンツ](#related)です。

## <a name="steps-for-importing-and-exporting-data"></a>インポートして、データをエクスポートするための手順  
 次の表に、データのインポートとエクスポートを行うための手順と、ウィザードの該当ページを示します。 オプションに応じて、ウィザードで選択した、一般的にこれらすべてのページを表示されません。  

一般的なセッションを表示するいくつかの画面で簡単に説明を見てこの単純なエンド ツー エンドの例の 1 ページに[インポートおよびエクスポート ウィザードのこの簡単な例の概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)です。

|手順|ウィザード ページ|  
|----------|------------------|  
|**ようこそ**<br />このページで必要な操作はありません。|[SQL Server インポートおよびエクスポート ウィザードへようこそ](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)|  
|データの変換元**を選択します**。|[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)|  
|データの**変換先を選択します**。|[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)|  
|**変換先を構成**です。 (省略可能な手順)<br /><br /> - 新しい変換先データベースを作成します。<br />- データをテキスト ファイルにコピーする場合は、追加設定を構成します。|[データベースを作成します。](../../integration-services/import-export-data/create-database-sql-server-import-and-export-wizard.md)<br /><br />[フラット ファイル変換先を構成します。](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)|  
|**コピーする内容を指定します。**|[テーブルのコピーまたはクエリを指定します。](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)<br /><br />[ソース テーブルとビューを選択します。](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)<br /><br />[ソース クエリを指定します。](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)|  
|**コピー操作を構成する**です。 (省略可能な手順)<br /><br /> - 新しい変換先テーブルを作成します。<br />-ウィザードがソースと選択した変換先の間のデータ型にマップする方法を知らない場合の対処方法を決定します。<br />- 変換元と変換先の間の列マッピングを見直します。<br />- 変換元と変換先の間のデータ型変換に関する問題を処理します。<br />- コピーされるデータを見直します。|[テーブル作成 SQL ステートメント](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md)<br /><br />[変換の確認を伴わない型を変換します。](../../integration-services/import-export-data/convert-types-without-conversion-checking-sql-server-import-and-export-wizard.md)<br /><br />[列マッピング](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)<br /><br />[データ型マッピングを確認します。](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)<br /><br />[列の変換の詳細 ダイアログ ボックス](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md)<br /><br />[プレビュー データ ダイアログ ボックス](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)|  
|**データをコピーします。**<br /><br /> 必要に応じて、設定を SQL Server Integration Services (SSIS) パッケージとして保存します。|[保存し、パッケージの実行](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)<br /><br />[SSIS パッケージの保存](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)<br /><br />[ウィザードを完了します。](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)<br /><br />[操作を実行します。](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md)|  

> [!TIP]
> ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。

## <a name="related"></a>関連のタスクとコンテンツ  
その他の基本的な作業のとおりです。
-   **ウィザードのしくみの簡単な例を参照してください。**

    -   **スクリーン ショットを参照する場合は。** 1 つのページ - この単純なエンド ツー エンドの例を見て[インポートおよびエクスポート ウィザードのこの簡単な例の概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)です。

    -   **ビデオを視聴する場合は。** ウィザードを示し、明確に説明された YouTube かつ簡単にデータを Excel にエクスポートする方法の 4 分のビデオ[、SQL Server インポートおよびエクスポート ウィザードを Excel にエクスポートするを使用して](https://go.microsoft.com/fwlink/?linkid=829049)です。

-   **ウィザードのしくみについて説明します。**

    -   **ウィザードの詳細についてを説明します。** ウィザードの概要をお探しの場合は、「 [SQL Server でサポートされるインポートとエクスポートのデータ ソース](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。

    -   **データ ソースおよび変換先に接続する方法を説明します。** データに接続する方法についての情報を探している場合は、ここに一覧から、ページを選択[、SQL Server インポートおよびエクスポート ウィザードでデータ ソースへの接続](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md)です。 いくつかの一般的に使用されるデータ ソースごとにドキュメントの別のページがあります。 

-   **ウィザードを起動します。** ウィザードを実行する準備が整い、開始方法について知りたい場合は、「[SQL Server インポートおよびエクスポート ウィザードを起動する](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)」を参照してください。

-     **ウィザードを取得します。** ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「 [SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。



