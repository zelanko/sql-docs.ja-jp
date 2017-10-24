---
title: "SQL Server インポートおよびエクスポート ウィザードでデータ インポートおよびエクスポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 160
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 6cd388215de02072522011b149a9cecc3239b64c
ms.contentlocale: ja-jp
ms.lasthandoff: 10/18/2017

---
# <a name="import-and-export-data-with-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードを使用してデータをインポートおよびエクスポートする

 > SQL Server の以前のバージョンに関連するコンテンツでは、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](https://msdn.microsoft.com/en-US/library/ms140052(SQL.120).aspx)です。

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、変換元から変換先にデータをコピーするための単純な方法です。 この概要では、ウィザードは、ソースと変換先として使用できるデータ ソースと、ウィザードを実行する必要があります。 アクセス許可について説明します。

## <a name="get-the-wizard"></a>ウィザードを取得します。
ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「 [SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。

## <a name="what-happens-when-i-run-the-wizard"></a>新機能は、ウィザードを実行するとどうなりますか。
-    **手順の一覧を参照してください。** ウィザードの手順については、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードの手順を](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md)です。 ウィザードの各ページ用のドキュメントの別のページもあります。  
    \- または \-
-   **例を参照してください。** 一般的なセッションを表示するいくつかの画面で簡単に説明を見てこの簡単な例の 1 ページに[インポートおよびエクスポート ウィザードのこの簡単な例の概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)です。  

##  <a name="wizardSources"></a>どのようなソースと変換先を使用できるか。  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードは、次の表に、データ ソースとの間に、データにコピーできます。 これらのデータ ソースの一部に接続するには、ダウンロードして追加のファイルをインストールする必要があります。
 
| データ ソース | 追加ファイルをダウンロードする必要があるかどうか |
|-------------|-----------------------------------------|
|**エンタープライズ データベース**<br/>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Oracle、DB2、およびその他のユーザーです。|SQL Server または SQL Server Data Tools (SSDT) のインストールへの接続に必要なファイル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 SSDT は、Oracle または IBM DB2 などその他の企業データベースに接続する必要のあるすべてのファイルをインストールしません。<br/><br/>エンタープライズ データベースに接続するには、通常存在する必要が 2 つの操作。<br/><br/>1.**クライアント ソフトウェア**です。 エンタープライズ データベース システム用のクライアント ソフトウェアを既にインストールしている場合、通常は接続するために必要なファイルは用意されています。 クライアント ソフトウェアをインストールしていない場合は、ライセンス コピーのインストール方法をデータベース管理者に問い合わせください。<br/><br/>2.**ドライバーまたはプロバイダー**です。 Microsoft では、ドライバーと Oracle への接続にプロバイダーをインストールします。 IBM DB2 に接続するに Microsoft® OLEDB Provider for DB2 v5.0 の取得から Microsoft SQL Server、 [Microsoft SQL Server 2016 Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)です。<br/><br/>詳細については、次を参照してください。 [SQL Server データ ソースへの接続](connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)または[Oracle データ ソースへの接続](connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)です。|
|**テキスト ファイル**(フラット ファイル)|追加ファイルは必要ありません。<br/><br/>詳細については、次を参照してください。[フラット ファイル データ ソースへの接続](connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)です。|
|**Microsoft Excel ファイルと Microsoft Access ファイル**|Microsoft Office は、Excel と Access のファイルにデータ ソースとして接続するために必要なすべてのファイルはインストールしません。 次のダウンロード - を入手する[Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)です。<br/><br/>詳細については、次を参照してください。 [Excel データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)または[Access データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)です。|
|**Azure データ ソース**<br/>現在 Azure BLOB ストレージのみ。|SQL Server Data Tools には、データ ソースとしての Azure Blob ストレージへの接続に必要なファイルをインストールしないでください。 次のダウンロードを取得してください - [Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492)。<br/><br/>詳細については、次を参照してください。 [Azure ブログの記憶域への接続](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)です。|
|**オープン ソース データベース**<br/>PostgreSQL、MySql、およびその他のユーザーです。|これらのデータ ソースに接続するには、追加のファイルをダウンロードする必要があります。<br/><br/>- **PostgreSQL**を参照してください[PostgreSQL データ ソースへの接続](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)です。<br/>- **MySql**を参照してください[MySQL データ ソースへの接続](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)です。|
|**他のデータ ソースのドライバーまたはプロバイダーを使用**|通常、次の種類のデータ ソースに接続するために追加ファイルをダウンロードする必要があります。<br/><br/>- **ODBC ドライバー** を使用できるソース。 詳細については、次を参照してください。 [ODBC データ ソースへの接続](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)です。<br/>- **.Net Framework Data Provider** を使用できるソース。<br/>- **OLE DB プロバイダー** を使用できるソース。<br/><br/>他のデータ ソースの元とコピー先の機能を提供するサード パーティ コンポーネントが場合がありますとして販売されているアドオン製品用 SQL Server Integration Services (SSIS)。|

## <a name="how-do-i-connect-to-my-data"></a>データに接続する方法は?
一般的に使用されるデータ ソースに接続する方法の詳細については、次のページのいずれかを参照してください。
-   [SQL Server への接続](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Oracle への接続](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [フラット ファイル (テキスト ファイル) への接続します。](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Excel への接続します。](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [アクセスに接続します。](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Azure Blob ストレージへの接続します。](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [ODBC を接続します。](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [PostgreSQL への接続します。](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [MySQL への接続します。](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)


詳細については、ここに記載されていないデータ ソースに接続する方法は、次を参照してください。[この接続文字列参照には](https://www.connectionstrings.com/)します。 このサード パーティのサイトには、サンプルの接続文字列とデータ プロバイダーの詳細と必要な接続情報が含まれています。

## <a name="what-permissions-do-i-need"></a>どのようなアクセス許可が必要ですか。  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを実行するには、少なくとも次の権限が必要です。 データ ソースと変換先で既に作業をしている場合は、必要な権限を既に持っている可能性があります。
  
|実行するには権限が必要な操作|これらの特定のアクセス許可が必要な SQL Server に接続する場合 |  
|-------------------------|----------------------------------------------------|  
|変換元および変換先のデータベースまたはファイル共有に接続する。|サーバーおよびデータベースへのログイン権限。|  
|変換元のデータベースまたはファイルからデータをエクスポートする、または読み取る。|変換元のテーブルおよびビューに対する SELECT 権限。|  
|変換先のデータベースまたはファイルにデータをインポートする、または書き込む。|変換先のテーブルに対する INSERT 権限。|  
|変換先データベースまたはファイルを作成する (該当する場合)。|CREATE DATABASE 権限または CREATE TABLE 権限。|  
|ウィザードによって作成された SSIS パッケージを保存する (該当する場合)。|パッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に保存する場合は、 **msdb** データベースにパッケージを保存するのに十分な権限。|  
  
## <a name="get-help-while-the-wizard-is-running"></a>ウィザードの実行中にヘルプを得る
> [!TIP]
> ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。   
  
##  <a name="wizardSSIS"></a> ウィザードは SQL Server Integration Services (SSIS) を使用する  
 ウィザードは SQL Server Integration Services (SSIS) を使用してデータをコピーします。 SSIS は、データの抽出、変換、および読み込み (ETL) を行うツールです。 ウィザードの各ページでは、SSIS の言語の一部を使用します。
  
 SSIS での基本単位は **パッケージ**です。 ウィザードのページを進みながらオプションを指定すると、SSIS パッケージがメモリに作成されます。    
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition 以降をインストールしている場合は、ウィザードの最後に、必要に応じて SSIS パッケージを保存することもできます。 後でパッケージを再使用したり、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを使用してタスク、変換、イベント ドリブン ロジックを追加することでパッケージを拡張したりできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、データを変換元から変換先にコピーする基本的な [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成するための最も簡単な方法です。

詳細については、「 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)」を参照してください。

## <a name="whats-next"></a>次の課題  
 ウィザードを開始します。 詳細については、「 [Start the SQL Server Import and Export Wizard](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)」(SQL Server インポートおよびエクスポート ウィザードを開始する) を参照してください。  

## <a name="see-also"></a>参照
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)  
[SQL Server インポートおよびエクスポート ウィザードのデータ型マッピング](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)



