---
title: テーブル値パラメーターを使用して |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3af61054-a886-4e1a-ad85-93f87c6d3584
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3b6790bce4cc3eb84ec707b56e909876606fa02
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603532"
---
# <a name="using-table-valued-parameters"></a>テーブル値パラメーターの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

テーブル値パラメーターは、複数行のデータをクライアント アプリケーションから SQL Server に簡単にマーシャリングするための手段です。複数のラウンド トリップや、データ処理用の特別なサーバー側ロジックは必要ありません。 テーブル値パラメーターを使用すると、クライアント アプリケーションで複数行のデータをカプセル化してサーバーに送信する処理を 1 つのパラメーター化コマンドで実行できます。 受信データ行は、TRANSACT-SQL を使用してで操作できるテーブル変数に格納されます。  
  
テーブル値パラメーター列の値は、標準の TRANSACT-SQL SELECT ステートメントを使用してアクセスできます。 テーブル値パラメーターが厳密に型指定し、その構造が自動的に検証します。 テーブル値パラメーターのサイズは、サーバーのメモリによってのみ制限されます。  
  
> [!NOTE]  
> テーブル値パラメーターのサポートは、SQL Server 用 Microsoft JDBC Driver 6.0 以降より使用可能です。
>
> テーブル値パラメーターでは、データを返すことはできません。 テーブル値パラメーターは入力専用です。OUTPUT キーワードがサポートされていません。  
  
 テーブル値パラメーターの詳細については、次のリソースを参照してください。  
  
