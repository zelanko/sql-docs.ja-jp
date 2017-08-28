---
title: "(SQL Server インポートおよびエクスポート ウィザード) 変換先の選択 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 104
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 4ff3c7c8413bd6b535e1c5f95e2a7b06b397c053
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>[変換先の選択] (SQL Server インポートおよびエクスポート ウィザード)
 データ ソースとデータへの接続方法を指定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードには、 **[変換先の選択]**が表示されます。 このページでは、データの変換先およびデータに接続する方法についての情報を指定します。
  
使用できるデータの変換先の詳細については、「 [使用できるデータ ソースと変換先](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)」を参照してください。 

## <a name="screen-shot-of-the-destination-page"></a>[変換先] ページのスクリーン ショット
次のスクリーンショットは、ウィザードの **[変換先の選択]** ページの最初の部分を示しています。 ページの残りの部分には、さまざまな変数、変換先は、ここを選択するのに依存するオプションがあります。

![変換先の選択](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>[変換先の選択]
 **変換先**  
 変換先を指定するには、変換先にデータをインポートすることができるデータ プロバイダーを選択します。
 
-   **必要なデータ プロバイダーは通常、その名前から明らかな**プロバイダーの名前通常含まれているため、変換先 - の名前など、*フラット ファイル*変換先、Microsoft *Excel*、Microsoft*アクセス*、.Net Framework Data Provider for *SqlServer*、.Net Framework Data Provider for *Oracle*です。

-   **変換先の ODBC ドライバーがある場合**、選択、.Net Framework Data Provider for ODBC です。 ドライバー固有の情報を入力します。 ODBC ドライバーは、変換先のドロップダウン リストに記載されていません。 .Net Framework Data Provider for ODBC は ODBC ドライバーをラップするラッパーとして機能します。 詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

-   **変換先として使用できるプロバイダーが複数存在する可能性があります。** 通常、変換先で使用できる任意のプロバイダーを選択できます。 例については、Microsoft に接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、SQL Server または SQL Server ODBC ドライバーの .NET Framework データ プロバイダーを使用することができます。 (その他のプロバイダーは、一覧にもまだが現在サポートされていません)。 

## <a name="my-destination-isnt-in-the-list"></a>目的地は、一覧ではありません。
-   **データ プロバイダーをダウンロードする必要があります**Microsoft またはサード パーティからです。 使用できるデータ プロバイダーの一覧、**先**一覧には、コンピューターにインストールされているプロバイダーのみが含まれています。 詳細については、変換先を使用することができますが、次を参照してください。[どのようなデータ ソースと変換先を使用できるか。](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **変換先の ODBC ドライバーがあるか。** ODBC ドライバーは、変換先のドロップダウン リストに記載されていません。 変換先の ODBC ドライバーがあれば、選択、.Net Framework Data Provider for ODBC です。 ドライバー固有の情報を入力します。 .Net Framework Data Provider for ODBC は ODBC ドライバーをラップするラッパーとして機能します。 詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

-   **64 ビットおよび 32 ビットのプロバイダー。** 64 ビットのウィザードを実行している場合は、変換先が表示されません、32 ビット プロバイダーのみがインストールされているため、その逆です。

> [!NOTE]
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するのには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのインストールのみです。

## <a name="after-you-choose-a-destination"></a>変換先の選択後
変換先の残りの部分を選択した後、**変換先を選択**ページには、可変個のオプションを選択するデータ プロバイダーによって異なります。

一般的に使用される変換先に接続するには、次のページのいずれかを参照してください。
-   [SQL Server に接続します。](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Oracle への接続します。](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [フラット ファイル (テキスト ファイル) への接続します。](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Excel への接続します。](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [アクセスに接続します。](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [ODBC を接続します。](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Azure Blob ストレージへの接続します。](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [PostgreSQL への接続します。](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [MySQL への接続します。](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

詳細については、ここに記載されていない変換先に接続する方法は、次を参照してください。[この接続文字列参照には](https://www.connectionstrings.com/)します。 このサード パーティのサイトには、サンプルの接続文字列とデータ プロバイダーの詳細と必要な接続情報が含まれています。

## <a name="whats-next"></a>次の操作  
 データの変換先とデータへの接続方法を指定した後、次のページは、 **[テーブルのコピーまたはクエリの指定]**です。 このページでは、テーブル全体をコピーするか、特定の行のみをコピーするかを指定します。 詳細については、「 [テーブルのコピーまたはクエリの指定](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)」を参照してください。  

## <a name="see-also"></a>参照
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



