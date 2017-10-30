---
title: "データ ソース (SQL Server インポートおよびエクスポート ウィザード) を選択 |Microsoft ドキュメント"
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
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 80d35cb294fd900611c73ca37bba2a66baef0767
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>[データ ソースの選択]\(SQL Server インポートおよびエクスポート ウィザード)
  [ようこそ] ページの後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードに **[データ ソースを選ぶ]**が表示されます。 このページでは、データ ソースおよびデータに接続する方法についての情報を指定します。
  
使用できるデータ ソースの詳細については、「 [どのようなデータ ソースと変換先を使用できるでしょうか。](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)」を参照してください。

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>[データ ソースの選択] ページのスクリーン ショット 
次のスクリーンショットは、ウィザードの **[データ ソースの選択]** ページの最初の部分を示しています。 ページの残りの部分には、可変個のここで選択したデータ ソースに依存するオプションがあります。

![ソースの選択](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>[データ ソースを選ぶ]
 **データ ソース**  
データ ソースを指定するには、ソースに接続することができるデータ プロバイダーを選択します。

-   **必要なデータ プロバイダーは通常、その名前から明らかな**プロバイダーの名前通常含まれているためデータ ソースの名前など、*フラット ファイル*ソース、Microsoft *Excel*、Microsoft*アクセス*、.Net Framework Data Provider for *SqlServer*、.Net Framework Data Provider for *Oracle*です。

-   **データ ソースの ODBC ドライバーがあるかどうかは**、選択、.Net Framework Data Provider for ODBC です。 ドライバー固有の情報を入力します。 ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 .Net Framework Data Provider for ODBC は ODBC ドライバーをラップするラッパーとして機能します。 詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

-   **データ ソースに使用できるプロバイダーが複数存在する可能性があります。** 通常、ソースで使用できる任意のプロバイダーを選択できます。 例については、Microsoft に接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、SQL Server または SQL Server ODBC ドライバーの .NET Framework データ プロバイダーを使用することができます。 (その他のプロバイダーは、一覧にもまだが現在サポートされていません)。 

## <a name="my-data-source-isnt-in-the-list"></a>データ ソースは、一覧ではありません。
-   **データ プロバイダーをダウンロードする必要があります**Microsoft またはサード パーティからです。 使用できるデータ プロバイダーの一覧、**データソース**一覧には、コンピューターにインストールされているプロバイダーのみが含まれています。 使用できるデータ ソースの詳細については、「 [どのようなデータ ソースと変換先を使用できるでしょうか。](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)」を参照してください。

-   **データ ソースの ODBC ドライバーがあるか。** ODBC ドライバーは、データ ソースのドロップダウン リストに記載されていません。 データ ソース、ODBC ドライバーがあれば、選択、.Net Framework Data Provider for ODBC です。 ドライバー固有の情報を入力します。 .Net Framework Data Provider for ODBC は ODBC ドライバーをラップするラッパーとして機能します。 詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。

-   **64 ビットおよび 32 ビットのプロバイダー。** 64 ビットのウィザードを実行している場合は、データ ソースが表示されません、32 ビット プロバイダーのみがインストールされているため、その逆です。

> [!NOTE]
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するのには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのインストールのみです。

## <a name="after-you-choose-a-data-source"></a>データ ソースの選択後
残りの部分のデータ ソースを選択した後、**データ ソースを選択**ページには、可変個のオプションを選択するデータ プロバイダーによって異なります。

一般的に使用されるデータ ソースに接続するには、次のページのいずれかを参照してください。
-   [SQL Server に接続します。](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Oracle への接続します。](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [フラット ファイル (テキスト ファイル) への接続します。](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Excel への接続します。](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [アクセスに接続します。](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [ODBC を接続します。](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Azure Blob ストレージへの接続します。](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [PostgreSQL への接続します。](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [MySQL への接続します。](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

詳細については、ここに記載されていないデータ ソースに接続する方法は、次を参照してください。[この接続文字列参照には](https://www.connectionstrings.com/)します。 このサード パーティのサイトには、サンプルの接続文字列とデータ プロバイダーの詳細と必要な接続情報が含まれています。

## <a name="whats-next"></a>次の操作  
 データ ソースとデータへの接続方法を指定したら、 **[変換先の選択]**ページに進みます。 このページでは、データの変換先およびデータに接続する方法についての情報を指定します。 詳細については、「 [[変換先の選択] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)」をご覧ください。
 
## <a name="see-also"></a>参照
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