| リソース                                                                                                             | [説明]                                                                         |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [テーブル値パラメーター (データベース エンジン)](https://go.microsoft.com/fwlink/?LinkId=98363)で SQL Server オンライン ブック | 作成してテーブル値パラメーターを使用する方法について説明します                             |
| [ユーザー定義テーブル型](https://go.microsoft.com/fwlink/?LinkId=98364)で SQL Server オンライン ブック                  | テーブル値パラメーターの宣言に使用されるユーザー定義テーブル型について説明します |
| [Microsoft SQL Server データベース エンジン](https://go.microsoft.com/fwlink/?LinkId=120507)CodePlex の「        | SQL Server の機能を使用する方法を示すサンプルが含まれます  |
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>SQL Server の以前のバージョンで複数の行を渡す  

テーブル値パラメーターは、SQL Server 2008 に導入された、前に、ストアド プロシージャまたはパラメーター化 SQL コマンドに複数行のデータを渡すためのオプションは限られていました。 開発者は、サーバーに複数の行を渡すために、次のオプションから選択できます。  
  
- 一連の個別のパラメーターを使用して、複数の列と行のデータの値を表します。 このメソッドを使用して渡すことができるデータの量は、使用できるパラメーターの数によって制限されます。 SQL Server プロシージャ パラメーターを指定できます、最大で 2100 です。 サーバー側ロジックは、テーブル変数または一時テーブルの処理に個々 の値をアセンブルする必要があります。  
  
- 区切られた文字列または XML ドキュメントを複数のデータ値にバンドルし、プロシージャまたはステートメントをそのテキスト値を渡します。 必要があります、プロシージャを処理するため、データ構造を検証するために必要なロジックを含めるようにステートメント値。  
  
- 一連の複数の行に影響を与えるデータ変更の個々 の SQL ステートメントを作成します。 変更をサーバーに個別に送信またはグループにバッチ化できます。 ただし、複数のステートメントを含むバッチを送信している場合でも各ステートメントで実行されますとは別に、サーバー。  
  
- Bcp ユーティリティ プログラムを使用して、または[SQLServerBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy(v=vs.110).aspx)に多くのデータ行をテーブルに読み込むオブジェクト。 この手法は非常に効率的ですが、サーバー側の処理を一時テーブルまたはテーブル変数にデータが読み込まれていない場合ことはできません。  
  
## <a name="creating-table-valued-parameter-types"></a>テーブル値パラメーターの型を作成します。  

テーブル値パラメーターは TRANSACT-SQL を使用して定義されている厳密に型指定されたテーブルの構造に基づいて`CREATE TYPE`ステートメント。 テーブル型を作成し、クライアント アプリケーションでテーブル値パラメーターを使用する前に、SQL Server で、構造を定義する必要があります。 テーブル型の作成の詳細については、次を参照してください。[ユーザー定義テーブル型](https://go.microsoft.com/fwlink/?LinkID=98364)SQL Server オンライン ブックの「します。  

```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```

テーブル型を作成した後は、その型に基づいてテーブル値パラメーターを宣言できます。 次の TRANSACT-SQL フラグメントでは、ストアド プロシージャの定義でテーブル値パラメーターを宣言する方法を示します。 なお、`READONLY`キーワードが、テーブル値パラメーターを宣言するために必要です。  

```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```

## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>テーブル値パラメーター (Transact SQL) によるデータの変更  

テーブル値パラメーターは、1 つのステートメントを実行することによって複数の行に影響するセット ベースのデータ変更で使用できます。 たとえば、テーブル値パラメーターのすべての行を選択して、データベース テーブルに挿入または update ステートメントを作成するには、テーブル値パラメーターを更新するテーブルを結合することで。  
  
次の TRANSACT-SQL UPDATE ステートメントでは、Categories テーブルに結合して、テーブル値パラメーターを使用する方法を示します。 Join FROM 句でテーブル値パラメーターを使用するときにする必要がありますエイリアスも、次に示すよう、テーブル値パラメーターが"ec"エイリアスは。  

```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```

この TRANSACT-SQL の例では、単一のセット ベース操作で INSERT を実行するテーブル値パラメーターから行を選択する方法を示します。

```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```

## <a name="limitations-of-table-valued-parameters"></a>テーブル値パラメーターの制限事項

テーブル値パラメーターをいくつかの制限があります。  
  
- テーブル値パラメーターは、ユーザー定義関数に渡すことはできません。  
  
- テーブル値パラメーターは、UNIQUE または PRIMARY KEY 制約をサポートするためにのみインデックスを作成できます。 SQL Server では、テーブル値パラメーターの統計が保持されません。  
  
- テーブル値パラメーターとは、TRANSACT-SQL コードの読み取り専用です。 テーブル値パラメーターの行に列の値を更新することはできませんし、挿入または行を削除することはできません。 ストアド プロシージャに渡されるまたはテーブル値パラメーター内のステートメントをパラメーター化されたデータを変更するには、一時テーブルにまたはテーブル変数にデータを挿入する必要があります。  
  
- ALTER TABLE ステートメントを使用して、テーブル値パラメーターの設計を変更することはできません。

- テーブル値パラメーター内のラージ オブジェクトをストリーミングすることができます。  
  
## <a name="configuring-a-table-valued-parameter"></a>テーブル値パラメーターの構成

Microsoft JDBC Driver 6.0 for SQL Server から、テーブル値パラメーターは、パラメーター化されたステートメントまたはパラメーター化されたストアド プロシージャでサポートされます。 テーブル値パラメーターの結果セットから、SQLServerDataTable から値が設定またはユーザーから ISQLServerDataRecord インターフェイスの実装を提供できます。 準備されたクエリのテーブル値パラメーターを設定するときに、既にサーバー上に作成、互換性のある型の名前に一致するよう型名を指定する必要があります。  
  
次の 2 つのコード フラグメントでは、SQLServerPreparedStatement とは、SQLServerCallableStatement データを挿入すると、テーブル値パラメーターを構成する方法を示します。 ここで、SQLServerDataTable、または、ResultSet、ISQLServerDataRecord オブジェクト sourceTVPObject ができます。 例では、接続がアクティブな接続オブジェクトが想定しています。  

```java
// Using table-valued parameter with a SQLServerPreparedStatement.  
SQLServerPreparedStatement pStmt =
    (SQLServerPreparedStatement) connection.prepareStatement(“INSERT INTO dbo.Categories SELECT * FROM ?”);  
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);  
pStmt.execute();  
```

```java
// Using table-valued parameter with a SQLServerCallableStatement.  
SQLServerCallableStatement pStmt =
    (SQLServerCallableStatement) connection.prepareCall("exec usp_InsertCategories ?");
pStmt.setStructured(1, "dbo.CategoryTableType", sourceTVPObject);;  
pStmt.execute();  
```

> [!NOTE]  
> セクションを参照して**JDBC Driver のテーブル値パラメーター API**以下のテーブル値パラメーターを設定するために使用できる Api の完全な一覧についてはします。  
  
## <a name="passing-a-table-valued-parameter-as-a-sqlserverdatatable-object"></a>SQLServerDataTable オブジェクトとしてテーブル値パラメーターの受け渡し  

Microsoft JDBC Driver 6.0 for SQL Server 以降、SQLServerDataTable クラスは、リレーショナル データのメモリ内のテーブルを表します。 この例では、SQLServerDataTable オブジェクトを使用してメモリ内データからテーブル値パラメーターを作成する方法を示します。 コードがまず SQLServerDataTable オブジェクトを作成、そのスキーマを定義およびテーブル データに設定します。 コードは、このデータ テーブルをテーブル値パラメーターとして SQL Server に渡される SQLServerPreparedStatement を構成します。  

```java
/* Assumes connection is an active Connection object. */

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
> セクションを参照して**JDBC Driver のテーブル値パラメーター API**以下のテーブル値パラメーターを設定するために使用できる Api の完全な一覧についてはします。  
  
## <a name="passing-a-table-valued-parameter-as-a-resultset-object"></a>結果セット オブジェクトとして、テーブル値パラメーターを渡す  

この例では、結果セットからデータをテーブル値パラメーターの行をストリームする方法を示します。 コードは最初のソース テーブルからデータを取得、SQLServerDataTable オブジェクトを作成し、そのスキーマを定義、テーブルにデータを設定します。 コードは、このデータ テーブルをテーブル値パラメーターとして SQL Server に渡される SQLServerPreparedStatement を構成します。  

```java
/* Assumes connection is an active Connection object. */

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
> セクションを参照して**JDBC Driver のテーブル値パラメーター API**以下のテーブル値パラメーターを設定するために使用できる Api の完全な一覧についてはします。  

## <a name="passing-a-table-valued-parameter-as-an-isqlserverdatarecord-object"></a>ISQLServerDataRecord オブジェクトとしてテーブル値パラメーターの受け渡し  

Microsoft JDBC Driver 6.0 for SQL Server から、新しいインターフェイス ISQLServerDataRecord がストリーミングする方法、ユーザーは、その実装を提供します) にもよりますデータの使用可能なテーブル値パラメーターを使用します。 次の例では、ISQLServerDataRecord インターフェイスを実装する方法と、テーブル値パラメーターとして渡す方法を示します。 わかりやすくするためは、次の例は、ハードコーディングされた値を持つ 1 つの行をテーブル値パラメーターに渡します。 理想的には、ユーザーは、たとえば、テキスト ファイルからの任意のソースから、ストリームの行にこのインターフェイスを実装は。  

```java
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
> セクションを参照して**JDBC Driver のテーブル値パラメーター API**以下のテーブル値パラメーターを設定するために使用できる Api の完全な一覧についてはします。

## <a name="table-valued-parameter-api-for-the-jdbc-driver"></a>JDBC Driver のテーブル値パラメーター API

### <a name="sqlservermetadata"></a>SQLServerMetaData

このクラスは、列のメタデータを表します。 列のメタデータをテーブル値パラメーターに渡す ISQLServerDataRecord インターフェイスで使用されます。 このクラスのメソッドは次のとおりです。  

| [オブジェクト名]                                                                                                                                                                             | [説明]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| パブリック SQLServerMetaData (文字列 columnName, int sqlType、int の有効桁数、int スケール、ブール useServerDefault、ブール isUniqueKey、SQLServerSortOrder sortOrder, int sortOrdinal) | 指定された列名、sql 型、有効桁数、スケールとサーバーの既定の SQLServerMetaData の新しいインスタンスを初期化します。 このフォームのコンス トラクターでは、列が一意で、テーブル値パラメーターで、列と並べ替え列の序数の並べ替え順序を指定することによってテーブル値パラメーターをサポートしています。 <br/><br/>useServerDefault - のかどうか、この列はサーバーの既定値を使用する必要がありますを指定します既定値は false です。<br>isUniqueKey - は、テーブル値パラメーターの列が一意であることを示します既定値は false です。<br>sortOrder -; 列の並べ替え順序を示します既定値は SQLServerSortOrder.Unspecified です。<br>sortOrdinal - 並べ替え、列の序数を指定しますsortOrdinal が 0 から開始します。既定値は-1 です。 |
| パブリック SQLServerMetaData (columnName の文字列、int sqlType)                                                                                                                        | 列名と sql の型を使用して SQLServerMetaData の新しいインスタンスを初期化します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| パブリック SQLServerMetaData (文字列 columnName、sqlType の int、int の有効桁数、int のスケール)                                                                                              | 列名、sql 型、有効桁数、およびスケールを使用して SQLServerMetaData の新しいインスタンスを初期化します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| パブリック SQLServerMetaData (SQLServerMetaData sqlServerMetaData)                                                                                                                    | 別の SQLServerMetaData オブジェクトから SQLServerMetaData の新しいインスタンスを初期化します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| パブリック文字列 getColumName()                                                                                                                                                     | 列名を取得します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| パブリック int getSqlType()                                                                                                                                                          | Java sql 型を取得します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| パブリック int getPrecision()                                                                                                                                                        | 列に渡される型の有効桁数を取得します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| パブリック int getScale()                                                                                                                                                            | 列に渡された型の小数点以下桁数を取得します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| パブリック SQLServerSortOrder getSortOrder()                                                                                                                                         | 並べ替え順序を取得します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| パブリック int getSortOrdinal()                                                                                                                                                      | 並べ替えの序数を取得します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| パブリック ブール isUniqueKey()                                                                                                                                                     | 列が一意かどうかを返します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| パブリック ブール useServerDefault()                                                                                                                                                | サーバーの既定値を返すかどうか、列に使用します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
  
### <a name="sqlserversortorder"></a>SQLServerSortOrder

並べ替え順序を定義する列挙型。 使用可能な値は、Ascending、Descending、未指定です。
  
### <a name="sqlserverdatatable"></a>SQLServerDataTable

このクラスは、テーブル値パラメーターで使用される、メモリ内のデータ テーブルを表します。 このクラスのメソッドは次のとおりです。  

| [オブジェクト名]                                                          | [説明]                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| パブリック SQLServerDataTable()                                   | SQLServerDataTable の新しいインスタンスを初期化します。    |
| 反復子を公開 < エントリ\<整数、object[] >> getIterator()      | データ テーブルの行の反復子を取得します。 |
| パブリックの void addColumnMetadata (columnName の文字列、int sqlType) | 指定された列のメタデータを追加します。              |
| public void addColumnMetadata (SQLServerDataColumn 列)     | 指定された列のメタデータを追加します。              |
| public void addRow (オブジェクトの値では...)                          | データ テーブルに 1 行のデータを追加します。              |
| パブリック マップ\<整数、SQLServerDataColumn > getColumnMetadata() | このデータ テーブルの列のメタデータを取得します。       |
| public void clear()                                           | このデータ テーブルをクリアします。                              |

### <a name="sqlserverdatacolumn"></a>SQLServerDataColumn

このクラスは、SQLServerDataTable で表されるメモリ内のデータ テーブルの列を表します。 このクラスのメソッドは次のとおりです。  

| [オブジェクト名]                                                       | [説明]                                                                      |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------- |
| パブリック SQLServerDataColumn (columnName の文字列、int sqlType) | 列名と型を持つ SQLServerDataColumn の新しいインスタンスを初期化します。 |
| パブリック文字列 getColumnName()                              | 列名を取得します。                                                       |
| パブリック int getColumnType()                                 | 列の型を取得します。                                                       |

### <a name="isqlserverdatarecord"></a>ISQLServerDataRecord

このクラスは、ユーザーは、テーブル値パラメーターにデータをストリーミングに実装できるインターフェイスを表します。 このインターフェイスのメソッドは次のとおりです。  
  
| [オブジェクト名]                                                    | [説明]                                                                                             |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| パブリック SQLServerMetaData getColumnMetaData (int 型の列)。 | 指定された列インデックスの列のメタデータを取得します。                                               |
| パブリック int getColumnCount();                            | 列の合計数を取得します。                                                                  |
| オブジェクトのパブリック getRowData();                           | オブジェクトの配列として、現在の行のデータを取得します。                                          |
| パブリック ブール next();                                  | 次の行に移動します。 移動が成功した場合に次の行で false、それ以外の場合は、True を返します。 |

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

次のメソッドが、テーブル値パラメーターの引き渡しをサポートするためには、このクラスに追加されました。  

| [オブジェクト名]                                                                                                    | [説明]                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| パブリックの最終的な void setStructured (int parameterIndex, 文字列 tvpName, SQLServerDataTable tvpDataTable)    | データ テーブルとテーブル値パラメーターを設定します。 parameterIndex はパラメーターのインデックス、tvpName は、テーブル値パラメーターの名前、tvpDataTable はソース データ テーブル オブジェクトです。                                                                                                          |
| パブリックの最終的な void setStructured (int parameterIndex、文字列 tvpName、ResultSet tvpResultSet)             | 別のテーブルから取得された結果セットには、テーブル値パラメーターを設定します。 parameterIndex はパラメーターのインデックス、tvpName は、テーブル値パラメーターの名前、tvpResultSet はソースの結果セット オブジェクトです。                                                                               |
| パブリックの最終的な void setStructured (int parameterIndex、文字列 tvpName、ISQLServerDataRecord tvpDataRecord) | ISQLServerDataRecord オブジェクトを使用して、テーブル値パラメーターを設定します。 ISQLServerDataRecord データをストリーミングを使用し、ユーザーがその使用方法を決定します。 parameterIndex はパラメーターのインデックス、tvpName は、テーブル値パラメーターの名前、tvpDataRecord は ISQLServerDataRecord オブジェクトです。 |
  
### <a name="sqlservercallablestatement"></a>SQLServerCallableStatement

次のメソッドが、テーブル値パラメーターの引き渡しをサポートするためには、このクラスに追加されました。  
  
| [オブジェクト名]                                                                                                        | [説明]                                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| パブリックの最終的な void setStructured (文字列 paratemeterName, 文字列 tvpName, SQLServerDataTable tvpDataTable)    | データ テーブルとストアド プロシージャに渡されたテーブル値パラメーターを設定します。 paratemeterName にパラメーターの名前も tvpName は TVP、型の名前、tvpDataTable は、データ テーブル オブジェクト。                                                                                                                 |
| パブリックの最終的な void setStructured (文字列 paratemeterName、文字列 tvpName、ResultSet tvpResultSet)             | 別のテーブルから取得された結果セットをストアド プロシージャに渡されたテーブル値パラメーターを設定します。 paratemeterName はパラメーターの名前、tvpName は TVP、型の名前、tvpResultSet はソースする結果セット オブジェクトです。                                                                              |
| パブリックの最終的な void setStructured (文字列 paratemeterName、文字列 tvpName、ISQLServerDataRecord tvpDataRecord) | ISQLServerDataRecord オブジェクトでストアド プロシージャに渡されたテーブル値パラメーターを設定します。 ISQLServerDataRecord データをストリーミングを使用し、ユーザーがその使用方法を決定します。 paratemeterName はパラメーターの名前、tvpName は TVP、型の名前、tvpDataRecord は ISQLServerDataRecord オブジェクトです。 |

## <a name="see-also"></a>参照

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
