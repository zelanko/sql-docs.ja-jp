---
title: sp_addlinkedserver (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addlinkedserver_TSQL
- sp_addlinkedserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedserver
ms.assetid: fed3adb0-4c15-4a1a-8acd-1b184aff558f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b4ff861015fc669defee69fece5c26ee45d66eaa
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493913"
---
# <a name="spaddlinkedserver-transact-sql"></a>sp_addlinkedserver (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リンク サーバーを作成します。 リンク サーバーを使用すると、OLE DB データ ソースに対する異種の分散クエリの利用が可能になります。 使用してリンク サーバーを作成した後**sp_addlinkedserver**、分散クエリは、このサーバーに対して実行できます。 リンク サーバーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスとして定義した場合は、リモート ストアド プロシージャを実行できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addlinkedserver [ @server= ] 'server' [ , [ @srvproduct= ] 'product_name' ]   
     [ , [ @provider= ] 'provider_name' ]  
     [ , [ @datasrc= ] 'data_source' ]   
     [ , [ @location= ] 'location' ]   
     [ , [ @provstr= ] 'provider_string' ]   
     [ , [ @catalog= ] 'catalog' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @server = ] 'server'` 作成するリンク サーバーの名前です。 *server* のデータ型は **sysname**で、既定値はありません。  
  
`[ @srvproduct = ] 'product_name'` リンク サーバーとして追加する OLE DB データ ソースの製品名です。 *product_name*は**nvarchar (** 128 **)**、既定値は NULL です。 場合**SQL Server**、 *provider_name*、 *data_source*、*場所*、 *provider_string*と*カタログ*指定する必要はありません。  
  
`[ @provider = ] 'provider_name'` このデータ ソースに対応する OLE DB プロバイダーの一意なプログラム識別子 (PROGID) です。 *provider_name*現在のコンピューターにインストールされている指定された OLE DB プロバイダーに対して一意である必要があります。 *provider_name*は**nvarchar (** 128 **)**、既定値は NULL です。 ただし、場合*provider_name*は省略すると、SQLNCLI が使用されます。 (SQLNCLI を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにリダイレクトされます)。OLE DB プロバイダーは、レジストリで指定した PROGID を登録することが必要です。  
  
`[ @datasrc = ] 'data_source'` OLE DB プロバイダーで解釈、データ ソースの名前です。 *data_source*は**nvarchar (** 4000 **)** します。 *data_source* OLE DB プロバイダーを初期化する DBPROP_INIT_DATASOURCE プロパティとして渡されます。  
  
`[ @location = ] 'location'` OLE DB プロバイダーで解釈は、データベースの場所です。 *場所*は**nvarchar (** 4000 **)**、既定値は NULL です。 *場所*OLE DB プロバイダーを初期化する DBPROP_INIT_LOCATION プロパティとして渡されます。  
  
`[ @provstr = ] 'provider_string'` 一意のデータ ソースを識別する OLE DB プロバイダーに固有の接続文字列です。 *provider_string*は**nvarchar (** 4000 **)**、既定値は NULL です。 *provstr*が IDataInitialize に渡されるまたは OLE DB プロバイダーを初期化する DBPROP_INIT_PROVIDERSTRING プロパティとして設定します。  
  
 に対して、リンク サーバーが作成されたとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、サーバーと、SERVER キーワードを使用して、インスタンスを指定することができます =*servername*\\*instancename*の特定のインスタンスを指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 *servername*となるコンピューターの名前を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されていると*instancename*の特定のインスタンスの名前を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するユーザーを接続します。  
  
> [!NOTE]
>  ミラー化されたデータベースにアクセスするには、接続文字列は、データベース名を含める必要があります。 この名前は、データ アクセス プロバイダーがフェールオーバーを試行できるようにするために必要です。 データベースを指定することができます、 **@provstr**または**@catalog**パラメーター。 必要に応じて、接続文字列では、フェールオーバー パートナー名が指定もできます。  
  
`[ @catalog = ] 'catalog'` OLE DB プロバイダーへの接続の確立時に使用されるカタログです。 *カタログ*は**sysname**、既定値は NULL です。 *カタログ*OLE DB プロバイダーを初期化する DBPROP_INIT_CATALOG プロパティとして渡されます。 インスタンスに対して、リンク サーバーが定義されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カタログは、リンク サーバーがマップされている既定のデータベースを参照します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="remarks"></a>コメント  
 次の表では、リンク サーバーは、OLE DB を介してアクセスできるデータ ソース設定できる方法を示します。 リンク サーバーは、特定のデータ ソースの複数の方法を設定できます。データ ソースの種類の 1 つ以上の行があります。 この表も示しています、 **sp_addlinkedserver**リンク サーバーを設定するために使用するパラメーター値。  
  
|リモート OLE DB データ ソース|OLE DB プロバイダー|product_name|provider_name|data_source|場所|provider_string|catalog|  
|-------------------------------|---------------------|-------------------|--------------------|------------------|--------------|----------------------|-------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <sup>1</sup> (既定値)||||||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー||**SQLNCLI**|ネットワーク名[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](の既定のインスタンス)|||データベース名 (省略可能)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー||**SQLNCLI**|*servername*\\*instancename* (の特定のインスタンス)|||データベース名 (省略可能)|  
|Oracle、バージョン 8 以降|Oracle Provider for OLE DB|Any|**OraOLEDB.Oracle**|Oracle データベースに対する別名||||  
|Access/jet|Microsoft OLE DB Provider for Jet|Any|**Microsoft.Jet.OLEDB.4.0**|Jet データベース ファイルの完全なパス||||  
|ODBC データ ソース (ODBC data source)|Microsoft OLE DB Provider for ODBC|Any|**MSDASQL**|システム DSN の ODBC データ ソース||||  
|ODBC データ ソース (ODBC data source)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for ODBC|Any|**MSDASQL**|||ODBC 接続文字列||  
|ファイル システム|[!INCLUDE[msCoName](../../includes/msconame-md.md)] インデックス サービスの OLE DB プロバイダー|Any|**MSIDXS は、その**|インデックス作成サービス カタログ名||||  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ワークシート|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet|Any|**Microsoft.Jet.OLEDB.4.0**|Excel ファイルのフル パス||Excel 5.0||  
|IBM DB2 データベース|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for DB2|Any|**DB2OLEDB**|||参照してください[!INCLUDE[msCoName](../../includes/msconame-md.md)]OLE DB Provider for DB2 のドキュメント。|DB2 データベースのカタログ名|  
  
 <sup>1</sup>リンク サーバーをセットアップするのには、この方法のリモート インスタンスのネットワーク名と同じにするリンク サーバーの名前は必ず[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 使用*data_source*サーバーを指定します。  
  
 <sup>2</sup> "any"は、製品名を指定できるで何かを示します。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、プロバイダーで使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダー名が指定されていない場合、または場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品名として指定されます。 以前のプロバイダー名、SQLOLEDB を指定した場合でも、カタログに保存されるときに SQLNCLI に変更されます。  
  
 *Data_source*、*場所*、 *provider_string*、および*カタログ*パラメーターまたはリンクされた複数のデータベースの識別サーバーをポイントします。 これらのいずれかのパラメーターが NULL に設定されると、対応する OLE DB 初期化プロパティは設定されません。  
  
 クラスター化された環境で OLE DB データ ソースを指すファイル名を指定するとを使用して、汎用名前付け規則 (UNC) または共有ドライブの場所を指定します。  
  
 **sp_addlinkedserver**ユーザー定義のトランザクション内で実行することはできません。  
  
> [!IMPORTANT]
>  使用してリンク サーバーを作成するときに**sp_addlinkedserver**、すべてのローカル ログインに対して既定の自己マッピングが追加されます。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインがプロバイダーにアクセスすることができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。 管理者は、使用を検討する必要があります`sp_droplinkedsrvlogin <linkedserver_name>, NULL`グローバル マッピングを削除します。  
  
## <a name="permissions"></a>アクセス許可  
 `sp_addlinkedserver`ステートメントが必要です、`ALTER ANY LINKED SERVER`権限。 (SSMS**新しいリンク サーバー**  ダイアログ ボックスがメンバーシップが必要な方法で実装されている、`sysadmin`固定サーバー ロール)。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-the-microsoft-sql-server-native-client-ole-db-provider"></a>A. Microsoft SQL Server Native Client OLE DB プロバイダーを使用してください。  
 次の例では、`SEATTLESales` というリンク サーバーを作成します。 製品名は `SQL Server` で、プロバイダー名は使用されません。  
  
```  
USE master;  
GO  
EXEC sp_addlinkedserver   
   N'SEATTLESales',  
   N'SQL Server';  
GO  
```  
  
 次の例では、リンク サーバーを作成する`S1_instance1`のインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー。  
  
```  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'SQLNCLI',   
   @datasrc=N'S1\instance1';  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-microsoft-access"></a>B. Microsoft OLE DB Provider for Microsoft Access を使用する  
 Microsoft.Jet.OLEDB.4.0 プロバイダーは、2002-2003 形式を使用する Microsoft Access データベースに接続します。 次の例では、`SEATTLE Mktg` というリンク サーバーを作成します。  
  
> [!NOTE]  
>  この例では、両方[!INCLUDE[msCoName](../../includes/msconame-md.md)]アクセスと、サンプル**Northwind**データベースがインストールされていることと、 **Northwind**データベースが C:\Msoffice\Access\Samples にします。  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.Jet.OLEDB.4.0',   
   @srvproduct = N'OLE DB Provider for Jet',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.mdb';  
GO  
```  
  
 Microsoft.ACE.OLEDB.12.0 プロバイダーは、2007 形式を使用する Microsoft Access データベースに接続します。 次の例では、`SEATTLE Mktg` というリンク サーバーを作成します。  
  
> [!NOTE]  
>  この例では、両方[!INCLUDE[msCoName](../../includes/msconame-md.md)]アクセスと、サンプル**Northwind**データベースがインストールされていることと、 **Northwind**データベースが C:\Msoffice\Access\Samples にします。  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.ACE.OLEDB.12.0',   
   @srvproduct = N'OLE DB Provider for ACE',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.accdb';  
GO  
```  
  
### <a name="c-using-the-microsoft-ole-db-provider-for-odbc-with-the-datasource-parameter"></a>C. ODBC の data_source パラメーターを使用して Microsoft OLE DB Provider を使用します。  
 次の例では、というリンク サーバーを作成する`SEATTLE Payroll`を使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for ODBC (`MSDASQL`) および*data_source*パラメーター。  
  
> [!NOTE]  
>  リンク サーバーを使用する前には、指定した ODBC データ ソース名をサーバーのシステム DSN として定義する必要があります。  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Payroll',   
   @srvproduct = N'',  
   @provider = N'MSDASQL',   
   @datasrc = N'LocalServer';  
GO  
```  
  
### <a name="d-using-the-microsoft-ole-db-provider-for-excel-spreadsheet"></a>D. Excel スプレッドシート用の Microsoft OLE DB プロバイダーを使用します。  
 使用してリンク サーバー定義を作成する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 1997-2003 形式で Excel スプレッドシートへのアクセスにまず名前付き範囲 Excel で作成して Excel ワークシートの行と列を指定しています。 こうすると、分散クエリで範囲の名前をテーブル名として参照できるようになります。  
  
```  
EXEC sp_addlinkedserver 'ExcelSource',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   'c:\MyData\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
GO  
```  
  
 Excel スプレッドシートからデータにアクセスするには、セルの範囲に名前を関連付けます。 先に設定したリンク サーバーを使って、テーブルとして指定されている名前付き範囲 `SalesData` にアクセスするときには、次のクエリを使用できます。  
  
```  
SELECT *  
   FROM ExcelSource...SalesData;  
GO  
```  
  
 場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されているリモート共有へのアクセス権を持つドメイン アカウントでマップされたドライブではなく UNC パスを使用することができます。  
  
```  
EXEC sp_addlinkedserver 'ExcelShare',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   '\\MyServer\MyShare\Spreadsheets\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
```  
  
 Excel への接続には、Excel 2007 形式でスプレッドシートは、ACE プロバイダーを使用します。  
  
```  
EXEC sp_addlinkedserver @server = N'ExcelDataSource',   
@srvproduct=N'ExcelData', @provider=N'Microsoft.ACE.OLEDB.12.0',   
@datasrc=N'C:\DataFolder\People.xlsx',  
@provstr=N'EXCEL 12.0' ;  
  
```  
  
### <a name="e-using-the-microsoft-ole-db-provider-for-jet-to-access-a-text-file"></a>E. テキスト ファイルにアクセスする、Microsoft OLE DB Provider for Jet を使用します。  
 次の例では、Access .mdb ファイル内のテーブルとしてテキスト ファイルにリンクするのではなく、直接テキスト ファイルにアクセスするリンク サーバーを作成します。 プロバイダーは`Microsoft.Jet.OLEDB.4.0`プロバイダー文字列は`Text`します。  
  
 データ ソースは、テキスト ファイルを格納するディレクトリの完全なパスです。 などのテキスト ファイルの構造を説明する schema.ini ファイルは、テキスト ファイルと同じディレクトリに存在する必要があります。 Schema.ini ファイルの作成方法の詳細については、Jet Database Engine のマニュアルを参照してください。  
  
```  
--Create a linked server.  
EXEC sp_addlinkedserver txtsrv, N'Jet 4.0',   
   N'Microsoft.Jet.OLEDB.4.0',  
   N'c:\data\distqry',  
   NULL,  
   N'Text';  
GO  
  
--Set up login mappings.  
EXEC sp_addlinkedsrvlogin txtsrv, FALSE, Admin, NULL;  
GO  
  
--List the tables in the linked server.  
EXEC sp_tables_ex txtsrv;  
GO  
  
--Query one of the tables: file1#txt  
--using a four-part name.   
SELECT *   
FROM txtsrv...[file1#txt];  
```  
  
### <a name="f-using-the-microsoft-ole-db-provider-for-db2"></a>F. Microsoft OLE DB Provider for DB2 使用  
 次の例では、というリンク サーバーを作成する`DB2`を使用して、`Microsoft OLE DB Provider for DB2`します。  
  
```  
EXEC sp_addlinkedserver  
   @server=N'DB2',  
   @srvproduct=N'Microsoft OLE DB Provider for DB2',  
   @catalog=N'DB2',  
   @provider=N'DB2OLEDB',  
   @provstr=N'Initial Catalog=PUBS;  
       Data Source=DB2;  
       HostCCSID=1252;  
       Network Address=XYZ;  
       Network Port=50000;  
       Package Collection=admin;  
       Default Schema=admin;';  
```  
  
### <a name="g-add-a-includesssdsfullincludessssdsfull-mdmd-as-a-linked-server-for-use-with-distributed-queries-on-cloud-and-on-premise-databases"></a>G. クラウドと内部設置型データベースに対応する分散クエリで使用するリンク サーバーとしての [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] の追加  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] をリンク サーバーとして追加し、内部設置型データベースとクラウド データベースにまたがる分散クエリでそのサーバーを使用することができます。 これは、オンプレミスの企業ネットワークと Windows Azure クラウドにまたがるデータベース複合ソリューションのコンポーネントです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ボックス製品には、ローカル データ ソースからデータとリモート ソースからデータを結合するクエリを記述することができます、分散クエリ機能が含まれています (以外のデータを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース) リンク サーバーとして定義します。 すべて[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]個別のリンク サーバーとして追加できます (仮想マスター) を除くと、その他のデータベース、データベース アプリケーションで直接を使用します。  
  
 使用する利点[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]管理の容易性、高可用性、スケーラビリティ、使い慣れた開発モデルとリレーショナル データ モデルの操作が含まれます。 使用する方法、データベース アプリケーションの要件の決定[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]クラウドで。 すべてのデータを同時に移動できます[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、または残り - オンプレミスのデータを維持しながら、データの一部を段階的に移動します。 このようなハイブリッド データベース アプリケーションの場合、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] をリンク サーバーとして追加し、データベース アプリケーションで分散クエリを実行して [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] からのデータと内部設置型データ ソースからのデータを結合することもできます。  
  
 接続する方法を説明する簡単な例を次に示します、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]分散クエリを使用します。  
  
```  
------ Configure the linked server  
-- Add one Windows Azure SQL DB as Linked Server  
EXEC sp_addlinkedserver  
@server='myLinkedServer', -- here you can specify the name of the linked server  
@srvproduct='',       
@provider='sqlncli', -- using SQL Server Native Client  
@datasrc='myServer.database.windows.net',   -- add here your server name  
@location='',  
@provstr='',  
@catalog='myDatabase'  -- add here your database name as initial catalog (you cannot connect to the master database)  
-- Add credentials and options to this linked server  
EXEC sp_addlinkedsrvlogin  
@rmtsrvname = 'myLinkedServer',  
@useself = 'false',  
@rmtuser = 'myLogin',             -- add here your login on Azure DB  
@rmtpassword = 'myPassword' -- add here your password on Azure DB  
EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;  
------ Now you can use the linked server to execute 4-part queries  
-- You can create a new table in the Azure DB  
exec ('CREATE TABLE t1tutut2(col1 int not null CONSTRAINT PK_col1 PRIMARY KEY CLUSTERED (col1) )') at myLinkedServer  
-- Insert data from your local SQL Server  
exec ('INSERT INTO t1tutut2 VALUES(1),(2),(3)') at myLinkedServer  
  
-- Query the data using 4-part names  
select * from myLinkedServer.myDatabase.dbo.myTable  
```  
  
## <a name="see-also"></a>参照  
 [分散クエリ ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [sp_setnetname &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setnetname-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
