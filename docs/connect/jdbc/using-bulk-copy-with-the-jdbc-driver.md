---
title: "JDBC ドライバーで一括コピーの使用 |Microsoft ドキュメント"
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
ms.assetid: 21e19635-340d-49bb-b39d-4867102fb5df
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 4edc1b7348e9b34c924236819f0122ea5277d3e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="using-bulk-copy-with-the-jdbc-driver"></a>JDBC ドライバーでの一括コピーの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Microsoft SQL Server には、という一般的なコマンド ライン ユーティリティが含まれています。 **bcp**の高速で一括 SQL Server データベースのテーブルまたはビューに大きなファイルをコピーします。 SQLServerBulkCopy クラスを使用すると、同様の機能を提供するコード ソリューションを Java で作成できます。 SQL Server テーブルにデータを読み込む方法は他にもありますが (INSERT ステートメントなど)、SQLServerBulkCopy を使用する方が大幅にパフォーマンスが向上します。  
  
 SQLServerBulkCopy クラスは、SQL Server テーブルのみにデータを書き込む場合に使用できます。 ただし、データ ソースは SQL Server に制限されていません。ResultSet、RowSet、または ISQLServerBulkRecord の実装で読み取れるデータであれば、任意のデータ ソースを使用できます。  
  
 SQLServerBulkCopy クラスを使用すると、次の操作を実行できます。  
  
-   単一の一括コピー操作  
  
-   複数の一括コピー操作  
  
-   トランザクション内での一括コピー操作  
  
> [!NOTE]  
>  Microsoft JDBC Driver 4.1 for SQL Server またはそれ以前のバージョン (SQLServerBulkCopy クラスをサポートしていない) を使用する場合、代わりに SQL Server Transact-SQL の BULK INSERT ステートメントを実行できます。  
  
## <a name="bulk-copy-example-setup"></a>一括コピーのセットアップ例  
 SQLServerBulkCopy クラスは、SQL Server テーブルのみにデータを書き込む場合に使用できます。 このトピック内のコード サンプルには、SQL Server のサンプル データベース AdventureWorks が使用されています。 既存のテーブルの改変を防ぐため、コード サンプルでは、別途作成したテーブルにデータを書き込みます。このテーブルを最初に作成しておく必要があります。  
  
 BulkCopyDemoMatchingColumns テーブルと BulkCopyDemoDifferentColumns テーブルは、どちらも AdventureWorks の Production.Products テーブルに基づいたテーブルです。 コード サンプルではこれらのテーブルを使用し、Production.Products テーブルからこれらのサンプル テーブルのいずれかにデータを追加します。 BulkCopyDemoDifferentColumns テーブルは、ソース データからコピー先のテーブルに列をマップする方法を例示するサンプルに使用されます。BulkCopyDemoMatchingColumns は他のサンプルの大部分に使用されます。  
  
 1 つの SQLServerBulkCopy クラスを使用して複数のテーブルに書き込む方法を示すコード サンプルもあります。 これらのサンプルでは、BulkCopyDemoOrderHeader テーブルと BulkCopyDemoOrderDetail テーブルはコピー先のテーブルとして使用されます。 これらのテーブルは、AdventureWorks の Sales.SalesOrderHeader テーブルと Sales.SalesOrderDetail テーブルに基づいたテーブルです。  
  
> [!NOTE]  
>  SQLServerBulkCopy コード サンプルでは、SQLServerBulkCopy のみを使用する構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL INSERT … SELECT ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
###  <a name="BKMK_TableSetup"></a>テーブルのセットアップ  
 コード サンプルを正しく実行するために必要なテーブルを作成するには、SQL Server データベースで次の Transact-SQL ステートメントを実行する必要があります。  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED   
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED   
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED   
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED   
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
```  
  
## <a name="single-bulk-copy-operations"></a>単一のバルク コピー操作  
 SQL Server の一括コピー操作を実行する最も簡単な方法は、データベースに対して単一操作を実行することです。 既定では、一括コピー操作は分離された操作として実行されます。このコピー操作は非トランザクション方式で処理され、ロールバックできません。  
  
> [!NOTE]  
>  ロールバックする一括コピーの一部またはすべてエラーが発生する必要がある場合、SQLServerBulkCopy が管理するトランザクションを使用するか、既存のトランザクション内でバルク コピー操作を実行します。  
>   
>  詳細については、次を参照してください[トランザクションとバルク コピー操作。](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TransactionBulk)  
  
 通常、一括コピー操作の実行手順は次のようになります。  
  
1.  コピー元のサーバーに接続し、コピーするデータを取得します。 データは、ResultSet のオブジェクトまたは ISQLServerBulkRecord の実装から取得できる場合、他のソースからも取得できます。  
  
2.  移行先サーバーに接続 (する場合を除き、 **SQLServerBulkCopy**の接続を確立するため)。  
  
3.  使用して、必要なプロパティを設定、SQLServerBulkCopy オブジェクトを作成**setBulkCopyOptions**です。  
  
4.  呼び出す、 **setDestinationTableName**一括の対象テーブルを示すためにメソッドが操作を挿入します。  
  
5.  1 つを呼び出して、 **writeToServer**メソッドです。  
  
6.  必要に応じて、経由でプロパティを更新**setBulkCopyOptions**を呼び出すと**writeToServer**必要に応じて、もう一度です。  
  
7.  呼び出す**閉じる**、または try のリソースでのステートメント内で一括コピー操作をラップします。  
  
> [!CAUTION]  
>  コピー元とコピー先の列のデータ型を一致させることをお勧めします。 データ型が一致しない場合、SQLServerBulkCopy はコピー元のそれぞれの値をコピー先のデータ型に変換しようとします。 この変換はパフォーマンスに影響を及ぼすだけでなく、予期しないエラーが発生する場合もあります。 たとえば、double データ型はたいていの場合 decimal データ型に変換できますが、変換できない場合もあります。  
  
### <a name="example"></a>例  
 次のアプリケーションでは、SQLServerBulkCopy クラスを使用してデータを読み込む方法を示します。 この例では、ResultSet を使用し、SQL Server の AdventureWorks データベースに格納された Production.Product テーブルのデータを、同じデータベース内の同等のテーブルにコピーします。  
  
> [!IMPORTANT]  
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[テーブルのセットアップ](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup)です。 このコードでは、SQLServerBulkCopy のみを使用する構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL INSERT … SELECT ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    // Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
                        // Open the destination connection. In the real world you would    
                        // not use SQLServerBulkCopy to move data from one table to the other    
                        // in the same database. This is for demonstration purposes only.   
                        try (Connection destinationConnection =   
                                DriverManager.getConnection(connectionString))  
                        {  
                            // Set up the bulk copy object.    
                            // Note that the column positions in the source   
                            // table match the column positions in    
                            // the destination table so there is no need to   
                            // map columns.   
                            try (SQLServerBulkCopy bulkCopy =  
                                       new SQLServerBulkCopy(destinationConnection))  
                            {  
                                bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                                try  
                                {  
                                    // Write from the source to the destination.  
                                    bulkCopy.writeToServer(rsSourceData);  
                                }  
                                catch (Exception e)  
                                {  
                                    // Handle any errors that may have occurred.  
                                    e.printStackTrace();  
                                }  
                            }  
  
                            // Perform a final count on the destination    
                            // table to see how many rows were added.  
                            try (ResultSet rsRowCount = stmt.executeQuery(  
                                    "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                            {  
                                rsRowCount.next();  
                                long countEnd = rsRowCount.getInt(1);  
                                System.out.println("Ending row count = " + countEnd);  
                                System.out.println((countEnd - countStart) + " rows were added.");  
                            }  
                        }  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
           "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
```  
  
