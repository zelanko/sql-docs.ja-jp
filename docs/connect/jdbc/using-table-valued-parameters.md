---
title: "テーブル値パラメーターを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 91777796843557cf6c5e6f7667994d7743b608a0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-table-valued-parameters"></a>テーブル値パラメーターの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  テーブル値パラメーターは、データを処理する複数のラウンド トリップや特別なサーバー側ロジックを必要とせず複数行の SQL Server へのクライアント アプリケーションからデータをマーシャ リングする簡単な方法を提供します。 テーブル値パラメーターを使用して、クライアント アプリケーション内のデータの行をカプセル化し、1 つのパラメーター化コマンド内のサーバーにデータを送信することができます。 受信データ行は、処理できる Transact SQL を使用してテーブル変数に格納されます。  
  
 テーブル値パラメーター列の値は、標準の TRANSACT-SQL SELECT ステートメントを使用してアクセスできます。 テーブル値パラメーターは厳密に型指定し、その構造が自動的に検証します。 テーブル値パラメーターのサイズは、サーバーのメモリによってのみ制限されます。  
  
> [!NOTE]  
>  テーブル値パラメーターのサポートは Microsoft JDBC Driver 6.0 for SQL Server 以降より使用可能です。  
  
> [!NOTE]  
>  テーブル値パラメーターのデータを返すことはできません。 テーブル値パラメーターは入力専用です。OUTPUT キーワードはサポートされていません。  
  
 テーブル値パラメーターの詳細については、次のリソースを参照してください。  
  
