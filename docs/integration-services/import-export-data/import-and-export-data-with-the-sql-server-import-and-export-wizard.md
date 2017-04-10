---
title: "SQL Server インポートおよびエクスポート ウィザードを使用してデータをインポートおよびエクスポートする | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データのエクスポート"
  - "マッピング ファイル [Integration Services]"
  - "SQL Server インポートおよびエクスポート ウィザード"
  - "SSIS パッケージ, 作成"
  - "パッケージ [Integration Services], コピー"
  - "Integration Services パッケージ, 作成"
  - "パッケージ [Integration Services], 作成"
  - "SQL Server Integration Services パッケージ, 作成"
  - "インポートおよびエクスポート ウィザード"
  - "データのコピー [Integration Services]"
  - "データのインポート, SSIS パッケージ"
  - "ソース [Integration Services], データのコピー"
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 160
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 134
---
# SQL Server インポートおよびエクスポート ウィザードを使用してデータをインポートおよびエクスポートする
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、変換元から変換先にデータをコピーするための単純な方法です。 ウィザードを実行するために SQL Server をインストールする必要はありません。 この概要では、ウィザードを利用してデータをインポートまたはエクスポートできるデータ ソースとウィザードの実行に必要なアクセス許可について説明します。

このトピックでは、ウィザードの**概要**のみを説明しています。
-   ウィザードを実行する準備が整い、開始方法について知りたい場合は、「[SQL Server インポートおよびエクスポート ウィザードを起動する](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)」を参照してください。
-   ウィザードの手順に関する情報をお探しの場合、コンテンツ ナビゲーション メニューで必要なページを選択してください。 ウィザードのページごとに別のドキュメント ページがあります。 または、ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。

