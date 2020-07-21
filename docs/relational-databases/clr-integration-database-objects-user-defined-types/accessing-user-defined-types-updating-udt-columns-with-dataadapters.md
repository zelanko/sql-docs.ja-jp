---
title: Dataadapter | を使用した UDT 列の更新Microsoft Docs
description: SQL Server データベースの Udt は、データを取得して変更するために、system.string と system.string を使用してサポートされます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- ADO.NET [CLR integration]
- updating data [CLR integration]
- populating DataSet
- datasets [CLR integration]
- UDTs [CLR integration], ADO.NET
- updating UDT columns
- user-defined types [CLR integration], ADO.NET
- data adapters [CLR integration]
ms.assetid: 4489c938-ba03-4fdb-b533-cc3f5975ae50
author: rothja
ms.author: jroth
ms.openlocfilehash: 07b1dc9d3f7beca9f048ec0e367c33922e388f32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727831"
---
# <a name="accessing-user-defined-types---updating-udt-columns-with-dataadapters"></a>ユーザー定義型へのアクセス - DataAdapter による UDT 列の更新
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  ユーザー定義型 (Udt)**は、データ**を取得および**変更するために、** system.string と system.string を使用してサポートされています。  
  
## <a name="populating-a-dataset"></a>データセットの設定  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT ステートメントを使用して UDT 列の値を選択すれば、データ アダプターを使用してデータセットにデータを設定できます。 次の例では、次の構造といくつかのサンプルデータを使用して、 **Points**テーブルが定義されていることを前提としています。 次のステートメントでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **Points**テーブルを作成し、いくつかの行を挿入します。  
  
```  
CREATE TABLE dbo.Points (id int PRIMARY Key, p Point);  
  
INSERT INTO dbo.Points VALUES (1, CONVERT(Point, '1,3'));  
INSERT INTO dbo.Points VALUES (2, CONVERT(Point, '2,4'));  
INSERT INTO dbo.Points VALUES (3, CONVERT(Point, '3,5'));  
INSERT INTO dbo.Points VALUES (4, CONVERT(Point, '4,6'));  
GO  
```  
  
 次の ADO.NET コード片では、有効な接続文字列を取得し、新しい**Sqldataadapter**を作成し、 **Points**テーブルのデータ行を使用して system.string を設定**します。**  
  
```vb  
Dim da As New SqlDataAdapter( _  
    "SELECT id, p FROM dbo.Points", connectionString)  
Dim datTable As New DataTable("Points")  
da.Fill(datTable)  
```  
  
```csharp  
SqlDataAdapter da = new SqlDataAdapter(  
   "SELECT id, p FROM dbo.Points", connectionString);  
DataTable datTable = new DataTable("Points");  
da.Fill(datTable);  
```  
  
## <a name="updating-udt-data-in-a-dataset"></a>データセットの UDT データの更新  
 **データセット**内の UDT 列を更新するには、次の2つの方法を使用できます。  
  
-   **Sqldataadapter**オブジェクトのカスタムの**InsertCommand**、 **UpdateCommand** 、および**DeleteCommand**オブジェクトを提供します。  
  
-   INSERT、UPDATE、および DELETE コマンドを自動的に作成するには、コマンドビルダー (**SqlCommandBuilder**) を使用します。 競合検出を行うには、UDT を含むテーブルに**timestamp**列 (別名**rowversion**) を追加し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 **Timestamp**データ型を使用すると、テーブル内の行のバージョンを指定することができ、データベース内で一意であることが保証されます。 テーブル内の値が変更されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではその変更の影響を受ける行の 8 バイトのバイナリ番号が自動的に更新されます。  
  
 **SqlCommandBuilder**では、基になるテーブルに**timestamp**列がない限り、競合検出のために UDT が考慮されないことに注意してください。 UDT は比較できる場合も比較できない場合もあるので、コマンドの生成に "元の値の比較" オプションを使用しているときは、UDT が WHERE 句に含められません。  
  
### <a name="example"></a>例  
 次の例では、 **Point** UDT 列と**timestamp**列を含む2番目のテーブルを作成する必要があります。 両方のテーブルを使用して、カスタムコマンドオブジェクトを作成し、データを更新する方法と、 **timestamp**列を使用して更新する方法を説明します。 2 つ目のテーブルを作成し、そのテーブルにサンプル データを設定するには、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。  
  
```  
CREATE TABLE dbo.Points_ts (id int PRIMARY KEY, p Point, ts timestamp);  
  
INSERT INTO dbo.Points_ts (id, p) VALUES (1, CONVERT(Point, '1,3'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (2, CONVERT(Point, '2,4'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (3, CONVERT(Point, '3,5'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (4, CONVERT(Point, '4,6'));  
```  
  
 次の ADO.NET の例には 2 つのメソッドが含まれています。  
  
