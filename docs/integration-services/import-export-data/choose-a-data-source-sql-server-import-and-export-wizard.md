---
title: "[データ ソースの選択] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
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
  - "sql13.dts.impexpwizard.chooseadatasource.f1"
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 113
---
# [データ ソースの選択] (SQL Server インポートおよびエクスポート ウィザード)
  [ようこそ] ページの後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードに **[データ ソースを選ぶ]** が表示されます。 このページでは、データ ソースおよびデータに接続する方法についての情報を指定します。
  
使用できるデータ ソースの詳細については、「[どのようなデータ ソースと変換先を使用できるでしょうか。](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)」を参照してください。

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>[データ ソースの選択] ページのスクリーン ショット 
次のスクリーンショットは、ウィザードの **[データ ソースの選択]** ページの最初の部分を示しています。

![ソースの選択](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>データ ソースの選択
 **データ ソース**  
データ ソースを指定するには、ソースに接続することができるデータ プロバイダーを選択します。 プロバイダーの名前にはソースの名前 (SQL Server、Oracle、フラット ファイル、Excel、Access など) が含まれているため、ほとんどの場合、必要なデータ プロバイダーはプロバイダーの名前から明らかです。

**[データ ソース]** の一覧に表示される、使用できるデータ プロバイダーの一覧は、コンピューターにインストールされているプロバイダーによって異なります。 また、64 ビットと 32 ビットのどちらのウィザードを実行しているかによっても異なります。

データ ソースに使用できるプロバイダーが複数存在する可能性があります。 通常、ソースで使用できる任意のプロバイダーを選択できます。 たとえば、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client、.NET Framework Data Provider for SQL Server、または Microsoft OLE DB Provider for SQL Server を使用できます。 

場合によっては、最初は汎用的なデータ プロバイダーを選択する必要があります。 たとえば、データ ソースで ODBC ドライバーを使用している場合は、.NET Framework Data Provider for ODBC を選択します。  
 
データ ソースによっては、Microsoft またはサード パーティからデータ プロバイダーをダウンロードする必要があります。 使用できるデータ ソースの詳細については、「[どのようなデータ ソースと変換先を使用できるでしょうか。](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources)」を参照してください。

## <a name="after-you-choose-a-data-source"></a>データ ソースの選択後
データソースを選択した後、**[データ ソースを選ぶ]** ページ プロパティの残りの部分で指定するオプションの数は、選択したデータ プロバイダーによって異なります。

以降のセクションでは、使用頻度の高いデータ ソースの重要なオプションを一覧表示します。 **[データ ソース]** ドロップダウン リストに表示されるソースをすべて示しているわけではありません。 追加のオプションおよびその他のプロバイダーについては、プロバイダー固有のマニュアルを参照してください。 
  
> [!TIP]  データ ソースに接続文字列が必要な場合は、サードパーティ サイト「[The Connection Strings Reference](https://www.connectionstrings.com/)」(接続文字列リファレンス) をご覧ください。  

## <a name="microsoft-sql-server"></a>Microsoft SQL Server 

### <a name="connect-to-sql-server-with-sql-server-native-client-or-the-microsoft-ole-db-provider-for-sql-server"></a>SQL Server Native Client または Microsoft OLE DB Provider for SQL Server を使用して SQL Server に接続する  

SQL Server Native Client と Microsoft OLE DB Provider for SQL Server は、同じオプション セットを公開しています。 例として SQL Server Native Client のオプションを次のスクリーン ショットに示します。

![SQL Server へのネイティブ接続](../../integration-services/import-export-data/media/sql-server-connection-native.png)

 **サーバー名**  
 データが格納されているサーバーの名前または IP アドレスを入力するか、一覧からサーバーを選択します。  
  
> [!NOTE] 複数のサーバーが配置されたネットワークでは、サーバー名を入力する方が簡単です。 ドロップダウン リストをクリックすると、使用可能なすべてのサーバーがネットワークに照会されるため、時間がかかることがあります。また、目的のサーバー名が検索結果の一覧に表示されない可能性もあります。

非標準の TCP ポートを指定するには、サーバー名または IP アドレスの後にコンマを入力し、ポート番号を入力します。
  
 **Windows 認証を使用する**  
 データベースへのログインに、ウィザードが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用するかどうかを指定します。 より高いセキュリティのためには Windows 認証をお勧めします。  
  
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

このページでは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオプションがグループ化されて一覧表示されます。 重要なオプションを次に示します。 このプロバイダーを選択したときに一覧表示される追加オプションは通常、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のソース データベースに正しく接続するために必須というわけではありません。 

詳細については、「[.NET Framework Data Provider for SQL Server connection strings](https://www.connectionstrings.com/sqlconnection/)」(.NET Framework Data Provider for SQL Server の接続文字列) を参照してください。

![SQL Server への .net 接続](../../integration-services/import-export-data/media/sql-server-connection-net.png)
  
 **データ ソース**  
 データが格納されているサーバーの名前または IP アドレスを入力するか、一覧からサーバーを選択します。  
  
> [!NOTE] 複数のサーバーが配置されたネットワークでは、サーバー名を入力する方が簡単です。 ドロップダウン リストをクリックすると、使用可能なすべてのサーバーがネットワークに照会されるため、時間がかかることがあります。また、目的のサーバー名が検索結果の一覧に表示されない可能性もあります。  
 
 非標準の TCP ポートを指定するには、サーバー名または IP アドレスの後にコンマを入力し、ポート番号を入力します。
 
 **初期カタログ**  
 ソース データベースの名前を入力するか、一覧からデータベースを選択します。  
  
 **統合セキュリティ**  
 **True** を指定して Windows 統合認証を使用して接続するか (推奨)、**False** を指定して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続します。 **False** を指定した場合は、ユーザー ID とパスワードを入力する必要があります。 既定値は **False**です。  
  
 **ユーザー ID**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のユーザー名を指定します。  
  
 **パスワード**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合に、データベース接続用のパスワードを指定します。  

## <a name="oracle"></a>Oracle

Oracle への接続には .Net Framework Data Provider for Oracle または Microsoft OLE DB Provider for Oracle を使用します。 次のスクリーン ショットに示す .Net Framework Data Provider for Oracle は簡単に構成できます。

詳細については、「[.NET Framework Data Provider for Oracle connection strings](https://www.connectionstrings.com/net-framework-data-provider-for-oracle/)」(.NET Framework Data Provider for Oracle の接続文字列) または「[Microsoft OLE DB Provider for Oracle connection strings](https://www.connectionstrings.com/microsoft-ole-db-provider-for-oracle-msdaora/)」(Microsoft OLE DB Provider for Oracle の接続文字列) を参照してください。

![Oracle 接続](../../integration-services/import-export-data/media/oracle-connection.png)

## <a name="odbc-data-sources"></a>ODBC データ ソース

ODBC ドライバーが提供されているソースからデータをロードするには、.Net Framework Data Provider for ODBC を選択します。

ODBC データ ソースの接続文字列を指定するには、使用する ODBC ドライバーのドキュメントを参照するか、「[The Connection Strings Reference](https://www.connectionstrings.com/)」(接続文字列リファレンス) で例を探してください。 

例として、SQL Server への ODBC 接続を次のスクリーン ショットに示します。 この例で使用されている接続文字列は次のとおりです。

    Driver={SQL Server};Server=(local);Database=TestData;Trusted_Connection=Yes;

**[ConnectionString]** フィールドに接続文字列を入力すると、ウィザードによって文字列が解析され、個々のプロパティとその値が一覧の **[その他]** セクションに表示されます。

![SQL への ODBC 接続](../../integration-services/import-export-data/media/odbc-connection-sql.png)

## <a name="text-files-flat-files"></a>テキスト ファイル (フラット ファイル)
 
 フラット ファイル データ ソースのオプションに関するページは複数あります。
 
 ### <a name="general-page"></a>[全般] ページ
 **[全般]** ページでは、ファイルを選択し、**[フォーマット]** セクションで設定を確認できます。
 
 ![フラット ファイル接続の [全般] ページ](/Image/IEWizard%20Sources/Flat%20file%20connection%20general.png)  
   
**[全般]** ページの詳細については、Integration Services リファレンス ページ「[[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(General%20Page\).md)」を参照してください。  

### <a name="columns-page"></a>[列] ページ

 **[列]** ページでは、ウィザードによって識別された列と区切り記号の一覧を確認できます。
 
 ![フラット ファイル接続の [列] ページ](/Image/IEWizard%20Sources/Flat%20file%20connection%20columns.png)
  
**[列]** ページの詳細については、Integration Services リファレンス ページ「[[フラット ファイル接続マネージャー エディター] &#40;[列] ページ&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Columns%20Page\).md)」を参照してください。

### <a name="advanced-page"></a>[詳細設定] ページ

**[詳細設定]** ページには、データ ソース内の各列に関する詳細情報が表示されます (データの型とサイズを含む)。

次のスクリーン ショットでは、 **id** 列の初期データ型が文字列になっています。

![フラット ファイル接続の詳細設定の変更前](../../integration-services/import-export-data/media/flat-file-connection-advanced-before.png)

**[型の推測]** をクリックすると、**[列の型の推測]** ダイアログ ボックスが表示されます。 

![フラット ファイル接続の推測機能](../../integration-services/import-export-data/media/flat-file-connection-suggest.png)

**[列の型の推測]** ダイアログ ボックスでオプションを選択した後、**[OK]** をクリックすると、インポートされる列のデータ型がウィザードによって一部変更される場合があります。

次のスクリーン ショットでは、データ ソースの **id** 列が実際にはテキスト文字列ではなく、数値であることがウィザードによって認識され、列のデータ型が文字列から整数に変更されています。

![フラット ファイル接続の詳細設定の変更後](../../integration-services/import-export-data/media/flat-file-connection-advanced-after.png)
  
**[詳細設定]** ページの詳細については、Integration Services リファレンス ページ「[[フラット ファイル接続マネージャー エディター] &#40;[詳細設定] ページ&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)」を参照してください。

### <a name="preview-page"></a>[プレビュー] ページ

**[プレビュー]** ページでは、列とサンプル データの一覧を見て、内容が目的どおりであることを確認できます。

![フラット ファイル接続のプレビュー](../../integration-services/import-export-data/media/flat-file-connection-preview.png)

**[プレビュー]** ページの詳細については、Integration Services リファレンス ページ「[[フラット ファイル接続マネージャー エディター] &#40;[プレビュー] ページ&#41;](../Topic/Flat%20File%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)」を参照してください。  
 
## <a name="microsoft-excel"></a>Microsoft Excel

Microsoft Excel ブックへの接続例を次のスクリーン ショットに示します。

![Excel 接続](../../integration-services/import-export-data/media/excel-connection.png) 
 
 **Excel ファイル パス**  
 データをインポートするスプレッドシートのパスとファイル名を指定します。 たとえば、ローカル コンピューター上のファイルの場合は **C:\\MyData.xlsx**、ネットワーク共有上のファイルの場合は **\\\\Sales\\Database\\Northwind.xlsx** と指定します。 または、**[参照]** をクリックします。  
  
 **参照**  
 **[ファイルを開く]** ダイアログ ボックスを使用して、ワークシートを検索します。  

> [!NOTE] パスワードで保護された Excel ファイルはウィザードで開くことができません。

 **Excel バージョン**  
 ソース ブックで使用される Excel のバージョンを選択します。

選択したバージョンの Excel に接続するために追加のファイルのダウンロード、インストールが必要になる場合もあります。 詳細については、このページの「[Excel と Access に必要なコンポーネントのダウンロード](Choose%20a%20Data%20Source%20\%28SQL%20Server%20Import%20and%20Export%20Wizard%29.md\#officeDownloads)」を参照してください。

バージョンの指定時に問題が発生する場合 (たとえば、Microsoft Office 365 がインストールされているため、Access 2016 ランタイムをインストールできない場合など)、2016 ではなく 2013 など、旧バージョンでも別のバージョンを指定してみてください。

**先頭行に列名を含める**  
ソース データの最初の行に列名が含まれるかどうかを指定します。
-   ソース データに列名が含まれていないのにこのオプションを有効にすると、ウィザードではソース データの最初の行が列名として扱われます。
-   ソース データに列名が含まれているのにこのオプションを無効にすると、ウィザードでは列名の行がデータの最初の行として扱われます。

ソース データに列名がない場合、ウィザードでは内部的に F1、F2 などが一時的な列見出しとして使用されます。

## <a name="microsoft-access"></a>Microsoft Access  

Microsoft Access データベースへの接続例を次のスクリーン ショットに示します。

![Access 接続](../../integration-services/import-export-data/media/access-connection.png)

 **ファイル名**  
 データをインポートするデータベース ファイルのパスとファイル名を指定します。 たとえば、**C:\MyData.mdb、\\\Sales\Database\Northwind.mdb** などです。 または、**[参照]** をクリックします。
 
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
Azure BLOB Source を使用するには、SSIS 用 Azure Feature Pack をインストールする必要があります。 詳細については、「[Azure Feature Pack for Integration Services &#40;SSIS&#41; (Integration Services 用の Azure Feature Pack &#40;SSIS&#41;)](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)」を参照してください。  

>   [!NOTE] Azure Storage 接続マネージャーとこれを使用する Blob Source などのコンポーネントが汎用ストレージ アカウントと BLOB ストレージ アカウントの両方に接続できるようにするために、必ず最新バージョンの Azure Feature Pack を[こちら](https://www.microsoft.com/download/details.aspx?id=49492)からダウンロードしてください。 これら 2 種類のストレージ アカウントの詳細については、「[Microsoft Azure Storage の概要](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts)」を参照してください。

![Azure BLOB ストレージ接続](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

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
 データ ソースとデータへの接続方法を指定したら、**[変換先の選択]** ページに進みます。 このページでは、データの変換先およびデータに接続する方法についての情報を指定します。 詳細については、「[[変換先の選択] (SQL Server インポートおよびエクスポート ウィザード)](../Topic/Choose%20a%20Destination%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)」をご覧ください。  