**ウィザードを取得します。** ウィザードを実行する必要はあるが、コンピューターに [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールしていない場合は、SQL Server Data Tools (SSDT) をインストールすることで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードをインストールできます。 詳細については、「[SQL Server Data Tools (SSDT) のダウンロード](https://msdn.microsoft.com/library/mt204009.aspx)」を参照してください。

> [!TIP] 複数のデータベース、またはテーブルとビュー以外のデータベース オブジェクトをコピーする必要がある場合は、インポートおよびエクスポート ウィザードではなく、データベース コピー ウィザードを使用します。 詳細については、「[データベース コピー ウィザードの使用](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。

## <a name="example-of-a-common-use-case---exporting-data-to-excel-video"></a>一般的な使用事例 - データを Excel にエクスポートする (ビデオ)  
ウィザードの一般的な用途は、データを Excel にエクスポートすることです。 ウィザードを実行し、わかりやすく簡単な手順でエクスポートする方法を説明した YouTube の 4 分間のビデオ「[Using the SQL Server Import and Export Wizard to Export to Excel](https://go.microsoft.com/fwlink/?linkid=829049)」(SQL Server インポートおよびエクスポート ウィザードを使用して Excel にエクスポートする) をご覧ください。

##  <a name="a-namewizardsourcesa-what-data-sources-and-destinations-can-i-use"></a><a name="wizardSources"></a> 使用できるデータ ソースと変換先  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、次のデータ ソース間でデータをコピーできます。 一部のデータ ソースを使用するには、追加ファイルをダウンロードしてインストールする必要があります。

| データ ソース | 追加ファイルをダウンロードする必要があるかどうか |
|-------------|-----------------------------------------|
|**エンタープライズ データベース**<br/>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Oracle など。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と Oracle に接続するために必要なファイルはインストールされますが、IBM DB2 や Informix などのエンタープライズ データベースに接続するために必要なファイルはインストールされません。<br/>- エンタープライズ データベース システム用のクライアント ソフトウェアを既にインストールしている場合、通常は接続するために必要なファイルは用意されています。<br/>- クライアント ソフトウェアをインストールしていない場合は、ライセンス コピーのインストール方法をデータベース管理者に問い合わせください。|
|**オープン ソース データベース**<br/>MySql、PostgreSQL、SQLite など。|これらのデータ ソースに接続するには、追加ファイルをダウンロードする必要があります。<br/><br/>- **MySql** については、「[MySQL Connector](http://dev.mysql.com/downloads/connector/)」を参照してください。<br/>- **PostgreSQL** については、「[psqlODBC - PostgreSQL ODBC driver](https://odbc.postgresql.org/)」 (psqlODBC - PostgreSQL ODBC ドライバー) と、[Npgsql - .NET Data Provider for PostgreSQL](http://www.npgsql.org/) などのサードパーティ製品を参照してください。<br/>- **SQLite** については、オンラインで利用できるさまざまなオープン ソース プロバイダーとドライバーから選択してください。|
|**テキスト ファイル** (フラット ファイル)。|追加ファイルは必要ありません。|
|**Microsoft Excel ファイルと Microsoft Access ファイル**|Microsoft Office は、Excel と Access のファイルにデータ ソースとして接続するために必要なすべてのファイルはインストールしません。 次のダウンロードを取得してください - [Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)。|
|**Azure データ ソース**<br/>現在 Azure BLOB ストレージのみ。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、Azure BLOB ストレージにデータ ソースとして接続するために必要なファイルはインストールされません。 次のダウンロードを取得してください - [Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492)。|
|**コネクタを使用できるその他のデータ ソース**。|通常、次の種類のデータ ソースに接続するために追加ファイルをダウンロードする必要があります。<br/><br/>- **ODBC ドライバー**を使用できるソース。 ODBC (Open Database Connectivity) 接続は、ウィザードの **[データ ソースの選択]** または **[変換先の選択]** ページで ODBC 用の .Net Framework Provider を選択し、ODBC ドライバーを参照する接続文字列または既存の DSN (データ ソース名) を指定することで実行します。<br/>- **OLE DB プロバイダー**を使用できるソース。<br/>- **.Net Framework Data Provider**を使用できるソース。<br/>- **サードパーティのコンポーネント**が変換元と変換先の機能を提供するその他のデータソース。 通常、これらのサードパーティ製品は、SQL Server Integration Services (SSIS) のアドオン製品として販売されます。|
  
> [!TIP] データ ソースに接続文字列が必要な場合は、サードパーティ サイト「[The Connection Strings Reference](https://www.connectionstrings.com/)」(接続文字列リファレンス) をご覧ください。  
  
## <a name="what-permissions-do-i-need-to-run-the-wizard"></a>ウィザードを実行するために必要な権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを実行するには、少なくとも次の権限が必要です。 データ ソースと変換先で既に作業をしている場合は、必要な権限を既に持っている可能性があります。
  
|実行するには権限が必要な操作|SQL Server に接続している場合に必要な権限 |  
|-------------------------|----------------------------------------------------|  
|変換元および変換先のデータベースまたはファイル共有に接続する。|サーバーおよびデータベースへのログイン権限。|  
|変換元のデータベースまたはファイルからデータをエクスポートする、または読み取る。|変換元のテーブルおよびビューに対する SELECT 権限。|  
|変換先のデータベースまたはファイルにデータをインポートする、または書き込む。|変換先のテーブルに対する INSERT 権限。|  
|変換先データベースまたはファイルを作成する (該当する場合)。|CREATE DATABASE 権限または CREATE TABLE 権限。|  
|ウィザードによって作成された SSIS パッケージを保存する (該当する場合)。|パッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に保存する場合は、**msdb** データベースにパッケージを保存するのに十分な権限。|  
  
##  <a name="a-namewizardssisa-the-wizard-uses-sql-server-integration-services-ssis"></a><a name="wizardSSIS"></a> ウィザードは SQL Server Integration Services (SSIS) を使用する  
 ウィザードは SQL Server Integration Services (SSIS) を使用してデータをコピーします。 SSIS は、データの抽出、変換、および読み込み (ETL) を行うツールです。 ウィザードの各ページでは、SSIS の言語の一部を使用します。
  
 SSIS での基本単位は**パッケージ**です。 ウィザードのページを進みながらオプションを指定すると、SSIS パッケージがメモリに作成されます。    
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition 以降をインストールしている場合は、ウィザードの最後に、必要に応じて SSIS パッケージを保存することもできます。 後でパッケージを再使用したり、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを使用してタスク、変換、イベント ドリブン ロジックを追加することでパッケージを拡張したりできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、データを変換元から変換先にコピーする基本的な [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを作成するための最も簡単な方法です。

詳細については、「[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)」を参照してください。

## <a name="get-help-while-the-wizard-is-running"></a>ウィザードの実行中にヘルプを得る
> [!TIP] ウィザードのページまたはダイアログ ボックスで F1 キーをタップすると、現在のページの文書が表示されます。   
  
## <a name="whats-next"></a>次の課題  
 ウィザードを開始します。 詳細については、「[Start the SQL Server Import and Export Wizard](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)」(SQL Server インポートおよびエクスポート ウィザードを開始する) を参照してください。  
  
## <a name="see-also"></a>参照
[SQL Server インポートおよびエクスポート ウィザードのデータ型マッピング](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