### <a name="performing-a-bulk-copy-operation-using-transact-sql"></a>Transact-SQL を使用した一括コピー操作の実行  
 次の例では、BULK INSERT ステートメントを実行する executeUpdate メソッドの使用方法を説明します。  
  
> [!NOTE]  
>  データ ソースのファイル パスはサーバーに対する相対パスです。 一括コピー操作を正常に実行するには、サーバー プロセスがこのパスにアクセスできる必要があります。  
  
```  
try (Connection con = DriverManager.getConnection(connectionString))  
{  
    try (Statement stmt = con.createStatement())  
    {  
        // Perform the BULK INSERT  
        stmt.executeUpdate(  
                "BULK INSERT Northwind.dbo.[Order Details] " +  
                        "FROM 'f:\\mydata\\data.tbl' " +  
                        "WITH ( FORMATFILE='f:\\mydata\\data.fmt' )");  
    }  
}  
```  
  
## <a name="multiple-bulk-copy-operations"></a>複数の一括コピー操作  
 SQLServerBulkCopy クラスの単一のインスタンスを使用して、一括コピー操作を複数回実行できます。 コピー元とコピー先で操作パラメーターが変わる場合 (たとえば、コピー先のテーブル名など)、WriteToServer メソッドを続けて呼び出す前に、次の例で示すようにパラメーターを更新する必要があります。 明示的に変更した場合を除き、すべてのプロパティ値は、任意のインスタンスに対して前回一括コピー操作を実行したときと同じ状態のままになっています。  
  
> [!NOTE]  
>  通常、一括コピー操作を複数回実行する場合は、同じ SQLServerBulkCopy のインスタンスを使用する方が各操作ごとに別のインスタンスを使用するよりも効率的です。  
  
 同じ SQLServerBulkCopy オブジェクトを使用して一括コピー操作を複数回実行する場合、コピー元またはコピー先の情報が各操作ごとに一致しているか異なっているかに関する制限はありません。 ただし、サーバーに書き込み処理を行うときは、列の関連付け情報を毎回正しく設定する必要があります。  
  