|リソース|Description|  
|--------------|-----------------|  
|[テーブル値パラメーター (データベース エンジン)](http://go.microsoft.com/fwlink/?LinkId=98363) SQL Server オンライン ブック|作成してテーブル値パラメーターを使用する方法について説明します|  
|[ユーザー定義テーブル型](http://go.microsoft.com/fwlink/?LinkId=98364)SQL Server オンライン ブック|テーブル値パラメーターを宣言するために使用するユーザー定義テーブル型について説明します|  
|[Microsoft SQL Server データベース エンジン](http://go.microsoft.com/fwlink/?LinkId=120507)CodePlex の「|SQL Server の機能および機能を使用する方法を示すサンプルが含まれます|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>SQL Server の以前のバージョンで複数の行を渡す  
 テーブル値パラメーターは、SQL Server 2008 に導入された、前に、ストアド プロシージャまたはパラメーター化 SQL コマンドに複数行のデータを受け渡すためのオプションは限られていました。 開発者は、サーバーに複数の行を渡すための次のオプションから選択できます。  
  
-   一連の個別のパラメーターを使用して、複数の列および行のデータの値を表します。 このメソッドを使用して渡すことができるデータの量は、使用できるパラメーターの数によって制限されます。 SQL Server のプロシージャが持てる、多くても 2100 パラメーターです。 サーバー側ロジックは、テーブル変数または一時テーブル処理のために個々 の値をアセンブルする必要があります。  
  
-   区切られた文字列または XML ドキュメントを複数のデータ値にバンドルし、そのテキスト値をプロシージャまたはステートメントに渡します。 これは、必要がありますプロシージャまたはステートメントに、データ構造と処理の検証に必要なロジックを含める値。  
  
-   一連のデータの変更を複数の行に影響する個々 の SQL ステートメントを作成します。 変更をサーバーに個別に送信またはグループにバッチ処理できます。 ただし、複数のステートメントを含んでいるバッチで送信されると場合でもの各ステートメントとは別にサーバー上で実行します。  
  
-   Bcp ユーティリティ プログラムを使用して、または[SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx)に多数のデータ行をテーブルに読み込むオブジェクト。 この方法は非常に効率的なサーバー側の処理を一時テーブルまたはテーブル変数にデータが読み込まれていない限りことはできません。  
  
## <a name="creating-table-valued-parameter-types"></a>テーブル値パラメーターの型を作成します。  
 テーブル値パラメーターは、TRANSACT-SQL の CREATE TYPE ステートメントを使用して定義されている厳密に型指定されたテーブルの構造に基づいています。 テーブル型を作成し、クライアント アプリケーションでテーブル値パラメーターを使用する前に、SQL Server で、構造を定義する必要があります。 テーブルの種類の作成の詳細については、次を参照してください。[ユーザー定義テーブル型](http://go.microsoft.com/fwlink/?LinkID=98364)SQL Server オンライン ブック。  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 テーブル型を作成した後は、その種類に基づいてテーブル値パラメーターを宣言できます。 次の TRANSACT-SQL フラグメントでは、ストアド プロシージャ定義内のテーブル値パラメーターを宣言する方法を示します。 READONLY キーワードは、テーブル値パラメーターを宣言するために必要なことに注意してください。  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>テーブル値パラメーター (TRANSACT-SQL) によるデータの変更  
 テーブル値パラメーターは、1 つのステートメントを実行することによって複数の行に影響するセット ベースのデータ変更で使用できます。 たとえば、テーブル値パラメーターのすべての行を選択して、データベース テーブルに挿入または update ステートメントを作成するには、テーブル値パラメーターを更新するテーブルに結合することでします。  
  
 次の TRANSACT-SQL UPDATE ステートメントでは、Categories テーブルに結合して、テーブル値パラメーターを使用する方法を示します。 Join FROM 句でテーブル値パラメーターを使用するときにする必要がありますエイリアスも、"ec"という別名をテーブル値パラメーターがここでは、ここで示すようにします。  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 この TRANSACT-SQL の例では、単一セット ベース操作での挿入を実行するテーブル値パラメーターから行を選択する方法を示します。  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>テーブル値パラメーターの制限事項  
 テーブル値パラメーターにいくつかの制限があります。  
  
-   テーブル値パラメーターは、ユーザー定義関数に渡すことはできません。  
  
-   テーブル値パラメーターは、UNIQUE または PRIMARY KEY 制約をサポートするためにのみインデックスを作成できます。 SQL Server は、テーブル値パラメーターの統計を保持していません。  
  
-   テーブル値パラメーターとは、TRANSACT-SQL コードの読み取り専用です。 テーブル値パラメーターの行の列の値を更新することはできませんし、挿入または行を削除することはできません。 ストアド プロシージャに渡されるまたはテーブル値パラメーター内のステートメントをパラメーター化されたデータを変更するを一時テーブルにまたはテーブル変数にデータを挿入する必要があります。  
  
-   ALTER TABLE ステートメントを使用して、テーブル値パラメーターの設計を変更することはできません。
-   テーブル値パラメーター内のラージ オブジェクトをストリーム配信できます。  
  
## <a name="configuring-a-table-valued-parameter"></a>テーブル値パラメーターを構成します。  
 Microsoft JDBC Driver 6.0 for SQL Server から始まり、テーブル値パラメーターはパラメーター化されたステートメントまたはパラメーター化されたストアド プロシージャでサポートされています。 テーブル値パラメーターは、結果セットから、SQLServerDataTable から取得されます。 またはユーザーから ISQLServerDataRecord インターフェイスの実装を提供できます。 準備されたクエリのテーブル値パラメーターを設定する場合は、サーバー上で作成された互換性のある型の名前に一致するよう型名を指定する必要があります。  
  
 次の 2 つのコード フラグメントでは、SQLServerPreparedStatement とデータを挿入する SQLServerCallableStatement、テーブル値パラメーターを構成する方法を示します。 ここで、SQLServerDataTable または結果セットまたは ISQLServerDataRecord オブジェクト sourceTVPObject 使用できます。 例では、接続がアクティブな接続オブジェクトを前提としています。  
  
```  
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =   
    (SQLServerPreparedStatement) connection.prepareStatement(“INSERT INTO dbo.Categories SELECT * FROM ?”);  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```  
  
```  
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =   
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");       
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```  
  
> [!NOTE]  
>  セクションを参照して**JDBC Driver のテーブル値パラメーター API**下、テーブル値パラメーターを設定するため利用可能な Api の完全な一覧についてはします。  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>SQLServerDataTable オブジェクトとしてテーブル値パラメーターの受け渡し  
 Microsoft JDBC Driver 6.0 for SQL Server から始まり、SQLServerDataTable クラスは、リレーショナル データのメモリ内のテーブルを表します。 この例では、SQLServerDataTable オブジェクトを使用してデータをメモリ内からテーブル値パラメーターを作成する方法を示します。 コードが最初 SQLServerDataTable オブジェクトを作成、そのスキーマを定義およびテーブル データを追加します。 コードは、このデータ テーブルをテーブル値パラメーターとして SQL Server に渡される SQLServerPreparedStatement を構成します。  
  
```  
// Assumes connection is an active Connection object.  
  
// Create an in-memory data table.  
SQLServerDataTable sourceDataTable = new SQLServerDataTable();   
  
// Define metadata for the data table.  
sourceDataTable.addColumnMetadata("CategoryID" ,java.sql.Types.INTEGER);   
sourceDataTable.addColumnMetadata("CategoryName" ,java.sql.Types.NVARCHAR);   
  
// Populate the data table.  
sourceDataTable.addRow(1, "CategoryNameValue1");   
sourceDataTable.addRow(2, "CategoryNameValue2");   
  
// Pass the data table as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =   
        (SQLServerPreparedStatement) connection.prepareStatement(  
            "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceDataTable);  
pStmt.execute();  
```  
  
> [!NOTE]  
>  セクションを参照して**JDBC Driver のテーブル値パラメーター API**下、テーブル値パラメーターを設定するため利用可能な Api の完全な一覧についてはします。  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>結果セット オブジェクトとしてテーブル値パラメーターの受け渡し  
 この例では、行のテーブル値パラメーターを結果セットからデータをストリーミングする方法を示します。 コードは最初のソース テーブルからデータを取得、SQLServerDataTable オブジェクトを作成、そのスキーマを定義およびテーブル データを追加します。 コードは、このデータ テーブルをテーブル値パラメーターとして SQL Server に渡される SQLServerPreparedStatement を構成します。  
  
```  
// Assumes connection is an active Connection object.  
  
// Create the source ResultSet object. Here SourceCategories is a table defined with the same schema as Categories table.   
ResultSet sourceResultSet = connection.createStatement().executeQuery("SELECT * FROM SourceCategories");  
  
// Pass the source result set as a table-valued parameter using a prepared statement.  
SQLServerPreparedStatement pStmt =   
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceResultSet);  
pStmt.execute();  
```  
  
> [!NOTE]  
>  セクションを参照して**JDBC Driver のテーブル値パラメーター API**下、テーブル値パラメーターを設定するため利用可能な Api の完全な一覧についてはします。  
  
## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>ISQLServerDataRecord オブジェクトとしてテーブル値パラメーターの受け渡し  
 Microsoft JDBC Driver 6.0 for SQL Server から始まり、新しいインターフェイス ISQLServerDataRecord が (ユーザーが提供する方法を実装) に応じてデータのストリーミングの使用可能なテーブル値パラメーターを使用します。 次の例では、ISQLServerDataRecord インターフェイスを実装する方法と、テーブル値パラメーターとして渡す方法を示します。 わかりやすくするため、次の例は、テーブル値パラメーターをハードコードされた値を持つ 1 つの行を渡します。 理想的には、ユーザーはテキスト ファイルからの変更など、任意のソースから行をストリームするこのインターフェイスを実装は。  
  
```  
class MyRecords implements ISQLServerDataRecord  
{  
    int currentRow = 0;  
    Object[] row = new Object[2];  
  
    MyRecords(){  
        // Constructor. This implementation has just one row.   
        row[0] = new Integer(1);  
        row[1] = "categoryName1";  
    }  
  
    public int getColumnCount(){  
        // Return the total number of columns, for this example it is 2.  
        return 2;  
    }  
  
    public SQLServerMetaData getColumnMetaData(int columnIndex) {  
        // Return the column metadata.  
        if (1 == columnIndex)  
            return new SQLServerMetaData("CategoryID", java.sql.Types.INTEGER);  
        else  
            return new SQLServerMetaData("CategoryName", java.sql.Types.NVARCHAR);  
    }  
  
    public Object[] getRowData(){  
        // Return the columns in the current row as an array of objects. This implementation has just one row.  
        return row;       
    }  
  
    public boolean next(){  
        // Move to the next row. This implementation has just one row, after processing the first row, return false.  
        currentRow++;  
        if (1 == currentRow)  
            return true;  
        else  
            return false;  
    }     
}  
  
// Following code demonstrates how to pass MyRecords object as a table-valued parameter.  
MyRecords sourceRecords = new MyRecords();  
SQLServerPreparedStatement pStmt =   
        (SQLServerPreparedStatement) connection.prepareStatement(  
                "INSERT INTO dbo.Categories SELECT * FROM ?;");  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceRecords);  
pStmt.execute();  
```  
  
> [!NOTE]  
>  セクションを参照して**JDBC Driver のテーブル値パラメーター API**下、テーブル値パラメーターを設定するため利用可能な Api の完全な一覧についてはします。  
    
## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>JDBC Driver のテーブル値パラメーター API  
 **SQLServerMetaData**  
  
 このクラスは、列のメタデータを表します。 列のメタデータをテーブル値パラメーターに渡す ISQLServerDataRecord インターフェイスで使用されます。 このクラスのメソッドは次のとおりです。  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerMetaData (文字列 columnName、int sqlType、int 型の有効桁数、int 型の小数点以下桁数、ブール useServerDefault、ブール isUniqueKey、SQLServerSortOrder sortOrder、int sortOrdinal)|指定された列名、sql 型、有効桁数、小数点以下桁数およびサーバーの既定値を持つ SQLServerMetaData の新しいインスタンスを初期化します。 このフォームのコンス トラクターは、列が一意で、テーブル値パラメーターで、列と並べ替え列の序数の並べ替え順序を指定することによってテーブル値パラメーターをサポートします。 <br><br>useServerDefault - のかどうか、この列はサーバーの既定値です。 を使用する必要がありますを指定します既定値は false です。<br>isUniqueKey - は、テーブル値パラメーターの列が一意であることを示します既定値は false です。<br>sortOrder -; 列の並べ替え順序を示します既定値は SQLServerSortOrder.Unspecified です。<br>sortOrdinal - 並べ替え列の序数を指定しますsortOrdinal が 0 から開始します。既定値は-1 です。|
|パブリック SQLServerMetaData (文字列 columnName、int sqlType)|列名と sql の型を使用して SQLServerMetaData の新しいインスタンスを初期化します。|  
|パブリック SQLServerMetaData (文字列 columnName、int sqlType、int 型の有効桁数、int 型の小数点以下桁数)|列名、sql 型、有効桁数および小数点以下桁数を使用して SQLServerMetaData の新しいインスタンスを初期化します。|  
|パブリック SQLServerMetaData (SQLServerMetaData sqlServerMetaData)|別の SQLServerMetaData オブジェクト SQLServerMetaData からの新しいインスタンスを初期化します。|  
|パブリック文字列 getColumName()|列の名前を取得します。|  
|パブリック int getSqlType()|Java sql 型を取得します。|  
|パブリック int getPrecision()|列に渡される型の有効桁数を取得します。|  
|パブリック int getScale()|列に渡される型の小数点以下桁数を取得します。|  
|パブリック SQLServerSortOrder getSortOrder()|並べ替え順序を取得します。|
|パブリック int getSortOrdinal()|並べ替えの序数を取得します。|
|パブリック ブール isUniqueKey()|列が一意かどうかを返します。|
|パブリック ブール useServerDefault()|サーバーの既定値を返すかどうか、列に使用します。|
  
 **SQLServerSortOrder**
 
 並べ替え順序を定義する列挙です。 使用可能な値は昇順、降順および未指定です。 
  
 **SQLServerDataTable**  
  
 このクラスは、テーブル値パラメーターで使用する、メモリ内のデータ テーブルを表します。 このクラスのメソッドは次のとおりです。  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerDataTable()|SQLServerDataTable の新しいインスタンスを初期化します。|  
|パブリック反復子 < エントリ\<整数、object[] >> getIterator()|データ テーブルの行に対して反復子を取得します。|  
|パブリックの void addColumnMetadata (文字列 columnName、int sqlType)|指定された列のメタデータを追加します。|  
|public void addColumnMetadata (SQLServerDataColumn 列)|指定された列のメタデータを追加します。|  
|public void addRow (オブジェクトの値では...)|データ テーブルに 1 行のデータを追加します。|  
|パブリック マップ\<整数、SQLServerDataColumn > getColumnMetadata()|このデータ テーブルの列メタデータを取得します。|
|public void clear() |このデータ テーブルをクリアします。 |  
  
 **SQLServerDataColumn**  
  
 このクラスは、SQLServerDataTable によって表される、インメモリ データ テーブルの列を表します。 このクラスのメソッドは次のとおりです。  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerDataColumn (文字列 columnName、int sqlType)|列の名前と種類 SQLServerDataColumn の新しいインスタンスを初期化します。|  
|パブリック文字列 getColumnName()|列の名前を取得します。|  
|パブリック int getColumnType()|列のデータ型を取得します。|  
  
 **ISQLServerDataRecord**  
  
 このクラスは、ユーザーが、テーブル値パラメーターにデータをストリーミングするために実装するインターフェイスを表します。 このインターフェイスのメソッドは、次のとおりです。  
  
|名前|Description|  
|----------|-----------------|  
|パブリック SQLServerMetaData getColumnMetaData (int 型の列) です。|指定された列インデックスの列のメタデータを取得します。|  
|パブリック int getColumnCount() です。|列の合計数を取得します。|  
|パブリック オブジェクト:operator[] getRowData() です。|オブジェクトの配列として、現在の行のデータを取得します。|  
|パブリック ブール next() です。|次の行に移動します。 移動が成功し、それ以外の場合、次の行、false がある場合は、True を返します。|  
  
 **SQLServerPreparedStatement**  
  
 テーブル値パラメーターの引き渡しをサポートするためにこのクラスは、次の方法が追加されました。  
  
|名前|Description|  
|----------|-----------------|  
|パブリックの最終的な void setStructured (int parameterIndex、文字列 tvpName、SQLServerDataTable tvpDataTbale)|データ テーブルとテーブル値パラメーターを追加します。 parameterIndex はパラメーター インデックス、tvpName は、テーブル値パラメーターの名前、tvpDataTable はソース データ テーブル オブジェクトです。|  
|パブリックの最終的な void setStructured (int parameterIndex、文字列 tvpName、ResultSet tvpResultSet)|別のテーブルから取得された結果セットには、テーブル値パラメーターを設定します。 parameterIndex はパラメーター インデックス、tvpName は、テーブル値パラメーターの名前、tvpResultSet はソースの結果セット オブジェクトです。|  
|パブリックの最終的な void setStructured (int parameterIndex、文字列 tvpName、ISQLServerDataRecord tvpDataRecord)|ISQLServerDataRecord オブジェクトを持つテーブル値パラメーターを追加します。 ISQLServerDataRecord はデータのストリーミングのために使用され、ユーザーがその使用方法を決定します。 parameterIndex パラメーターのインデックス、tvpName は、テーブル値パラメーターの名前、tvpDataRecord ISQLServerDataRecord オブジェクト。|  
  
 **SQLServerCallableStatement**  
  
 テーブル値パラメーターの引き渡しをサポートするためにこのクラスは、次の方法が追加されました。  
  
|名前|Description|  
|----------|-----------------|  
|パブリックの最終的な void setStructured (文字列 paratemeterName、文字列 tvpName、SQLServerDataTable tvpDataTable)|データ テーブルとストアド プロシージャに渡されたテーブル値パラメーターを追加します。 paratemeterName はパラメーターの名前、tvpName は TVP、型の名前、tvpDataTable はデータ テーブル オブジェクトです。|  
|パブリックの最終的な void setStructured (文字列 paratemeterName、文字列 tvpName、ResultSet tvpResultSet)|別のテーブルから取得された結果セットでストアド プロシージャに渡されたテーブル値パラメーターを追加します。 paratemeterName はパラメーターの名前、tvpName は TVP、型の名前、tvpResultSet はソースの結果セット オブジェクトです。|  
|パブリックの最終的な void setStructured (文字列 paratemeterName、文字列 tvpName、ISQLServerDataRecord tvpDataRecord)|ISQLServerDataRecord オブジェクトを持つストアド プロシージャに渡されたテーブル値パラメーターを追加します。 ISQLServerDataRecord はデータのストリーミングのために使用され、ユーザーがその使用方法を決定します。 paratemeterName はパラメーターの名前、tvpName は TVP、型の名前、tvpDataRecord は ISQLServerDataRecord オブジェクトです。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

