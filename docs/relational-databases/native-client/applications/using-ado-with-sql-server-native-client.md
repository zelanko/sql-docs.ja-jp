---
title: "SQL Server Native Client と ADO の併用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 13978b8eb01fda4b9478111a3bef3e36c76f8e58
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="using-ado-with-sql-server-native-client"></a>SQL Server Native Client と ADO の併用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  導入された新機能を活用するために[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]など複数のアクティブな結果セット (MARS)、クエリ通知、ユーザー定義型 (Udt)、または新しい**xml** ActiveX を使用する既存のアプリケーションのデータ型Data Objects (ADO) を使用する必要があります、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーをデータ アクセス プロバイダーとして。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の新機能を一切使用する必要がない場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用する必要はありません。つまり、現在のデータ アクセス プロバイダー (通常は SQLOLEDB) を継続して使用できます。 既存のアプリケーションを強化して、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の新機能を使用する必要がある場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用してください。  
  
> [!NOTE]  
>  新しいアプリケーションを開発している場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の最新バージョンのすべての新機能にアクセスできるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ではなく、ADO.NET および .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の使用を検討することをお勧めします。 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の詳細については、ADO.NET に関する .NET Framework SDK のドキュメントを参照してください。  
  
 ADO から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の最新バージョンの新機能を使用できるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを機能強化し、OLE DB の中核となる機能を拡張しました。 これらの拡張機能を指定する許可を使用する ADO アプリケーションは新しい[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]機能し、2 つのデータで導入された型を使用する[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml**と**udt**です。 これらの拡張機能も強化を利用、 **varchar**、 **nvarchar**、および**varbinary**データ型。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、DBPROPSET_SQLSERVERDBINIT プロパティ セットを使用して ADO アプリケーションで、新しいデータ型が ADO と互換性のある方法で表示されるように、SSPROP_INIT_DATATYPECOMPATIBILITY 初期化プロパティを追加します。 さらに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーはという名前の新しい接続文字列キーワードも定義**DataTypeCompatibility**接続文字列に設定されています。  
  
> [!NOTE]  
>  既存の ADO アプリケーションは、SQLOLEDB プロバイダーを使用して、XML、UDT、および大きな値のテキストやバイナリのフィールド値にアクセスして更新できます。 新しい大きな**varchar (max)**、 **nvarchar (max)**、および**varbinary (max)**データ型が ADO 型として返されます**adLongVarChar**、**adLongVarWChar**と**adLongVarBinary**それぞれします。 として XML 列が返されます**adLongVarChar**、UDT 列として返されますと**adVarBinary**です。 ただし、使用する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQLOLEDB ではなく Native Client OLE DB プロバイダー (SQLNCLI11) を設定することを確認する必要があります、 **DataTypeCompatibility**キーワードを「80」、新しいデータ型が ADO データに正しく対応するように型。  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>ADO からの SQL Server Native Client の有効化  
 使用方法を有効にする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、ADO アプリケーションは、接続文字列で、次のキーワードを実装する必要があります。  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 詳細については、ADO 接続文字列でサポートされるキーワード[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client を参照してください[使用した Connection String Keywords with SQL Server Native Client を使用して](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)です。  
  
 次の例に示しますを使用する完全に有効になっている ADO 接続文字列を確立する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]MARS 機能の有効化を含む、ネイティブのクライアント。  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a>使用例  
 次のセクションでは、ADO との使用方法の例を提供する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。  
  
### <a name="retrieving-xml-column-data"></a>XML 列データの取得  
 この例では、レコード セットを取得および XML 列からデータを表示に使用される、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks**サンプル データベース。  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
 この例では、接続文字列はで MARS を有効にする、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーとし、2 つのレコード セット オブジェクトが作成されている場合、同じ接続を使用して実行します。  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
 以前のバージョンの OLE DB プロバイダーでは、アクティブな結果セットを 1 つの接続ごとに 1 つしか開くことができなかったので、このコードにより 2 回目の実行時に暗黙の接続が作成されました。 暗黙の接続が OLE DB 接続プールにプールされなかったので、これが原因でオーバーヘッドが増加することになります。 によって公開される、MARS 機能と、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、1 つの接続で複数のアクティブな結果を取得します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client でアプリケーションの構築](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