> [!IMPORTANT]  
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[テーブルのセットアップ](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup)です。 このコードでは、SQLServerBulkCopy のみを使用する構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL INSERT … SELECT ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection1 = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection1.createStatement())  
                {  
  
                    // Empty the destination tables.   
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoOrderHeader;");  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoOrderDetail;");  
  
                    // Perform an initial count on the destination   
                    //  table with matching columns.  
                    long countStartHeader = 0;  
                    try (ResultSet rsRowCountHeader = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderHeader;"))  
                    {  
                        rsRowCountHeader.next();  
                        countStartHeader = rsRowCountHeader.getInt(1);  
                        System.out.println("Starting row count for Header table = " + countStartHeader);  
                    }  
  
                    // Perform an initial count on the destination   
                    // table with different column positions.  
                    long countStartDetail = 0;  
                    try (ResultSet rsRowCountDetail = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderDetail;"))  
                    {  
                        rsRowCountDetail.next();  
                        countStartDetail = rsRowCountDetail.getInt(1);  
                        System.out.println("Starting row count for Detail table = " + countStartDetail);  
                    }  
  
                    // Get data from the source table as a ResultSet.   
                    // The Sales.SalesOrderHeader and Sales.SalesOrderDetail   
                    // tables are quite large and could easily cause a timeout   
                    // if all data from the tables is added to the destination.    
                    // To keep the example simple and quick, a parameter is     
                    // used to select only orders for a particular account    
                    // as the source for the bulk insert.  
                    try (PreparedStatement preparedStmt1 = sourceConnection1.prepareStatement(  
                            "SELECT [SalesOrderID], [OrderDate], " +  
                            "[AccountNumber] FROM [Sales].[SalesOrderHeader] " +  
                            "WHERE [AccountNumber] = ?;"))  
                    {  
                        preparedStmt1.setString(1, "10-4020-000034");  
  
                        try (ResultSet rsHeader = preparedStmt1.executeQuery())  
                        {  
                            // Get the Detail data in a separate connection.   
                            try (Connection sourceConnection2 = DriverManager.getConnection(connectionString))  
                            {  
                                try (PreparedStatement preparedStmt2 = sourceConnection2.prepareStatement(  
                                        "SELECT [Sales].[SalesOrderDetail].[SalesOrderID], " +  
                                                "[SalesOrderDetailID], [OrderQty], [ProductID], " +  
                                                "[UnitPrice] FROM [Sales].[SalesOrderDetail] " +  
                                                "INNER JOIN [Sales].[SalesOrderHeader] " +  
                                                "ON [Sales].[SalesOrderDetail].[SalesOrderID] " +  
                                                "= [Sales].[SalesOrderHeader].[SalesOrderID] " +  
                                                "WHERE [AccountNumber] = ?;"))  
                                {  
                                    preparedStmt2.setString(1, "10-4020-000034");  
  
                                    try (ResultSet rsDetail = preparedStmt2.executeQuery())  
                                    {  
                                        // Create the SQLServerBulkCopySQLServerBulkCopy object.    
                                        try (SQLServerBulkCopy bulkCopy =  
                                                   new SQLServerBulkCopy(connectionString))  
                                        {  
                                            bulkCopy.setBulkCopyOptions(copyOptions);  
                                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoOrderHeader");  
  
                                            // Guarantee that columns are mapped correctly by   
                                            // defining the column mappings for the order.  
                                            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");  
                                            bulkCopy.addColumnMapping("OrderDate", "OrderDate");  
                                            bulkCopy.addColumnMapping("AccountNumber", "AccountNumber");  
  
                                            // Write rsHeader to the destination.   
                                            try  
                                            {  
                                                bulkCopy.writeToServer(rsHeader);  
                                            }  
                                            catch (Exception e)  
                                            {  
                                                // Handle any errors that may have occurred.  
                                                e.printStackTrace();  
                                            }  
  
                                            // Set up the order details destination.   
                                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoOrderDetail");  
  
                                            // Clear the existing column mappings  
                                            bulkCopy.clearColumnMappings();  
  
                                            // Add order detail column mappings.  
                                            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");  
                                            bulkCopy.addColumnMapping(  
                                                    "SalesOrderDetailID",   
                                                    "SalesOrderDetailID");  
                                            bulkCopy.addColumnMapping("OrderQty", "OrderQty");  
                                            bulkCopy.addColumnMapping("ProductID", "ProductID");  
                                            bulkCopy.addColumnMapping("UnitPrice", "UnitPrice");  
  
                                            // Write rsDetail to the destination.   
                                            try  
                                            {  
                                                bulkCopy.writeToServer(rsDetail);  
                                            }  
                                            catch (Exception e)  
                                            {  
                                                // Handle any errors that may have occurred.  
                                                e.printStackTrace();  
                                            }  
                                        }  
                                    }  
                                }  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination   
                    // tables to see how many rows were added.  
                    try (ResultSet rsRowCountHeader = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderHeader;"))  
                    {  
                        rsRowCountHeader.next();  
                        long countEndHeader =  rsRowCountHeader.getInt(1);  
                        System.out.println(  
                                (countEndHeader - countStartHeader) +   
                                " rows were added to the Header table.");  
                    }  
  
                    try (ResultSet rsRowCountDetail = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderDetail;"))  
                    {  
                        rsRowCountDetail.next();  
                        long countEndDetail = rsRowCountDetail.getInt(1);  
                        System.out.println(  
                                (countEndDetail - countStartDetail) +   
                                " rows were added to the Detail table.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;"  
                + "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
  
```  
  
##  <a name="BKMK_TransactionBulk"></a>トランザクションとバルク コピー操作  
 一括コピー操作は、単独の操作として、または、複数の手順からなるトランザクションの一部として実行されます。 複数の手順からなるトランザクションの一部として実行する場合、挿入、更新、削除など、他のデータベース操作に加えて、同じトランザクション内で一括コピー操作を複数回実行でき、トランザクション全体をコミットまたはロールバックすることもできます。  
  
 既定では、一括コピー操作は単独の操作として実行されます。 この一括コピー操作は非トランザクション方式で処理され、ロールバックできません。 エラーの発生時に一括コピー処理の全部または一部をロールバックする必要がある場合は、SQLServerBulkCopy が管理するトランザクションを使用するか、既存のトランザクション内で一括コピー操作を実行できます。  
  
### <a name="performing-a-non-transacted-bulk-copy-operation"></a>非トランザクション処理の一括コピー操作の実行  
 次のアプリケーションでは、非トランザクション処理の一括コピー操作で操作途中にエラーが発生した場合の処理を示しています。  
  
 例では、ソース テーブルとコピー先のテーブルは、それぞれ含めるという名前、Id 列**ProductID**です。 コードがすべての行を削除することによって最初に、変換先テーブルを準備し、行行、1 つを挿入**ProductID**ソース テーブルに存在しています。 既定では、行が追加されるたびに、コピー先のテーブル内の ID 列に新しい値が生成されます。 この例では、一括読み込み処理でコピー元のテーブルの ID 値を強制的に使用する接続が開かれるときに、オプションが設定されます。  
  
 一括コピー操作を実行すると、 **BatchSize**プロパティを 10 に設定します。 操作中に無効な行が検出されると、例外がスローされます。 次に示す最初の例の一括コピー操作はトランザクション処理ではありません。 エラー発生ポイントまでにコピーされたバッチはすべてコミットされ、重複キーが含まれるバッチはロールバックされます。また、一括コピー操作は、他のバッチを処理する前に中止されます。  
  
> [!NOTE]  
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[テーブルのセットアップ](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup)です。 このコードでは、SQLServerBulkCopy のみを使用する構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL INSERT … SELECT ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    //  Delete all from the destination table.  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoMatchingColumns");  
  
                    //  Add a single row that will result in duplicate key            
                    //  when all rows from source are bulk copied.            
                    //  Note that this technique will only be successful in             
                    //  illustrating the point if a row with ProductID = 446              
                    //  exists in the AdventureWorks Production.Products table.             
                    //  If you have made changes to the data in this table, change            
                    //  the SQL statement in the code to add a ProductID that            
                    //  does exist in your version of the Production.Products            
                    //  table. Choose any ProductID in the middle of the table            
                    //  (not first or last row) to best illustrate the result.  
                    stmt.executeUpdate("SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns ON;" +  
                            "INSERT INTO " + "dbo.BulkCopyDemoMatchingColumns " +  
                            "([ProductID], [Name] ,[ProductNumber]) " +  
                            "VALUES(446, 'Lock Nut 23','LN-3416');" +  
                            "SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns OFF");  
  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    //  Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
  
                        // Set up the bulk copy object using the KeepIdentity option and BatchSize = 10.  
                        SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();  
                        copyOptions.setKeepIdentity(true);  
                        copyOptions.setBatchSize(10);  
  
                        try (SQLServerBulkCopy bulkCopy =   
                                new SQLServerBulkCopy(connectionString))  
                        {  
                            bulkCopy.setBulkCopyOptions(copyOptions);  
                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                            // Write from the source to the destination.   
                            // This should fail with a duplicate key error   
                            // after some of the batches have been copied.   
                            try  
                            {  
                                bulkCopy.writeToServer(rsSourceData);  
                            }  
                            catch (Exception e)  
                            {  
                                // Handle any errors that may have occurred.  
                                e.printStackTrace();  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection String.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
              "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
```  
  
### <a name="performing-a-dedicated-build-copy-operation-in-a-transaction"></a>トランザクションでの専用の一括コピー操作の実行  
 既定では、一括コピー操作は専用のトランザクションで実行されます。 専用の一括コピー操作を実行する場合は、接続文字列を使用して SQLServerBulkCopy の新しいインスタンスを作成します。 このシナリオでは、一括コピー操作でトランザクションを作成し、その後、トランザクションをコミットするかロールバックします。 明示的に指定することができます、 **UseInternalTransaction**オプション**SQLServerBulkCopyOptions**一括の各バッチの独自のトランザクションで実行するための一括コピー操作を明示的に発生するにはコピー操作は、別のトランザクション内で実行します。  
  
> [!NOTE]  
>  異なるバッチは別々のトランザクション内で実行されます。このため、一括コピー操作中にエラーが発生した場合、現在処理中のバッチの行はすべてロールバックされますが、エラー発生より前のバッチでコピーされた行はデータベースに残ります。  
  
 次のアプリケーションは、前の例と似ていますが、一括コピー操作で専用のトランザクションを管理している点が異なります。 エラー発生ポイントまでにコピーされたバッチはすべてコミットされ、重複キーが含まれるバッチはロールバックされます。また、一括コピー操作は、他のバッチを処理する前に中止されます。  
  
> [!NOTE]  
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[テーブルのセットアップ](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup)です。 このコードでは、SQLServerBulkCopy のみを使用する構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL INSERT … SELECT ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    //  Delete all from the destination table.  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoMatchingColumns");  
  
                    //  Add a single row that will result in duplicate key            
                    //  when all rows from source are bulk copied.            
                    //  Note that this technique will only be successful in             
                    //  illustrating the point if a row with ProductID = 446              
                    //  exists in the AdventureWorks Production.Products table.             
                    //  If you have made changes to the data in this table, change            
                    //  the SQL statement in the code to add a ProductID that            
                    //  does exist in your version of the Production.Products            
                    //  table. Choose any ProductID in the middle of the table            
                    //  (not first or last row) to best illustrate the result.  
                    stmt.executeUpdate("SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns ON;" +  
                            "INSERT INTO " + "dbo.BulkCopyDemoMatchingColumns " +  
                            "([ProductID], [Name] ,[ProductNumber]) " +  
                            "VALUES(446, 'Lock Nut 23','LN-3416');" +  
                            "SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns OFF");  
  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    //  Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
  
                        // Set up the bulk copy object.  
                        // Note that when specifying the UseInternalTransaction   
                        // option, you cannot also use an external transaction.   
                        // Therefore, you must use the SQLServerBulkCopy construct that   
                        // requires a string for the connection, rather than an   
                        // existing Connection object.   
                        SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();  
                        copyOptions.setKeepIdentity(true);  
                        copyOptions.setBatchSize(10);  
                        copyOptions.setUseInternalTransaction(true);  
  
                        try (SQLServerBulkCopy bulkCopy =   
                                new SQLServerBulkCopy(connectionString))  
                        {  
                            bulkCopy.setBulkCopyOptions(copyOptions);  
                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                            // Write from the source to the destination.   
                            // This should fail with a duplicate key error   
                            // after some of the batches have been copied.   
                            try  
                            {  
                                bulkCopy.writeToServer(rsSourceData);  
                            }  
                            catch (Exception e)  
                            {  
                                // Handle any errors that may have occurred.  
                                e.printStackTrace();  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;"  
                + "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
```  
  
### <a name="using-existing-transactions"></a>既存のトランザクションの使用  
 パラメーターとして有効になっているトランザクションを含む接続オブジェクトを SQLServerBulkCopy コンストラクター内で渡すことができます。 この場合、一括コピー操作は既存のトランザクションで実行され、このトランザクションの状態は変更されません (つまり、コミットも中止もされません)。 これにより、アプリケーションは他のデータベース操作を行うトランザクションで一括コピー操作を実行できます。 エラーが発生したため一括コピー操作全体をロールバックする必要がある場合、またはロールバック可能な大きな処理の一部として一括コピー処理を実行する場合、一括コピー操作の開始後いつでも接続オブジェクト上でロールバックを実行できます。  
  
 次のアプリケーションは、最初の (トランザクションのない) 例とほぼ同じですが、一括コピー操作がより大きな外部トランザクションに含まれている点が異なります。 主キー違反エラーが発生した場合、トランザクション全体がロールバックされ、コピー先のテーブルに行は追加されません。  
  
> [!NOTE]  
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[テーブルのセットアップ](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup)です。 このコードでは、SQLServerBulkCopy のみを使用する構文について説明します。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL INSERT … SELECT ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    //  Delete all from the destination table.  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoMatchingColumns");  
  
                    //  Add a single row that will result in duplicate key            
                    //  when all rows from source are bulk copied.            
                    //  Note that this technique will only be successful in             
                    //  illustrating the point if a row with ProductID = 446              
                    //  exists in the AdventureWorks Production.Products table.             
                    //  If you have made changes to the data in this table, change            
                    //  the SQL statement in the code to add a ProductID that            
                    //  does exist in your version of the Production.Products            
                    //  table. Choose any ProductID in the middle of the table            
                    //  (not first or last row) to best illustrate the result.  
                    stmt.executeUpdate("SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns ON;" +  
                            "INSERT INTO " + "dbo.BulkCopyDemoMatchingColumns " +  
                            "([ProductID], [Name] ,[ProductNumber]) " +  
                            "VALUES(446, 'Lock Nut 23','LN-3416');" +  
                            "SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns OFF");  
  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    //  Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
  
                        // Set up the bulk copy object inside the transaction.  
                        try (Connection destinationConnection =   
                                DriverManager.getConnection(connectionString))  
                        {  
                            destinationConnection.setAutoCommit(false);  
  
                            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();  
                            copyOptions.setKeepIdentity(true);  
                            copyOptions.setBatchSize(10);  
  
                            try (SQLServerBulkCopy bulkCopy =   
                                    new SQLServerBulkCopy(destinationConnection))  
                            {  
                                bulkCopy.setBulkCopyOptions(copyOptions);  
                                bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                                // Write from the source to the destination.   
                                // This should fail with a duplicate key error.   
                                try  
                                {  
                                    bulkCopy.writeToServer(rsSourceData);  
                                    destinationConnection.commit();  
                                }  
                                catch (Exception e)  
                                {  
                                    // Handle any errors that may have occurred.  
                                    e.printStackTrace();  
                                    destinationConnection.rollback();  
                                }  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;"  
                + "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
  
```  
  
### <a name="bulk-copy-from-a-csv-file"></a>CSV ファイルからの一括コピー  
 次のアプリケーションでは、SQLServerBulkCopy クラスを使用してデータを読み込む方法を示します。 この例では、CSV ファイルを使用し、SQL Server の AdventureWorks データベース内の Production.Product テーブルからエクスポートされたデータを、このデータベース内の同等のテーブルにコピーします。  
  
> [!IMPORTANT]  
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[テーブルのセットアップ](../../ssms/download-sql-server-management-studio-ssms.md)それを取得します。  
  
1.  開いている**SQL Server Management Studio**し、AdventureWorks データベースで SQL Server に接続します。  
  
2.  データベースを展開し、AdventureWorks データベースを右クリックして、選択**タスク**と**データのエクスポート**しています.  
  
3.  データ ソースの選択、**データソース**、SQL Server (例: SQL Server Native Client 11.0) に接続し、構成を確認することができ、 **[次へ]**  
  
4.  バックアップ先として、次のように選択します。、**フラット ファイル変換先**を入力し、**ファイル名**C:\Test\TestBulkCSVExample.csv などの対象とします。 確認、**形式**区切られた、**テキスト修飾子**は none、および有効にする**先頭データ行の列名**、し、 **次へ**  
  
5.  選択**を転送するデータを指定するクエリを記述**と**次**です。  入力、 **SQL ステートメント**選択 ProductID、Name、ProductNumber FROM Production.Product と**[次へ]**  
  
6.  構成の確認: 行区切り記号を {CR}{LF}、列区切り記号をコンマ {,} にしておくことができます。  選択**マッピングを編集する**しています. 確認し、データ**型**(整数型、他の ProductID と Unicode の文字列の) の各列に適切な。  
  
7.  進んで**完了**エクスポートを実行します。  
  
```  
  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCSVFileRecord;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        SQLServerBulkCSVFileRecord fileRecord = null;  
        try  
        {              
            // Get data from the source file by loading it into a class that implements ISQLServerBulkRecord.  
            // Here we are using the SQLServerBulkCSVFileRecord implementation to import the example CSV file.  
            fileRecord = new SQLServerBulkCSVFileRecord("C:\\Test\\TestBulkCSVExample.csv", true);      
  
            // Set the metadata for each column to be copied.  
            fileRecord.addColumnMetadata(1, null, java.sql.Types.INTEGER, 0, 0);  
            fileRecord.addColumnMetadata(2, null, java.sql.Types.NVARCHAR, 50, 0);  
            fileRecord.addColumnMetadata(3, null, java.sql.Types.NVARCHAR, 25, 0);  
  
            // Open a destinationConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection destinationConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = destinationConnection.createStatement())  
                {  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    // Set up the bulk copy object.    
                    // Note that the column positions in the source   
                    // data reader match the column positions in    
                    // the destination table so there is no need to   
                    // map columns.   
                    try (SQLServerBulkCopy bulkCopy =  
                               new SQLServerBulkCopy(destinationConnection))  
                    {  
                        bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                        try  
                        {  
                            // Write from the source to the destination.  
                            bulkCopy.writeToServer(fileRecord);  
                        }  
                        catch (Exception e)  
                        {  
                            // Handle any errors that may have occurred.  
                            e.printStackTrace();  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
        finally  
        {  
            if (fileRecord != null) try { fileRecord.close(); } catch(Exception e) {}  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
           "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
  
```  
  
### <a name="bulk-copy-with-always-encrypted-columns"></a>Always Encrypted の列を含む一括コピー  
 Microsoft JDBC Driver 6.0 for SQL Server から始まり、Always Encrypted の列を含む一括コピーはサポートされています。  
  
 一括コピー オプションと暗号化によって、JDBC ドライバーは透過的に暗号化解除し、や、データを暗号化し、ソースとターゲット テーブルの種類は、暗号化されたデータをそのままを送信できます。 たとえば、一括暗号化されていない列を暗号化された列からデータをコピーする場合、ドライバー透過的に暗号化解除データ SQL Server に送信する前にします。 同様に一括暗号化された列にデータを暗号化されていない列 (または CSV ファイル) にコピーする場合、ドライバー透過的に暗号化データ SQL Server に送信する前にします。 ソースの両方と、変換先が暗号化されて、しに応じて、 **allowEncryptedValueModifications**一括コピー オプションでは、ドライバーはデータとして送信されますか、データの暗号化を解除して、SQL Server に送信する前に暗号化します。  
  
 詳細については、次を参照してください。、 **allowEncryptedValueModifications**一括コピー オプション、下と[JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)です。  
  
> [!IMPORTANT]  
>  一括暗号化された列に、CSV ファイルからデータをコピーする場合、SQL Server 用 Microsoft JDBC Driver 6.0 の制限:  
>   
>  日付と時刻型に対してのみ TRANSACT-SQL 既定の文字列リテラル形式がサポートされています。  
>   
>  DATETIME および SMALLDATETIME データ型はサポートされていません  
  
## <a name="bulk-copy-api-for-jdbc-driver"></a>JDBC ドライバー用 API の一括コピー  
  
### <a name="sqlserverbulkcopy"></a>SQLServerBulkCopy  
 別のソースからのデータを含む SQL Server テーブルを効率的に一括読み込みできます。  
  
 Microsoft SQL Server には、単一のサーバー上または複数のサーバー間で、テーブルから別のテーブルへデータを移動するための bcp という一般的なコマンド プロンプト ユーティリティが用意されています。 SQLServerBulkCopy クラスを使用すると、同様の機能を提供するコード ソリューションを Java で記述できます。 SQL Server テーブルにデータを読み込む方法は他にもありますが(INSERT ステートメントなど)、SQLServerBulkCopy を使用する方が大幅にパフォーマンスが向上します。  
  
 SQLServerBulkCopy クラスは、SQL Server テーブルのみにデータを書き込む場合に使用できます。 ただし、データ ソースが SQL Server に制限されているわけではありません。ResultSet インスタンスか ISQLServerBulkRecord の実装で読み取れるデータであれば、任意のデータ ソースを使用できます。  
  
|コンス トラクター|Description|  
|-----------------|-----------------|  
|SQLServerBulkCopy(Connection)|SQLServerConnection の指定されたオープン インスタンスを使用して、SQLServerBulkCopy クラスの新しいインスタンスを初期化します。 接続でトランザクションが有効になっている場合、コピー操作はそのトランザクション内で実行されます。|  
|SQLServerBulkCopy (文字列 connectionURL)|初期化して、指定された connectionURL に基づき、SQLServerConnection の新しいインスタンスを開きます。 コンス トラクターは、SQLServerBulkCopy クラスの新しいインスタンスを初期化するために、SQLServerConnection を使用します。|  
  
|プロパティ|Description|  
|--------------|-----------------|  
|文字列 DestinationTableName|サーバー上にあるコピー先のテーブルの名前。<br /><br /> DestinationTableName が設定されていない場合、WriteToServer が呼び出されると、SQLServerException がスローされます。<br /><br /> DestinationTableName は、3 部構成の名前 (\<データベース >.\<owningschema >。\<名 >)。 必要に応じ、テーブル名をデータベースと所有しているスキーマで修飾することができます。 ただし、テーブル名にアンダースコア ("_") またはその他の特殊文字を使用する場合は、角かっこで囲んで、名前をエスケープする必要があります。 詳細については、SQL Server オンライン ブックの「識別子」をご覧ください。|  
|ColumnMappings|列のマッピングでは、データ ソース内の列とコピー先の列の間の関係を定義します。<br /><br /> マッピングが定義されていない場合、列は序数の位置に基づいて暗黙的にマップされます。 これを行うには、コピー元のスキーマとコピー先のスキーマが一致する必要があります。 一致しない場合、例外がスローされます。<br /><br /> マッピングが空でない場合、データ ソースに存在するすべての列を指定する必要はありません。 マップされていない列は無視されます。<br /><br /> コピー元とコピー先の列は、名前か序数のいずれかで参照できます。|  
  
|方法|Description|  
|------------|-----------------|  
|AddColumnMapping ((int sourceColumn、int destinationColumn) を無効にします。|序数を使用してコピー元とコピー先の両方の列を指定する、新しい列マッピングを追加します。|  
|AddColumnMapping ((int sourceColumn、文字列の destinationColumn) を無効にします。|コピー元の列の序数とコピー先の列の列名を使用する、新しい列マッピングを追加します。|  
|AddColumnMapping ((文字列 sourceColumn、int destinationColumn) を無効にします。|コピー元の列を説明する列名とコピー先の列を指定する序数を使用する、新しい列マッピングを追加します。|  
|AddColumnMapping (文字列 sourceColumn、文字列の destinationColumn) を無効にします。|列名を使用してコピー元とコピー先の両方の列を指定する、新しい列マッピングを追加します。|  
|Void clearColumnMappings()|列マッピングの内容を消去します。|  
|Close() を無効にします。|SQLServerBulkCopy インスタンスを閉じます。|  
|SQLServerBulkCopyOptions getBulkCopyOptions()|SQLServerBulkCopyOptions の現在のセットを取得します。|  
|文字列 getDestinationTableName()|現在のコピー先テーブル名を取得します。|  
|Void setBulkCopyOptions(SQLServerBulkCopyOptions copyOptions)|指定したオプションに従って SQLServerBulkCopy インスタンスの動作を更新します。|  
|Void setDestinationTableName(String tableName)|コピー先テーブルの名前を設定します。|  
|Void writeToServer(ResultSet sourceData)|SQLServerBulkCopy オブジェクトの DestinationTableName プロパティで指定された宛先のテーブルに、指定された ResultSet 内のすべての行をコピーします。|  
|Void writeToServer(RowSet sourceData)|SQLServerBulkCopy オブジェクトの DestinationTableName プロパティで指定されたコピー先テーブルに、指定された RowSet 内のすべての行をコピーします。|  
|Void writeToServer(ISQLServerBulkRecord sourceData)|SQLServerBulkCopy オブジェクトの DestinationTableName プロパティで指定された宛先のテーブルに指定された ISQLServerBulkRecord 実装内のすべての行をコピーします。|  
  
### <a name="sqlserverbulkcopyoptions"></a>SQLServerBulkCopyOptions  
 SQLServerBulkCopy インスタンス内の writeToServer メソッドの動作を制御する設定のコレクション。  
  
|コンス トラクター|Description|  
|-----------------|-----------------|  
|SQLServerBulkCopyOptions()|すべての設定の既定値を使用して SQLServerBulkCopyOptions クラスの新しいインスタンスを初期化します。|  
  
 get アクセス操作子および set アクセス操作子は、次のオプションのために存在します。  
  
|オプション|Description|既定値|  
|------------|-----------------|-------------|  
|ブール CheckConstraints|データが挿入される際の制約をチェックします。|False - 制約はチェックされません|  
|ブール FireTriggers|このオプションを指定すると、データベースに挿入される行に対する挿入トリガーがサーバーで発生します。|False - トリガーは発生しません。|  
|ブール KeepIdentity|ソースの ID 値が保持されます。|False - コピー先により ID 値が割り当てられます|  
|ブール KeepNulls|既定値の設定に関係なく、コピー先のテーブル内の null 値が保持されます。|False - 該当する個所で、null 値は既定値で置き換えられます。|  
|ブール TableLock|一括コピー操作の実行中、一括更新のロックを取得します。|False - 行ロックが使用されます。|  
|ブール UseInternalTransaction|指定した場合、一括コピー操作の各バッチがトランザクション内で発生します。 SQLServerBulkCopy がコンストラクターで指定されている既存の接続を使用する場合、SQLServerException が発生します。  SQLServerBulkCopy で専用の接続が作成された場合、トランザクションが有効になります。|False - トランザクションなし|  
|Int BatchSize|各バッチに含まれる行数。 各バッチの最後に、バッチ内の行がサーバーに送信されます。<br /><br /> BatchSize 分の行が処理されるか、コピー先のデータ ソースに送信する行がなくなると、バッチは完了します。  UseInternalTransaction オプションを有効にせず、SQLServerBulkCopy インスタンスが宣言されている場合、行はサーバーの BatchSize 行に一度に送信されますが、トランザクション関連のアクションは実行されません。 UseInternalTransaction が有効になっている場合は、行の各バッチが個別のトランザクションとして挿入されます。|0 - 各 writeToServer 操作が 1 つのバッチであることを示します|  
|Int BulkCopyTimeout|タイムアウトになる前に完了する操作の秒数。値 0 は無制限を意味しており、一括コピーは無期限に待機します。|60 秒。|  
|ブール allowEncryptedValueModifications|このオプションは使用可能な Microsoft JDBC Driver 6.0 (またはそれ以上) for SQL Server です。<br /><br /> 指定した場合、 **allowEncryptedValueModifications**一括がデータの暗号化を解除せずにテーブルまたはデータベース間で暗号化されたデータのコピーを有効にします。 通常、アプリケーションでは、(アプリはデータベースへの接続で、列暗号化のキーワード設定を無効になっています)、データの暗号化を解除せず 1 つのテーブルから暗号化された列からデータを選択し、し、このオプションを使用、一括挿入をまだ暗号化されているデータ。 詳細については、次を参照してください。 [JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)です。<br /><br /> 指定する場合に警告を使用して**allowEncryptedValueModifications**ドライバーはかどうか、データが実際に暗号化されてを参照しないため、データベースが破損する可能性が、または同じの暗号化を使用して正しく暗号化されている場合型、アルゴリズムとキーが対象列とします。||  
  
 Get アクセス操作子および set アクセス操作子:  
  
|メソッド|Description|  
|-------------|-----------------|  
|ブール isCheckConstraints()|制約かデータの挿入中にチェックするかどうかを示します。|  
|Void setCheckConstraints(Boolean checkConstraints)|制約かデータの挿入中にチェックするかどうかを設定します。|  
|ブール isFireTriggers()|サーバーがデータベースに挿入される行の挿入トリガーを起動するかどうかを示します。|  
|Void setFireTriggers(Boolean fireTriggers)|データベースに挿入される行のトリガーを起動するサーバーを設定する必要があるかどうかを設定します。|  
|ブール isKeepIdentity()|任意のソース id 値を保持するかどうかを示します。|  
|Void setKeepIdentity(Boolean keepIdentity)|Id 値を保持するかどうかを設定します。|  
|ブール isKeepNulls()|既定値の設定に関係なく、変換先テーブル内の null 値を保持するかどうか、またはかどうかは、置き換える必要があります、既定値 (ある場合) を示します。|  
|Void setKeepNulls(Boolean keepNulls)|かどうか、既定値の設定に関係なく、変換先テーブル内の null 値を保持するかどうかは、置き換える必要があります、既定値 (ある場合) を設定します。|  
|ブール isTableLock()|SQLServerBulkCopy が一括コピー操作の間で一括更新ロックを取得する必要があるかどうかを示します。|  
|Void setTableLock(Boolean tableLock)|SQLServerBulkCopy が一括コピー操作の実行中で一括更新ロックを取得する必要があるかどうかを設定します。|  
|ブール isUseInternalTransaction()|一括コピー操作の各バッチがトランザクション内で発生するかどうかを示します。|  
|Void setUseInternalTranscation(Boolean useInternalTransaction)|かは、一括コピー操作の各バッチをトランザクション内で発生するかどうかを設定します。|  
|Int getBatchSize()|各バッチ内の行の数を取得します。 各バッチの最後に、バッチ内の行がサーバーに送信されます。|  
|Void setBatchSize(int batchSize)|各バッチの行の数を設定します。 各バッチの最後に、バッチ内の行がサーバーに送信されます。|  
|Int getBulkCopyTimeout()|タイムアウトになる前に完了する操作の秒数を取得します。|  
|Void setBulkCopyTimeout(int timeout)|タイムアウトになる前に完了する操作の秒数を設定します。|  
|ブール isAllowEncryptedValueModifications()|AllowEncryptedValueModifications 設定を有効または無効になっているかどうかを示します。|  
|void setAllowEncryptedValueModifications(boolean allowEncryptedValueModifications)|Always Encrypted の列を含む一括コピーのために使用される、allowEncryptedValueModifications 設定を構成します。|  
  
### <a name="isqlserverbulkrecord"></a>ISQLServerBulkRecord  
 ISQLServerBulkRecord インターフェイスを使用すると、ファイルなどの任意のソースからデータを読み取るクラスを作成して、SQLServerBulkCopy インスタンスでそのデータを含む SQL Server テーブルを一括して読み込むことができます。  
  
|インターフェイス メソッド|Description|  
|-----------------------|-----------------|  
|設定\<整数 > getColumnOrdinals()|このデータ レコード内に表示される各列の序数を取得します。|  
|文字列 getColumnName(int column)|指定した列の名前を取得します。|  
|Int getColumnType (int 型の列)|指定した列の JDBC データ型を取得します。|  
|Int getPrecision (int 型の列)|指定した列の精度を取得します。|  
|オブジェクト [getRowData()|オブジェクトの配列として、現在の行のデータを取得します。<br /><br /> 各オブジェクトは、指定した列の JDBC データ型を表すために使用する Java 言語の種類と一致する必要があります。  適切なマッピングの詳細については、「JDBC ドライバーのデータ型について」をご覧ください。|  
|Int getScale (int 型の列)|指定した列の小数点以下桁数を取得します。|  
|ブール isAutoIncrement (int 型の列)|その列が ID 列を表しているかどうかを示します。|  
|ブール next()|次のデータ行に進みます。|  
  
### <a name="sqlserverbulkcsvfilerecord"></a>SQLServerBulkCSVFileRecord  
 データ区切りがあり、各行がデータ行を表すファイルから、基本的な Java データ型を読み込むのに使用できる ISQLServerBulkRecord インターフェイスの単純な実装。  
  
 実装に関する注意事項と制約事項:  
  
1.  1 行分のデータが一度に読み取られるため、各行で許容されるデータ量の上限は、使用可能なメモリによって制限されます。  
  
2.  varchar(max)、varbinary(max)、nvarchar(max)、sqlxml や ntext のような大規模なデータ型のストリーミングはサポートされていません。  
  
3.  CSV ファイル用に指定した区切り記号はデータ内に全く使用しないようにし、それが Java の正規表現で制限のある文字の場合には、正しくエスケープする必要があります。  
  
4.  CSV ファイルの実装では、二重引用符はデータの一部として扱われます。 たとえば、区切り記号にコンマを選択した場合「hello,”world”,”hello,world”」という行は、それぞれ「hello」、「“world”」、「“hello」、および「world”」という値を持つ 4 列として処理されます。  
  
5.  改行文字は行ターミネータとして使用され、データ内には使用できません。  
  
|コンス トラクター|Description|  
|-----------------|-----------------|  
|SQLServerBulkCSVFileRecord (文字列して fileToParse、文字列のエンコーディングは、文字列の区切り記号、ブール firstLineIsColumnNamesSQLServerBulkCSVFileRecord (文字列、文字列、文字列、ブール値)|指定された区切り記号とエンコードを使用して fileToParse 内の各行を解析する SQLServerBulkCSVFileRecord クラスの新しいインスタンスを初期化します。 FirstLineIsColumnNames が True に設定されている場合、ファイルの最初の行は列名として解析されます。  エンコードが NULL の場合、既定のエンコードが使用されます。|  
|SQLServerBulkCSVFileRecord (文字列して fileToParse、文字列、ブール firstLineIsColumnNamesSQLServerBulkCSVFileRecord (文字列、文字列、ブール値) のエンコード|コンマを区切り記号とし、指定されたエンコードを使用して fileToParse 内の各行を解析する SQLServerBulkCSVFileRecord クラスの新しいインスタンスを初期化します。 FirstLineIsColumnNames が True に設定されている場合、ファイルの最初の行は列名として解析されます。  エンコードが NULL の場合、既定のエンコードが使用されます。|  
|SQLServerBulkCSVFileRecord (文字列して fileToParse、ブール firstLineIsColumnNamesSQLServerBulkCSVFileRecord (文字列、ブール値)|コンマを区切り記号とし、既定のエンコードを使用して fileToParse 内の各行を解析する SQLServerBulkCSVFileRecord クラスの新しいインスタンスを初期化します。 FirstLineIsColumnNames が True に設定されている場合、ファイルの最初の行になりますが列名として解析できません。|  
  
|方法|Description|  
|------------|-----------------|  
|AddColumnMetadata (int positionInFile、文字列 columnName、int jdbcType、int 型の有効桁数、int 型の小数点以下桁数) を無効にします。|ファイル内の指定した列にメタデータを追加します。|  
|Close() を無効にします。|ファイル リーダーに関連付けられている任意のリソースを解放します。|  
|Void setTimestampWithTimezoneFormat (DateTim eFormatter dateTimeFormatter|ファイルからのタイムスタンプ データを java.sql.Types.TIMESTAMP_WITH_TIMEZONE として解析するための書式を設定します。|  
|Void setTimestampWithTimezoneFormat(String dateTimeFormat)setTimeWithTimezoneFormat(DateTimeFormatter)|ファイルからのタイム データを java.sql.Types.TIME_WITH_TIMEZONE として解析するための書式を設定します。|  
|Void setTimeWithTimezoneFormat (DateTimeForm atter dateTimeFormatter)|ファイルからのタイム データを java.sql.Types.TIME_WITH_TIMEZONE として解析するための書式を設定します。|  
|Void setTimeWithTimezoneFormat(String timeFormat)|ファイルからのタイム データを java.sql.Types.TIME_WITH_TIMEZONE として解析するための書式を設定します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

