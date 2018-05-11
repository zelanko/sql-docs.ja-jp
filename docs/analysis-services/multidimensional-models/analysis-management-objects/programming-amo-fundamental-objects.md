---
title: AMO 基本オブジェクトのプログラミング |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f79a3c939d53242a49bd1896b355c8489881242e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="programming-amo-fundamental-objects"></a>AMO 基本オブジェクトのプログラミング
  基本オブジェクトは、一般に、単純で簡単なオブジェクトです。 これらのオブジェクトは、通常、作成およびインスタンス化され、その後、必要がなくなると、ユーザーによって切断されます。 基礎クラスには、<xref:Microsoft.AnalysisServices.Server>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.DataSourceView> などのオブジェクトが含まれます。 AMO 基本オブジェクトの中で唯一の複雑なオブジェクトは、<xref:Microsoft.AnalysisServices.DataSourceView> です。これは、データ ソース ビューを表す抽象モデルを構築するために詳細を必要とします。  
  
 <xref:Microsoft.AnalysisServices.Server> オブジェクトと <xref:Microsoft.AnalysisServices.Database> オブジェクトは、通常、OLAP オブジェクトまたはデータ マイニング オブジェクトとして含まれているオブジェクトを使用する必要があります。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [Server オブジェクト](#ServerObjects)  
  
-   [AMOException 例外オブジェクト](#AMO)  
  
-   [データベース オブジェクト](#DatabaseObjects)  
  
-   [DataSource オブジェクト](#DataSource)  
  
-   [DataSourceView オブジェクト](#DSV)  
  
##  <a name="ServerObjects"></a> Server オブジェクト  
 <xref:Microsoft.AnalysisServices.Server> オブジェクトを使用するには、サーバーに接続し、<xref:Microsoft.AnalysisServices.Server> オブジェクトがサーバーに接続しているかどうかを確認し、接続している場合はそのサーバーから <xref:Microsoft.AnalysisServices.Server> を切断する必要があります。  
  
### <a name="connecting-to-the-server-object"></a>Server オブジェクトへの接続  
 サーバーへの接続は、正しい接続文字列を保持することにより行われます。  
  
 次のコード サンプルで返される、<xref:Microsoft.AnalysisServices.Server>オブジェクトの接続が成功するかを返すかどうか**null**場合は、エラーが発生します。 接続プロセス中のエラーは、try/catch コンストラクトで処理されます。 AMO エラーは、<xref:Microsoft.AnalysisServices.AmoException> 例外クラスを使用してキャッチされます。 この例では、メッセージ ボックスにエラーが表示され、ユーザーに通知されます。  
  
```  
static Server ServerConnect( String strStringConnection)  
{  
    string methodCaption = "ServerConnect method";  
    Server svr = new Server();  
    try  
    {  
        svr.Connect(strStringConnection);  
    }  
    #region ErrorHandling  
    catch (AmoException e)  
    {  
        MessageBox.Show( "AMO exception " + e.ToString());  
        svr = null;  
    }  
    catch (Exception e)  
    {  
        MessageBox.Show("General exception " + e.ToString());  
        svr = null;  
    }  
    #endregion  
  
    return svr;  
}  
```  
  
 接続文字列の構造は、次のとおりです。  
  
 "**データ ソース =**\<サーバー名 >"です。  
  
 接続文字列の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Management.Common.OlapConnectionInfo.ConnectionString%2A>です。  
  
### <a name="validating-the-connection"></a>接続の検証  
 <xref:Microsoft.AnalysisServices.Server> オブジェクトをプログラミングする前に、サーバーに接続されていることを検証する必要があります。 次のコード サンプルは、この方法を示します。 このサンプルでは、`svr` がコード内に存在する <xref:Microsoft.AnalysisServices.Server> オブジェクトであることを前提としています。  
  
```  
if ( (svr != null) && ( svr.Connected))  
{  
    // Do what it is needed if connection is good  
}  
```  
  
### <a name="disconnecting-from-the-server"></a>サーバーからの切断  
 完了直後に、Disconnect メソッドを使用して、サーバーから切断できます。 次のコード サンプルは、この方法を示します。 このサンプルでは、`svr` がコード内に存在する <xref:Microsoft.AnalysisServices.Server> オブジェクトであることを前提としています。  
  
```  
if ( (svr != null) && ( svr.Connected))  
{  
    svr.Disconnect()  
}  
```  
  
###  <a name="AMO"></a> AmoException 例外オブジェクト  
 AMO は、さまざまな問題が検出されるたびに例外をスローします。 例外の詳細については、次を参照してください。 [AMO のその他のクラスとメソッド](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)です。 次のサンプル コードは、AMO 内の例外をキャプチャするための正しい方法を示します。  
  
```  
try  
{  
   //... some AMO code in here  
}  
  
catch (  OutOfSynchException e)  
{  
   // error handling code for OutOfSynchException   
}  
  
catch (  OperationException e)  
{  
   // error handling code for OperationException   
}   
  
catch (  ResponseFormatException e)  
  
{  
   // error handling code for ResponseFormatException   
}   
  
catch (  ConnectionException e)  
  
{  
   // error handling code for ConnectionException   
}  
  
catch (  AMOException e)  
  
{  
   //... here is the place where you end if it is an AMO exception, but none of the previous exceptions  
   // if you start with AMOException in the first catch you will never see any one of the previous exceptions  
}  
```  
  
##  <a name="DatabaseObjects"></a> データベース オブジェクト  
 <xref:Microsoft.AnalysisServices.Database> オブジェクトを使用した作業は、非常に単純です。 <xref:Microsoft.AnalysisServices.Server> オブジェクトのデータベース コレクションから既存のデータベースを取得します。  
  
### <a name="creating-dropping-and-finding-a-database"></a>データベースの作成、削除、および検索  
 次のコード サンプルは、データベース名を使用したデータベースの作成方法を示します。 データベースを作成する前に、サーバーの <xref:Microsoft.AnalysisServices.DatabaseCollection> をクエリして、データベースが存在するかどうかを確認します。 データベースが存在する場合は、そのデータベースを削除してから、再作成します。データベースが存在しない場合は、データベースを作成します。 データベースを削除する場合、そのデータベースは、最初にデータベース コレクションから取得されます。  
  
```  
static Database CreateDatabase(Server svr, String DatabaseName)  
{  
    Database db = null;  
    if ( (svr != null) && ( svr.Connected))  
    {  
        // Drop the database if it already exists  
        db = svr.Databases.FindByName(DatabaseName);  
        if (db != null)  
        {  
            db.Drop();  
        }  
  
        // Create the database  
        db = svr.Databases.Add(DatabaseName);  
        db.Update();  
    }  
  
    return db;  
}  
```  
  
 データベースがデータベース コレクションに存在するかどうかを確認するには、FindByName メソッドを使用します。 データベースが存在する場合、FindByName メソッドは検出されたデータベース オブジェクトを返します。データベースが存在しない場合は、NULL オブジェクトを返します。  
  
 <xref:Microsoft.AnalysisServices.Database> オブジェクトをデータベース コレクションに追加したら、Update メソッドを使用してサーバーを更新する必要があります。 サーバーの更新に失敗すると、<xref:Microsoft.AnalysisServices.Database> オブジェクトは、そのサーバーで作成されなくなります。  
  
### <a name="processing-a-database"></a>データベースの処理  
 <xref:Microsoft.AnalysisServices.Database> オブジェクトには Process メソッドが含まれるため、すべての子オブジェクトを使用したデータベースの処理は非常に単純です。  
  
 Process メソッドにはパラメーターを含めることができますが、パラメーターは必要ありません。 パラメーターが指定されていないかどうかは、すべての子オブジェクトをで処理する、 **ProcessDefault**オプション。 処理オプションの詳細については、次を参照してください。<xref:Microsoft.AnalysisServices.Database>です。  
  
1.  次のサンプル コードは、既定値を使用してデータベースを処理します。  
  
```  
static Database ProcessDatabase(Database db, ProcessType pt)  
{  
    db.Process( pt);  
    return db;  
}  
```  
  
##  <a name="DataSource"></a> DataSource オブジェクト  
 <xref:Microsoft.AnalysisServices.DataSource> オブジェクトとは、データが存在するデータベースと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] との間のリンクです。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の基になるモデルを表すスキーマは、<xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトによって定義されます。 <xref:Microsoft.AnalysisServices.DataSource> オブジェクトは、データが存在するデータベースに対する接続文字列と見なすことができます。  
  
 次のサンプル コードは、<xref:Microsoft.AnalysisServices.DataSource> オブジェクトの作成方法を示します。 このサンプルでは、サーバーが依然として存在していること、<xref:Microsoft.AnalysisServices.Server> オブジェクトが接続されていること、およびデータベースが存在していることを確認します。 <xref:Microsoft.AnalysisServices.DataSource> オブジェクトが存在する場合、そのオブジェクトを削除して再作成します。 同じ名前と内部 ID を持つ <xref:Microsoft.AnalysisServices.DataSource> オブジェクトを作成します。 このサンプルでは、検証のために接続文字列に対して確認を実行しません。  
  
```  
static string CreateDataSource(Database db, string strDataSourceName, string strConnectionString)  
{  
        Server svr = db.Parent;  
        DataSource ds = db.DataSources.FindByName(strDataSourceName);  
        if (ds != null)  
            ds.Drop();  
        // Create the data source  
        ds = db.DataSources.Add(strDataSourceName, strDataSourceName);  
        ds.ConnectionString = strConnectionString;  
  
        // Send the data source definition to the server.  
        ds.Update();  
  
        return ds.Name;  
}  
```  
  
##  <a name="DSV"></a> DataSourceView オブジェクト  
 <xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のスキーマ モデルを保持する役割を担います。 <xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトがスキーマを保持するには、まず、スキーマを作成する必要があります。 スキーマは、DataSet オブジェクトを経由して、System.Data 名前空間から作成されます。  
  
 次のサンプル コードは、AdventureWorks に基づく Analysis Services サンプル プロジェクトに含まれるスキーマの一部を作成します。 この現サンプルは、テーブル、計算列、リレーション、および複合リレーションに対するスキーマ定義を作成します。 スキーマは、保存されるデータセットです。  
  
 サンプル コードは、次の処理を実行します。  
  
1.  <xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトを作成します。  
  
     場合、まずことを確認、<xref:Microsoft.AnalysisServices.DataSource>オブジェクトが存在する場合は**true**、ドロップ、<xref:Microsoft.AnalysisServices.DataSource>し、作成します。 <xref:Microsoft.AnalysisServices.DataSource> が存在しない場合は、これを作成します。  
  
2.  <xref:Microsoft.AnalysisServices.DataSource> 接続文字列を使用して、データベースへの接続を開きます。  
  
3.  スキーマを作成します。  
  
     スキーマは次の要素で構成されます。  
  
    -   テーブル定義 (`AddTable()` メソッド)  
  
    -   省略可能な計算列のセット (`AddComputedColumn()` メソッド)  
  
    -   省略可能なリレーションのセット (`AddRelation`)  
  
    -   省略可能な複合リレーションのセット (`AddCompositeRelations`)  
  
4.  サーバーを更新します。  
  
> [!NOTE]  
>  次のサンプル コードは、読みやすくするために一部省略されています。完全なコードは、このトピックの最後で確認できます。  
  
> [!NOTE]  
>  `AddTable` メソッド、`AddComputedColumn` メソッド、`AddRelation` メソッド、および `AddCompositeRelation` メソッドは、サンプル コードの一部です。  
  
> [!NOTE]  
>  句`'WHERE 1=0'`に行を返さないクエリを回避するのには、**データセット**オブジェクト。  
  
```  
        static DataSourceView CreateDataSourceView(Database db, string strDataSourceName)  
        {  
            // Create the data source view  
            DataSourceView dsv = db.DataSourceViews.FindByName(strDataSourceName);  
            if ( dsv != null)  
               dsv.Drop();  
            dsv = db.DataSourceViews.Add(strDataSourceName);  
            dsv.DataSourceID = strDataSourceName;  
            dsv.Schema = new DataSet();  
            dsv.Schema.Locale = CultureInfo.CurrentCulture;  
  
            // Open a connection to the data source  
            OleDbConnection connection  
                = new OleDbConnection(dsv.DataSource.ConnectionString);  
            connection.Open();  
  
            #region Create tables  
  
            // Add the DimTime table  
            AddTable(dsv, connection, "DimTime");  
            AddComputedColumn(dsv, connection, "DimTime", "SimpleDate", "DATENAME(mm, FullDateAlternateKey) + ' ' + DATENAME(dd, FullDateAlternateKey) + ',' + ' ' + DATENAME(yy, FullDateAlternateKey)");  
  
            // Add the DimProductCategory table  
            AddTable(dsv, connection, "DimProductCategory");  
  
            // Add the DimProductSubcategory table  
            AddTable(dsv, connection, "DimProductSubcategory");  
            AddRelation(dsv, "DimProductSubcategory", "ProductCategoryKey", "DimProductCategory", "ProductCategoryKey");  
  
            // Add the FactInternetSales table  
            AddTable(dsv, connection, "FactInternetSales");  
"DimTime", "TimeKey");  
            AddRelation(dsv, "FactInternetSales", "ShipDateKey", "DimTime", "TimeKey");  
            AddRelation(dsv, "FactInternetSales", "DueDateKey", "DimTime", "TimeKey");  
  
            // Add the FactInternetSalesReason table  
            AddTable(dsv, connection, "FactInternetSalesReason");  
            AddCompositeRelation(dsv, "FactInternetSalesReason", "FactInternetSales", "SalesOrderNumber", "SalesOrderLineNumber");  
            dsv.Update();  
  
            #endregion  
  
            // Send the data source view definition to the server  
            dsv.Update();  
  
            return dsv;  
        }  
  
        static void AddTable(DataSourceView dsv, OleDbConnection connection, String tableName)  
        {  
            string strSelectText = "SELECT * FROM [dbo].[" + tableName + "] WHERE 1=0";  
            OleDbDataAdapter adapter = new OleDbDataAdapter(strSelectText, connection);  
            DataTable[] dataTables = adapter.FillSchema(dsv.Schema,  
                SchemaType.Mapped, tableName);  
            DataTable dataTable = dataTables[0];  
  
            dataTable.ExtendedProperties.Add("TableType", "Table");  
            dataTable.ExtendedProperties.Add("DbSchemaName", "dbo");  
            dataTable.ExtendedProperties.Add("DbTableName", tableName);  
            dataTable.ExtendedProperties.Add("FriendlyName", tableName);  
  
            dataTable = null;  
            dataTables = null;  
            adapter = null;  
        }  
  
        static void AddComputedColumn(DataSourceView dsv, OleDbConnection connection, String tableName, String computedColumnName, String expression)  
        {  
            DataSet tmpDataSet = new DataSet();  
            tmpDataSet.Locale = CultureInfo.CurrentCulture;  
            OleDbDataAdapter adapter = new OleDbDataAdapter("SELECT ("  
                + expression + ") AS [" + computedColumnName + "] FROM [dbo].["  
                + tableName + "] WHERE 1=0", connection);  
            DataTable[] dataTables = adapter.FillSchema(tmpDataSet,  
                SchemaType.Mapped, tableName);  
            DataTable dataTable = dataTables[0];  
            DataColumn dataColumn = dataTable.Columns[computedColumnName];  
  
            dataTable.Constraints.Clear();  
            dataTable.Columns.Remove(dataColumn);  
  
            dataColumn.ExtendedProperties.Add("DbColumnName", computedColumnName);  
            dataColumn.ExtendedProperties.Add("ComputedColumnExpression",  
                expression);  
            dataColumn.ExtendedProperties.Add("IsLogical", "True");  
  
            dsv.Schema.Tables[tableName].Columns.Add(dataColumn);  
  
            dataColumn = null;  
            dataTable = null;  
            dataTables = null;  
            adapter = null;  
            tmpDataSet = null;  
        }  
  
        static void AddRelation(DataSourceView dsv, String fkTableName, String fkColumnName, String pkTableName, String pkColumnName)  
        {  
            DataColumn fkColumn  
                = dsv.Schema.Tables[fkTableName].Columns[fkColumnName];  
            DataColumn pkColumn  
                = dsv.Schema.Tables[pkTableName].Columns[pkColumnName];  
            dsv.Schema.Relations.Add("FK_" + fkTableName + "_"  
                + fkColumnName, pkColumn, fkColumn, true);  
        }  
  
        static void AddCompositeRelation(DataSourceView dsv, String fkTableName, String pkTableName, String columnName1, String columnName2)  
        {  
            DataColumn[] fkColumns = new DataColumn[2];  
            fkColumns[0] = dsv.Schema.Tables[fkTableName].Columns[columnName1];  
            fkColumns[1] = dsv.Schema.Tables[fkTableName].Columns[columnName2];  
  
            DataColumn[] pkColumns = new DataColumn[2];  
            pkColumns[0] = dsv.Schema.Tables[pkTableName].Columns[columnName1];  
            pkColumns[1] = dsv.Schema.Tables[pkTableName].Columns[columnName2];  
  
            dsv.Schema.Relations.Add("FK_" + fkTableName + "_" + columnName1  
                + "_" + columnName2, pkColumns, fkColumns, true);  
        }  
  
```  
  
 サンプル コードで、`AddTable`と`AddComputedColumn`メソッドを使用して、`FillSchema`のメソッド、 **DataAdapter**を追加するオブジェクト、 **DataTable**を**データセット**し、データ ソースに一致するスキーマを構成します。 拡張プロパティは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のスキーマを構成するために必要な情報を追加します。  
  
 サンプル コードでは、`AddRelation` メソッドと `AddCompositeRelation` メソッドは、モデルにおける既存のスキーマと既存の列に応じて、リレーション列を追加します。 これらのメソッドを機能させるには、列が、スキーマで定義されたテーブルの一部である必要があります。  
  
 完全なコード サンプルを以下に示します。  
  
```  
static DataSourceView CreateDataSourceView(Database db, string strDataSourceName)  
{  
    // Create the data source view  
    DataSourceView dsv = db.DataSourceViews.FindByName(strDataSourceName);  
    if ( dsv != null)  
       dsv.Drop();  
    dsv = db.DataSourceViews.Add(strDataSourceName);  
    dsv.DataSourceID = strDataSourceName;  
    dsv.Schema = new DataSet();  
    dsv.Schema.Locale = CultureInfo.CurrentCulture;  
  
    // Open a connection to the data source  
    OleDbConnection connection  
        = new OleDbConnection(dsv.DataSource.ConnectionString);  
    connection.Open();  
  
    #region Create tables  
  
    // Add the DimTime table  
    AddTable(dsv, connection, "DimTime");  
    AddComputedColumn(dsv, connection, "DimTime", "SimpleDate", "DATENAME(mm, FullDateAlternateKey) + ' ' + DATENAME(dd, FullDateAlternateKey) + ',' + ' ' + DATENAME(yy, FullDateAlternateKey)");  
    AddComputedColumn(dsv, connection, "DimTime", "CalendarYearDesc", "'CY' + ' ' + CalendarYear");  
    AddComputedColumn(dsv, connection, "DimTime", "CalendarSemesterDesc", "CASE WHEN CalendarSemester = 1 THEN 'H1'+' '+ 'CY' +' '+ CONVERT(CHAR (4), CalendarYear) ELSE 'H2'+' '+ 'CY' +' '+ CONVERT(CHAR (4), CalendarYear) END");  
    AddComputedColumn(dsv, connection, "DimTime", "CalendarQuarterDesc", "'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY' +' '+ CONVERT(CHAR (4), CalendarYear)");  
    AddComputedColumn(dsv, connection, "DimTime", "MonthName", "EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalYearDesc", "'FY' + ' ' + FiscalYear");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalSemesterDesc", "CASE WHEN FiscalSemester = 1 THEN 'H1'+' '+ 'FY' +' '+ CONVERT(CHAR (4), FiscalYear) ELSE 'H2'+' '+ 'FY' +' '+ CONVERT(CHAR (4), FiscalYear) END");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalQuarterDesc", "'Q' + CONVERT(CHAR (1), FiscalQuarter) +' '+ 'FY' +' '+ CONVERT(CHAR (4), FiscalYear)");  
    AddComputedColumn(dsv, connection, "DimTime", "FiscalMonthNumberOfYear", "CASE WHEN MonthNumberOfYear = '1'  THEN CONVERT(int,'7') WHEN MonthNumberOfYear = '2'  THEN CONVERT(int,'8') WHEN MonthNumberOfYear = '3'  THEN CONVERT(int,'9') WHEN MonthNumberOfYear = '4'  THEN CONVERT(int,'10') WHEN MonthNumberOfYear = '5'  THEN CONVERT(int,'11') WHEN MonthNumberOfYear = '6'  THEN CONVERT(int,'12') WHEN MonthNumberOfYear = '7'  THEN CONVERT(int,'1') WHEN MonthNumberOfYear = '8'  THEN CONVERT(int,'2') WHEN MonthNumberOfYear = '9'  THEN CONVERT(int,'3') WHEN MonthNumberOfYear = '10' THEN CONVERT(int,'4') WHEN MonthNumberOfYear = '11' THEN CONVERT(int,'5') WHEN MonthNumberOfYear = '12' THEN CONVERT(int,'6') END");  
    dsv.Update();  
  
    // Add the DimGeography table  
    AddTable(dsv, connection, "DimGeography");  
  
    // Add the DimProductCategory table  
    AddTable(dsv, connection, "DimProductCategory");  
  
    // Add the DimProductSubcategory table  
    AddTable(dsv, connection, "DimProductSubcategory");  
    AddRelation(dsv, "DimProductSubcategory", "ProductCategoryKey", "DimProductCategory", "ProductCategoryKey");  
  
    // Add the DimProduct table  
    AddTable(dsv, connection, "DimProduct");  
    AddComputedColumn(dsv, connection, "DimProduct", "ProductLineName", "CASE ProductLine WHEN 'M' THEN 'Mountain' WHEN 'R' THEN 'Road' WHEN 'S' THEN 'Accessory' WHEN 'T' THEN 'Touring' ELSE 'Components' END");  
    AddRelation(dsv, "DimProduct", "ProductSubcategoryKey", "DimProductSubcategory", "ProductSubcategoryKey");  
    dsv.Update();  
  
    // Add the DimCustomer table  
    AddTable(dsv, connection, "DimCustomer");  
    AddComputedColumn(dsv, connection, "DimCustomer", "FullName", "CASE WHEN MiddleName IS NULL THEN FirstName + ' ' + LastName ELSE FirstName + ' ' + MiddleName + ' ' + LastName END");  
    AddComputedColumn(dsv, connection, "DimCustomer", "GenderDesc", "CASE WHEN Gender = 'M' THEN 'Male' ELSE 'Female' END");  
    AddComputedColumn(dsv, connection, "DimCustomer", "MaritalStatusDesc", "CASE WHEN MaritalStatus = 'S' THEN 'Single' ELSE 'Married' END");  
    AddRelation(dsv, "DimCustomer", "GeographyKey", "DimGeography", "GeographyKey");  
  
    // Add the DimReseller table  
    AddTable(dsv, connection, "DimReseller");  
    AddComputedColumn(dsv, connection, "DimReseller", "OrderFrequencyDesc", "CASE WHEN OrderFrequency = 'A' THEN 'Annual' WHEN OrderFrequency = 'S' THEN 'Bi-Annual' ELSE 'Quarterly' END");  
    AddComputedColumn(dsv, connection, "DimReseller", "OrderMonthDesc", "CASE WHEN OrderMonth = '1' THEN 'January' WHEN OrderMonth = '2' THEN 'February' WHEN OrderMonth = '3' THEN 'March' WHEN OrderMonth = '4' THEN 'April' WHEN OrderMonth = '5' THEN 'May' WHEN OrderMonth = '6' THEN 'June' WHEN OrderMonth = '7' THEN 'July' WHEN OrderMonth = '8' THEN 'August' WHEN OrderMonth = '9' THEN 'September' WHEN OrderMonth = '10' THEN 'October' WHEN OrderMonth = '11' THEN 'November' WHEN OrderMonth = '12' THEN 'December' ELSE 'Never Ordered' END");  
  
    // Add the DimCurrency table  
    AddTable(dsv, connection, "DimCurrency");  
    dsv.Update();  
  
    // Add the DimSalesReason table  
    AddTable(dsv, connection, "DimSalesReason");  
  
    // Add the FactInternetSales table  
    AddTable(dsv, connection, "FactInternetSales");  
    AddRelation(dsv, "FactInternetSales", "ProductKey", "DimProduct", "ProductKey");  
    AddRelation(dsv, "FactInternetSales", "CustomerKey", "DimCustomer", "CustomerKey");  
    AddRelation(dsv, "FactInternetSales", "OrderDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactInternetSales", "ShipDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactInternetSales", "DueDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactInternetSales", "CurrencyKey", "DimCurrency", "CurrencyKey");  
    dsv.Update();  
  
    // Add the FactResellerSales table  
    AddTable(dsv, connection, "FactResellerSales");  
    AddRelation(dsv, "FactResellerSales", "ProductKey", "DimProduct", "ProductKey");  
    AddRelation(dsv, "FactResellerSales", "ResellerKey", "DimReseller", "ResellerKey");  
    AddRelation(dsv, "FactResellerSales", "OrderDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactResellerSales", "ShipDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactResellerSales", "DueDateKey", "DimTime", "TimeKey");  
    AddRelation(dsv, "FactResellerSales", "CurrencyKey", "DimCurrency", "CurrencyKey");  
  
    // Add the FactInternetSalesReason table  
    AddTable(dsv, connection, "FactInternetSalesReason");  
    AddCompositeRelation(dsv, "FactInternetSalesReason", "FactInternetSales", "SalesOrderNumber", "SalesOrderLineNumber");  
    dsv.Update();  
  
    // Add the FactCurrencyRate table  
    AddTable(dsv, connection, "FactCurrencyRate");  
    AddRelation(dsv, "FactCurrencyRate", "CurrencyKey", "DimCurrency", "CurrencyKey");  
    AddRelation(dsv, "FactCurrencyRate", "TimeKey", "DimTime", "TimeKey");  
  
    #endregion  
  
    // Send the data source view definition to the server  
    dsv.Update();  
  
    return dsv;  
}  
  
static void AddTable(DataSourceView dsv, OleDbConnection connection, String tableName)  
{  
    string strSelectText = "SELECT * FROM [dbo].[" + tableName + "] WHERE 1=0";  
    OleDbDataAdapter adapter = new OleDbDataAdapter(strSelectText, connection);  
    DataTable[] dataTables = adapter.FillSchema(dsv.Schema,  
        SchemaType.Mapped, tableName);  
    DataTable dataTable = dataTables[0];  
  
    dataTable.ExtendedProperties.Add("TableType", "Table");  
    dataTable.ExtendedProperties.Add("DbSchemaName", "dbo");  
    dataTable.ExtendedProperties.Add("DbTableName", tableName);  
    dataTable.ExtendedProperties.Add("FriendlyName", tableName);  
  
    dataTable = null;  
    dataTables = null;  
    adapter = null;  
}  
  
static void AddComputedColumn(DataSourceView dsv, OleDbConnection connection, String tableName, String computedColumnName, String expression)  
{  
    DataSet tmpDataSet = new DataSet();  
    tmpDataSet.Locale = CultureInfo.CurrentCulture;  
    OleDbDataAdapter adapter = new OleDbDataAdapter("SELECT ("  
        + expression + ") AS [" + computedColumnName + "] FROM [dbo].["  
        + tableName + "] WHERE 1=0", connection);  
    DataTable[] dataTables = adapter.FillSchema(tmpDataSet,  
        SchemaType.Mapped, tableName);  
    DataTable dataTable = dataTables[0];  
    DataColumn dataColumn = dataTable.Columns[computedColumnName];  
  
    dataTable.Constraints.Clear();  
    dataTable.Columns.Remove(dataColumn);  
  
    dataColumn.ExtendedProperties.Add("DbColumnName", computedColumnName);  
    dataColumn.ExtendedProperties.Add("ComputedColumnExpression",  
        expression);  
    dataColumn.ExtendedProperties.Add("IsLogical", "True");  
  
    dsv.Schema.Tables[tableName].Columns.Add(dataColumn);  
  
    dataColumn = null;  
    dataTable = null;  
    dataTables = null;  
    adapter = null;  
    tmpDataSet = null;  
}  
  
static void AddRelation(DataSourceView dsv, String fkTableName, String fkColumnName, String pkTableName, String pkColumnName)  
{  
    DataColumn fkColumn  
        = dsv.Schema.Tables[fkTableName].Columns[fkColumnName];  
    DataColumn pkColumn  
        = dsv.Schema.Tables[pkTableName].Columns[pkColumnName];  
    dsv.Schema.Relations.Add("FK_" + fkTableName + "_"  
        + fkColumnName, pkColumn, fkColumn, true);  
}  
  
static void AddCompositeRelation(DataSourceView dsv, String fkTableName, String pkTableName, String columnName1, String columnName2)  
{  
    DataColumn[] fkColumns = new DataColumn[2];  
    fkColumns[0] = dsv.Schema.Tables[fkTableName].Columns[columnName1];  
    fkColumns[1] = dsv.Schema.Tables[fkTableName].Columns[columnName2];  
  
    DataColumn[] pkColumns = new DataColumn[2];  
    pkColumns[0] = dsv.Schema.Tables[pkTableName].Columns[columnName1];  
    pkColumns[1] = dsv.Schema.Tables[pkTableName].Columns[columnName2];  
  
    dsv.Schema.Relations.Add("FK_" + fkTableName + "_" + columnName1  
        + "_" + columnName2, pkColumns, fkColumns, true);  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO 基礎クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
