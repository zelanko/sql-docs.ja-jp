---
title: "[変換先の選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.chooseadestination.f1"
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 104
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 95
---
# [変換先の選択] (SQL Server インポートおよびエクスポート ウィザード)
 データ ソースとデータへの接続方法を指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードには、**[変換先の選択]** が表示されます。 このページでは、データの変換先およびデータに接続する方法についての情報を指定します。
  
使用できるデータの変換先の詳細については、「[使用できるデータ ソースと変換先](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources)」を参照してください。 

## <a name="screen-shot-of-the-destination-page"></a>[変換先] ページのスクリーン ショット
次のスクリーンショットは、ウィザードの **[変換先の選択]** ページの最初の部分を示しています。

![変換先の選択](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>変換先の選択
 **変換先**  
 変換先を指定するには、変換先にデータをインポートすることができるデータ プロバイダーを選択します。 プロバイダーの名前には変換先の名前 (SQL Server、Oracle、フラット ファイル、Excel、Access など) が含まれているため、ほとんどの場合、必要なデータ プロバイダーはプロバイダーの名前から明らかです。
 
**[変換先]** の一覧に表示される、使用できるデータ プロバイダーの一覧は、コンピューターにインストールされているプロバイダーによって異なります。 また、64 ビットと 32 ビットのどちらのウィザードを実行しているかによっても異なります。

変換先として使用できるプロバイダーが複数存在する可能性があります。 通常、変換先で使用できる任意のプロバイダーを選択できます。 たとえば、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、.NET Framework Data Provider for SQL Server、または Microsoft OLE DB Provider for SQL Server を使用できます。
 
場合によっては、最初は汎用的なデータ プロバイダーを選択する必要があります。 たとえば、変換先で ODBC ドライバーを使用している場合は、.NET Framework Data Provider for ODBC を選択します。

変換先によっては、Microsoft またはサード パーティからデータ プロバイダーをダウンロードする必要があります。 使用できるデータの変換先の詳細については、「[使用できるデータ ソースと変換先](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources)」を参照してください。

## <a name="after-you-choose-a-destination"></a>変換先の選択後
変換先を選択した後、**[変換先の選択]** ページ プロパティの残りの部分で指定するオプションの数は、選択したデータ プロバイダーによって異なります。

以降のセクションでは、使用頻度の高い変換先の重要なオプションを一覧表示します。 **[変換先]** ドロップダウン リストに表示される変換先をすべて示しているわけではありません。 追加のオプションおよびその他のプロバイダーについては、プロバイダー固有のマニュアルを参照してください。

> [!TIP] 変換先に接続文字列が必要な場合は、このサードパーティ サイト 「[The Connection Strings Reference](https://www.connectionstrings.com/)」(接続文字列リファレンス) を参照してください。  

## <a name="microsoft-sql-server"></a>Microsoft SQL Server 

変換先として新しい SQL Server データベースを作成する場合は、SQL Server Native Client または Microsoft OLE DB Provider for SQL Server を選択します。 .Net Framework Data Provider for SQL Server を選択すると、新しいデータベースを作成するオプションは使用できません。  

### <a name="connect-to-sql-server-with-sql-server-native-client-or-the-microsoft-ole-db-provider-for-sql-server"></a>SQL Server Native Client または Microsoft OLE DB Provider for SQL Server を使用して SQL Server に接続する  

SQL Server Native Client と Microsoft OLE DB Provider for SQL Server は、同じオプション セットを公開しています。 例として SQL Server Native Client のオプションを次のスクリーン ショットに示します。

![SQL ネイティブ変換先](../../integration-services/import-export-data/media/sql-native-destination.png)

 **サーバー名**  
 変換先サーバーの名前または IP アドレスを入力するか、一覧からサーバーを選択します。  
  
> [!NOTE] 複数のサーバーが配置されたネットワークでは、サーバー名を入力する方が簡単です。 ドロップダウン リストをクリックすると、使用可能なすべてのサーバーがネットワークに照会されるため、時間がかかることがあります。また、目的のサーバー名が検索結果の一覧に表示されない可能性もあります。  
 
 非標準の TCP ポートを指定するには、サーバー名または IP アドレスの後にコンマを入力し、ポート番号を入力します。
 
 **Windows 認証を使用する**  
 データベースへのログインに、ウィザードが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するかどうかを指定します。 推奨されるのは、Windows 認証です。  
  
 **SQL Server 認証を使用する**  
 データベースへのログインに、ウィザードが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するかどうかを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。  
  
 **ユーザー名**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。  
  
 **パスワード**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。  
  
 **データベース**  
 指定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベースの一覧から選択します。  
  
 **更新**  
 **[更新]** をクリックして、利用可能なデータベースの一覧を復元します。  
  
### <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>.NET Framework Data Provider for SQL Server を使用して SQL Server に接続する 

このページでは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオプションがグループ化されて一覧表示されます。 重要なオプションを次に示します。 このプロバイダーを選択したときに一覧表示される追加オプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の変換先データベースに正しく接続するために必須というわけではありません。 

詳細については、「[.NET Framework Data Provider for SQL Server connection strings](https://www.connectionstrings.com/sqlconnection/)」(.NET Framework Data Provider for SQL Server の接続文字列) を参照してください。

![SQL Server 宛先ネットワーク](../../integration-services/import-export-data/media/sql-server-destination-net.png)
  
 **変換先**  
 変換先サーバーの名前または IP アドレスを入力するか、一覧からサーバーを選択します。  
  
> [!NOTE] 複数のサーバーが配置されたネットワークでは、サーバー名を入力する方が簡単です。 ドロップダウン リストをクリックすると、使用可能なすべてのサーバーがネットワークに照会されるため、時間がかかることがあります。また、目的のサーバー名が検索結果の一覧に表示されない可能性もあります。  
 
 非標準の TCP ポートを指定するには、サーバー名または IP アドレスの後にコンマを入力し、ポート番号を入力します。
 
 **初期カタログ**  
 変換先データベースの名前を入力するか、一覧からデータベースを選択します。  
  
 **統合セキュリティ**  
 **True** を指定して Windows 統合認証を使用して接続するか (推奨)、**False** を指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続します。 **False** を指定した場合は、ユーザー ID とパスワードを入力する必要があります。 既定値は **False**です。  
  
 **ユーザー ID**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。  
  
 **パスワード**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。  

## <a name="oracle"></a>Oracle

Oracle への接続には .Net Framework Data Provider for Oracle または Microsoft OLE DB Provider for Oracle を使用します。 次のスクリーン ショットに示す .Net Framework Data Provider for Oracle は簡単に構成できます。

詳細については、「[.NET Framework Data Provider for Oracle connection strings](https://www.connectionstrings.com/net-framework-data-provider-for-oracle/)」(.NET Framework Data Provider for Oracle の接続文字列) または「[Microsoft OLE DB Provider for Oracle connection strings](https://www.connectionstrings.com/microsoft-ole-db-provider-for-oracle-msdaora/)」(Microsoft OLE DB Provider for Oracle の接続文字列) を参照してください。

![Oracle 変換先](../../integration-services/import-export-data/media/oracle-destination.png)

## <a name="odbc-destinations"></a>Oracle 変換先

ODBC ドライバーが提供されている変換先にデータを保存するには、.Net Framework Data Provider for ODBC を選択します。

ODBC 変換先の接続文字列を指定するには、使用する ODBC ドライバーのドキュメントを参照するか、「[The Connection Strings Reference](https://www.connectionstrings.com/)」 (接続文字列リファレンス) で例を探してください。 

例として、SQL Server への ODBC 接続を次のスクリーン ショットに示します。 この例で使用されている接続文字列は次のとおりです。

    Driver={SQL Server};Server=(local);Database=TestData;Trusted_Connection=Yes;

**[ConnectionString]** フィールドに接続文字列を入力すると、ウィザードによって文字列が解析され、個々のプロパティとその値が一覧の **[その他]** セクションに表示されます。

![ODBC 接続の SQL 変換先](../../integration-services/import-export-data/media/odbc-connection-sql-destination.png)

 ## <a name="text-files-flat-files"></a>テキスト ファイル (フラット ファイル)
 
![フラット ファイル変換先](../../integration-services/import-export-data/media/flat-file-destination.png)  

**ファイル名**  
 データを格納するファイルのパスとファイル名を指定します。 または、 **[参照]** をクリックしてファイルを探します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、ファイルを検索します。  
  
 **ロケール**  
 文字の並べ替え順と日時の形式を定義するロケールの ID (LCID) を指定します。  
  
 **Unicode**  
 Unicode を使用するかどうかを示します。 Unicode を使用する場合、コード ページを指定する必要はありません。  
  
 **コード ページ**  
 使用する言語のコード ページを指定します。  
  
 **形式**  
 区切り形式、固定幅形式、または幅合わせしない形式を使用するかどうかを示します。  
  
|値|Description|  
|-----------|-----------------|  
|[区切り記号]|列は区切り記号で区切られます。|  
|[固定幅]|列は固定幅を持ちます。|  
|[幅合わせしない]|幅合わせしないファイルとは、最後の列以外のすべての列が固定幅を持つファイルです。最後の列は、行区切り記号で区切られます。|  
  
 **テキスト修飾子**  
 使用するテキスト修飾子を入力します。 たとえば、各テキスト列を引用符で囲むように指定できます。  
  
 **先頭データ行を列名として使用する**  
 先頭のデータ行に列名を表示するかどうかを指定します。  
 
 ## <a name="microsoft-excel"></a>Microsoft Excel

>  **ビデオ**: ウィザードの一般的な用途は、データを Excel にエクスポートすることです。 YouTube に公開されているこの 4 分間のビデオでは、わかりやすく簡易な手順で実行する方法が説明されています。 「[Using the SQL Server Import and Export Wizard to Export to Excel](https://go.microsoft.com/fwlink/?linkid=829049)」(SQL Server インポートおよびエクスポート ウィザードを使用して Excel にエクスポートする) をご覧ください (このビデオでは [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2012 を使用しています)。

Microsoft Excel ブックへの接続例を次のスクリーン ショットに示します。

![Excel 変換先](../../integration-services/import-export-data/media/excel-destination.png) 
 
 **Excel ファイル パス**  
 データのエクスポート先となるスプレッドシートのパスとファイル名を指定します。 たとえば、ローカル コンピューター上のファイルの場合は **C:\\MyData.xlsx**、ネットワーク共有上のファイルの場合は **\\\\Sales\\Database\\Northwind.xlsx** と指定します。 または、**[参照]** をクリックします。   
  
 **参照**  
 **[ファイルを開く]** ダイアログ ボックスを使用して、ワークシートを検索します。  

> [!NOTE] パスワードで保護された Excel ファイルはウィザードで開くことができません。

 **Excel バージョン**  
変換先のブックで使用される Excel のバージョンを選択します。  

選択したバージョンの Excel に接続するために追加のファイルのダウンロード、インストールが必要になる場合もあります。 詳細については、このページの「[Excel と Access に必要なコンポーネントのダウンロード](Choose%20a%20Data%20Source%20\%28SQL%20Server%20Import%20and%20Export%20Wizard%29.md\#officeDownloads)」を参照してください。

バージョンの指定時に問題が発生する場合 (たとえば、Microsoft Office 365 がインストールされているため、Access 2016 ランタイムをインストールできない場合など)、2016 ではなく 2013 など、旧バージョンでも別のバージョンを指定してみてください。

**先頭行に列名を含める**  
Excel が変換先の場合、このオプションは影響がありません。 変換先に列名がない場合、このオプションが有効でもドライバーは列名を出力しません。 ウィザードの内部処理では、一時的な列見出しとして F1、F2 などが使用されます。
 
## <a name="microsoft-access"></a>Microsoft Access  

Microsoft Access データベースへの接続例を次のスクリーン ショットに示します。

![Access 変換先](../../integration-services/import-export-data/media/access-destination.png)

 **ファイル名**  
 データのエクスポート先となるデータベース ファイルのパスとファイル名を指定します。 たとえば、**C:\MyData.mdb、\\\Sales\Database\Northwind.mdb** などです。 または、**[参照]** をクリックします。
 
 >   [!NOTE] ウィザードは、MDB ファイル形式の Access データベースのみに接続できます、します。MDB ファイル形式です。  
  
 **参照**  
 **[ファイルを開く]** ダイアログ ボックスを使用して、データベース ファイルを検索します。  
  
 **ユーザー名**  
ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のために有効なユーザー名を指定します。  
  
 **パスワード**  
ワークグループの情報ファイルがデータベースに関連付けられている場合は、データベース接続のためにユーザーのパスワードを指定します。

データベースがすべてのユーザーに対して 1 つのパスワードで保護されている場合は、**[データ リンク プロパティ]** ダイアログ ボックスでこの値を指定します。 **[データ リンク プロパティ]** ダイアログ ボックスを開くには、**[詳細設定]** をクリックします。    
  
 **詳細設定**  
**[データ リンク プロパティ]** ダイアログ ボックスで、データベースのパスワードや既定以外のワークグループ情報ファイルなどの詳細なオプションを指定します。  
  
## <a name="a-nameofficedownloadsaget-the-downloads-you-need-for-excel-and-access"></a><a name="officeDownloads"></a>Excel と Access に必要なコンポーネントのダウンロード  
Microsoft Excel および Access データ ソース用の接続コンポーネントがまだインストールされていない場合は、必要に応じてダウンロードします。

以前のバージョンのプログラムで作成したファイルは、新しいバージョンのコンポーネントで開くことができます。 場合によっては、新しいバージョンのプログラムで作成したファイルを古いバージョンのコンポーネントで開くこともできます。  
  
32 ビット バージョンの Office をインストールしている場合は、32 ビット バージョンのコンポーネントをインストールする必要があります。 また、32 ビット モードでウィザード (または作成した Integration Services パッケージ) を実行する必要があります。 
 |Microsoft Office のバージョン|ダウンロード|  
|------------------------------|--------------|  
|2007|[2007 Office system ドライバー: データ接続コンポーネント](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|  
 
## <a name="azure-blob-storage"></a>Azure BLOB ストレージ  
Azure Blob Destination を使用するには、SSIS 用 Azure Feature Pack をインストールする必要があります。 詳細については、「[Azure Feature Pack for Integration Services &#40;SSIS&#41; (Integration Services 用の Azure Feature Pack &#40;SSIS&#41;)](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)」を参照してください。  

>   [!NOTE] Azure Storage 接続マネージャーとこれを使用する Blob Destination などのコンポーネントが汎用ストレージ アカウントと BLOB ストレージ アカウントの両方に接続できるようにするために、必ず最新バージョンの Azure Feature Pack を[こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 これら 2 種類のストレージ アカウントの詳細については、「[Microsoft Azure Storage の概要](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts)」を参照してください。

![Azure Blob Destination](../../integration-services/import-export-data/media/azure-blob-destination.png)

**Azure アカウントの使用**  
オンライン アカウントを使用するかどうかを指定します。

 **ストレージ アカウント名**  
 Azure ストレージ アカウントの名前を指定します。  
  
 **アカウント キー**  
 Azure ストレージ アカウントのキーを指定します。  
  
 **HTTPS の使用**  
 ストレージ アカウントへの接続に HTTP または HTTPS のどちらを使用するかを指定します。  
  
 **ローカル開発者アカウントの使用**  
 ローカル コンピューター上のストレージ エミュレーターを使用するかどうかを指定します。  
  
 **BLOB コンテナーの名前**  
 指定されたストレージ アカウントで利用できるストレージ コンテナーの一覧から選択します。  
  
 **BLOB ファイル形式**  
 テキスト ファイル形式または Avro ファイル形式を選択します。  
  
 **列区切り文字**  
 テキスト形式を選択した場合は、列区切り文字を指定します。  
  
 **先頭行を列名として使用する**  
 データの最初の行に列名が含まれるかどうかを指定します。  

## <a name="whats-next"></a>次の操作  
 データの変換先とデータへの接続方法を指定した後、次のページは、**[テーブルのコピーまたはクエリの指定]** です。 このページでは、テーブル全体をコピーするか、特定の行のみをコピーするかを指定します。 詳細については、「[テーブルのコピーまたはクエリの指定](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md)」を参照してください。  