-   **UserInsertCommand Dedcommands**。 **Points**テーブル ( **timestamp**列を含まない) の**Point** UDT を更新するために、 **InsertCommand**、 **UpdateCommand**、および**DeleteCommand**オブジェクトを指定する方法を示しています。  
  
-   **CommandBuilder**。 **timestamp**列を含む**Points_ts**テーブルで**SqlCommandBuilder**を使用する方法を示します。  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
    ' Retrieves the connection string  
    Private connString As String = GetConnectionString()  
  
    Sub Main()  
        UserProvidedCommands()  
        CommandBuilder()  
    End Sub  
  
    Private Sub UserProvidedCommands()  
        ' Create a new SqlDataAdapter  
        Dim da As New SqlDataAdapter( _  
          "SELECT id, p FROM dbo.Points", connString)  
  
        ' Setup the INSERT/UPDATE/DELETE commands  
        Dim idParam As SqlParameter  
        Dim pointParam As SqlParameter  
  
        da.InsertCommand = New SqlCommand( _  
          "INSERT INTO dbo.Points (id, p) VALUES (@id, @p)", _  
          da.SelectCommand.Connection)  
        idParam = da.InsertCommand.Parameters.Add( _  
          "@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
        pointParam = da.InsertCommand.Parameters.Add( _  
          "@p", SqlDbType.Udt)  
        pointParam.SourceColumn = "p"  
        pointParam.UdtTypeName = "dbo.Point"  
  
        da.UpdateCommand = New SqlCommand( _  
          "UPDATE dbo.Points SET p = @p WHERE id = @id", _  
          da.SelectCommand.Connection)  
        idParam = _  
           da.UpdateCommand.Parameters.Add("@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
        pointParam = da.UpdateCommand.Parameters.Add( _  
          "@p", SqlDbType.Udt)  
        pointParam.SourceColumn = "p"  
        pointParam.UdtTypeName = "dbo.Point"  
  
        da.DeleteCommand = New SqlCommand( _  
          "DELETE dbo.Points WHERE id = @id", _  
          da.SelectCommand.Connection)  
        idParam = da.DeleteCommand.Parameters.Add( _  
          "@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
  
        ' Fill the DataTable with UDT rows  
        Dim datTable As New DataTable("Points")  
        da.Fill(datTable)  
  
        ' Display the contents of the p (Point) column  
        Dim r As DataRow  
        For Each r In datTable.Rows  
            Dim p As Point = CType(r(1), Point)  
            Console.WriteLine( _  
              "ID: {0}, x={1}, y={1}", r(0), p.X, p.Y)  
        Next r  
  
        ' Update a row if the DataTable has at least 1 row  
        If datTable.Rows.Count > 0 Then  
            Dim oldPoint As Point = _  
              CType(datTable.Rows(0)(1), Point)  
            datTable.Rows(0)(1) = _  
              New Point(oldPoint.X + 1, oldPoint.Y + 1)  
        End If  
  
        ' Delete the last row  
        If datTable.Rows.Count > 0 Then  
            ' If we have at least 1 row  
            datTable.Rows(1).Delete()  
        End If  
  
        ' Insert a row. This will fail if run twice  
        ' because 100 is a primary key value.  
        datTable.Rows.Add(100, New Point(100, 200))  
  
        ' Send the changes back to the database  
        da.Update(datTable)  
    End Sub  
  
    Private Sub CommandBuilder()  
        ' Create a new SqlDataAdapter  
        Dim da As New SqlDataAdapter( _  
          "SELECT id, ts, p FROM dbo.Points_ts", connString)  
  
        ' Select a few rows with UDTs from the database  
        Dim datTable As New DataTable("Points")  
        da.Fill(datTable)  
  
        ' Display the contents of the p (Point) column  
        Dim r As DataRow  
        For Each r In datTable.Rows  
            Dim p As Point = CType(r(2), Point)  
            Console.WriteLine( _  
              "ID: {0}, x={1}, y={1}", r(0), p.X, p.Y)  
        Next r  
  
        ' Update a row if DataTable has at least 1 row  
        If datTable.Rows.Count > 0 Then  
            Dim oldPoint As Point = _  
              CType(datTable.Rows(0)(2), Point)  
            datTable.Rows(0)(2) = _  
              New Point(oldPoint.X + 1, oldPoint.Y + 1)  
        End If  
  
        ' Delete the last row  
        If datTable.Rows.Count > 0 Then  
            ' if we have at least 1 row  
            datTable.Rows(1).Delete()  
        End If  
  
        ' Insert a row. This will fail if run twice  
        ' because 100 is a primary key value  
        datTable.Rows.Add(100, Nothing, New Point(100, 200))  
  
        ' Use the CommandBuilder to generate DML statements  
        Dim bld As New SqlCommandBuilder(da)  
        bld.ConflictDetection = ConflictOptions.CompareRowVersion  
  
        ' Send the changes back to the database  
        da.Update(datTable)  
    End Sub  
  
  Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,   
      ' you can retrieve it from a configuration file.  
     Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
       & "Integrated Security=SSPI"  
   End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
  {  
// Retrieves the connection string  
private string connString = GetConnectionString();  
  
static void Main()  
{  
        UserProvidedCommands();  
        CommandBuilder();  
 }  
    static void UserProvidedCommands()  
    {  
        // Create a new SqlDataAdapter  
        SqlDataAdapter da = new SqlDataAdapter(  
          "SELECT id, p FROM dbo.Points", connString);  
  
        // Setup the INSERT/UPDATE/DELETE commands  
        SqlParameter idParam;  
        SqlParameter pointParam;  
  
        da.InsertCommand = new SqlCommand(  
            "INSERT INTO dbo.Points (id, p) VALUES (@id, @p)",   
             da.SelectCommand.Connection);  
        idParam =   
            da.InsertCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
        pointParam =   
            da.InsertCommand.Parameters.Add("@p", SqlDbType.Udt);  
        pointParam.SourceColumn = "p";  
        pointParam.UdtTypeName = "dbo.Point";  
  
        da.UpdateCommand = new SqlCommand(  
            "UPDATE dbo.Points SET p = @p WHERE id = @id",   
            da.SelectCommand.Connection);  
        idParam =   
            da.UpdateCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
        pointParam =   
            da.UpdateCommand.Parameters.Add("@p", SqlDbType.Udt);  
        pointParam.SourceColumn = "p";  
        pointParam.UdtTypeName = "dbo.Point";   
  
        da.DeleteCommand = new SqlCommand(  
            "DELETE dbo.Points WHERE id = @id",   
            da.SelectCommand.Connection);  
        idParam =   
            da.DeleteCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
  
        // Fill the DataTable with UDT rows  
        DataTable datTable = new DataTable("Points");  
        da.Fill(datTable);  
  
        // Display the contents of the p (Point) column  
        foreach(DataRow r in datTable.Rows)   
        {  
            Point p = (Point)r[1];  
            Console.WriteLine(  
                "ID: {0}, x={1}, y={1}", r[0], p.X, p.Y);  
        }  
  
        // Update a row if the DataTable has at least 1 row  
        if(datTable.Rows.Count > 0 )   
        {   
            Point oldPoint = (Point)datTable.Rows[0][1];  
            datTable.Rows[0][1] =   
                new Point(oldPoint.X+1, oldPoint.Y+1);  
        }  
  
        // Delete the last row  
        if(datTable.Rows.Count > 0 )   
        { // If we have at least 1 row  
            datTable.Rows[1].Delete();  
        }  
  
        // Insert a row. This will fail if run twice  
        // because 100 is a primary key value.  
        datTable.Rows.Add(100, new Point(100, 200));   
  
        // Send the changes back to the database  
        da.Update(datTable);  
    }  
  
    static void CommandBuilder()  
    {  
        // Create a new SqlDataAdapter  
        SqlDataAdapter da = new SqlDataAdapter(  
            "SELECT id, ts, p FROM dbo.Points_ts", connString);  
  
        // Select a few rows with UDTs from the database  
        DataTable datTable = new DataTable("Points");  
        da.Fill(datTable);  
  
        // Display the contents of the p (Point) column  
        foreach (DataRow r in datTable.Rows)  
        {  
            Point p = (Point)r[2];  
            Console.WriteLine(  
                "ID: {0}, x={1}, y={1}", r[0], p.X, p.Y);  
        }  
  
        // Update a row if DataTable has at least 1 row  
        if (datTable.Rows.Count > 0)  
        {   
            Point oldPoint = (Point)datTable.Rows[0][2];  
            datTable.Rows[0][2] =   
                new Point(oldPoint.X + 1, oldPoint.Y + 1);  
        }  
  
        // Delete the last row  
        if (datTable.Rows.Count > 0)  
        { // if we have at least 1 row  
            datTable.Rows[1].Delete();  
        }  
  
        // Insert a row. This will fail if run twice  
        // because 100 is a primary key value  
        datTable.Rows.Add(100, null, new Point(100, 200));   
  
        // Use the CommandBuilder to generate DML statements  
        SqlCommandBuilder bld = new SqlCommandBuilder(da);  
        bld.ConflictDetection = ConflictOptions.CompareRowVersion;  
  
        // Send the changes back to the database  
        da.Update(datTable);  
    }  
  
 static private string GetConnectionString()  
 {  
 // To avoid storing the connection string in your code,   
 // you can retrieve it from a configuration file.  
    return "Data Source=localhost;Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET でのユーザー定義型へのアクセス](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
  
  
