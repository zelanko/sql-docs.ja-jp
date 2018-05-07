---
title: SQL Server の OLE DB ドライバーと ADO の併用 |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーと ADO の併用
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: c1244669bcfeea5008640ed00b6f8e579ce71139
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB ドライバーと ADO の併用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  導入された新機能を活用するために[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]など複数のアクティブな結果セット (MARS)、クエリ通知、ユーザー定義型 (Udt)、または新しい**xml** ActiveX を使用する既存のアプリケーションのデータ型Data Objects (ADO) は、データ アクセス プロバイダーとしての SQL Server の OLE DB Driver を使用してください。  
  
 最新バージョンの新機能を使用する ADO を有効にする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、一部の機能強化に加えられた OLE DB Driver for SQL Server OLE DB のコア機能を拡張するものです。 これらの拡張機能を指定する許可を使用する ADO アプリケーションは新しい[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]機能し、2 つのデータで導入された型を使用する[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml**と**udt**です。 これらの拡張機能も強化を利用、 **varchar**、 **nvarchar**、および**varbinary**データ型。 OLE DB Driver for SQL Server は、DBPROPSET_SQLSERVERDBINIT プロパティ セットを使用して ADO アプリケーションで、新しいデータ型が ADO と互換性のある方法で表示されるように、SSPROP_INIT_DATATYPECOMPATIBILITY 初期化プロパティを追加します。 さらに、SQL Server の OLE DB Driver は、という名前の新しい接続文字列キーワードもを定義**DataTypeCompatibility**接続文字列に設定されています。  

> [!NOTE]  
>  既存の ADO アプリケーションは、SQLOLEDB プロバイダーを使用して、XML、UDT、および大きな値のテキストやバイナリのフィールド値にアクセスして更新できます。 新しい大きな**varchar (max)**、 **nvarchar (max)**、および**varbinary (max)** データ型が ADO 型として返されます**adLongVarChar**、**adLongVarWChar**と**adLongVarBinary**それぞれします。 として XML 列が返されます**adLongVarChar**、UDT 列として返されますと**adVarBinary**です。 ただし場合の SQL Server (MSOLEDBSQL) SQLOLEDB ではなく、OLE DB Driver を使用する必要がありますを設定することを確認する、 **DataTypeCompatibility**キーワードを「80」、新しいデータ型が ADO データ型に正しく対応するようにします。  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>ADO から SQL Server の OLE DB ドライバーを有効にします。  
 SQL Server で OLE DB ドライバーの使用方法を有効にするのには ADO アプリケーションは、接続文字列で、次のキーワードを実装する必要があります。  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 詳細については、ADO 接続文字列キーワードが SQL Server の OLE DB ドライバーでサポートされてを参照してください[OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)です。  

 MARS の機能を有効にするなど、SQL Server の OLE DB Driver を使用する完全に有効になっている ADO 接続文字列を確立する例を次に示します。  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  

## <a name="examples"></a>使用例  
 次のセクションでは、SQL Server の OLE DB ドライバーと ADO を使用する方法の例を示します。  

### <a name="retrieving-xml-column-data"></a>XML 列データの取得  
 この例では、レコード セットを取得および XML 列からデータを表示に使用される、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks**サンプル データベース。  

```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  

' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  

con.Close  
Set con = Nothing  
```  

> [!NOTE]  
>  レコードセットのフィルター選択は、XML 列でサポートされません。 これを使用すると、エラーが返されます。  

### <a name="retrieving-udt-column-data"></a>UDT 列データの取得  
 この例では、**コマンド**オブジェクトは、UDT を返す SQL クエリを実行するために使用、UDT データが更新され、新しいデータをデータベースに挿入されます。 この例では、**ポイント**UDT が既にデータベースに登録されています。  

```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  

' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  

' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  

con.Close  
Set con = Nothing  
```  

### <a name="enabling-and-using-mars"></a>MARS の有効化と使用  
 この例では、接続文字列を構築して、SQL Server の OLE DB ドライバーを通じて MARS を有効にして作成して、2 つのレコード セット オブジェクトは、同じ接続を使用して実行します。  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  

Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  

Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  

con.Close  
Set con = Nothing  
```  

 以前のバージョンの OLE DB プロバイダーでは、アクティブな結果セットを 1 つの接続ごとに 1 つしか開くことができなかったので、このコードにより 2 回目の実行時に暗黙の接続が作成されました。 暗黙の接続が OLE DB 接続プールにプールされなかったので、これが原因でオーバーヘッドが増加することになります。 MARS 機能を使用して SQL Server の OLE DB ドライバーによって公開される 1 つの接続で複数のアクティブな結果を取得します。  

## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
