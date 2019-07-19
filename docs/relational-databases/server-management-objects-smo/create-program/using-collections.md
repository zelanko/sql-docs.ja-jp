---
title: コレクションの使用 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 21b431b121e9ded13352309404014d5a851bbfa0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098175"
---
# <a name="using-collections"></a>コレクションの使用
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  コレクションとは、同じオブジェクト クラスから作成された、同じ親オブジェクトを持つオブジェクトのリストのことです。 コレクション オブジェクトには、Collection サフィックス付きのオブジェクトの種類の名前が必ず含まれています。 たとえば、指定されたテーブル内の列にアクセスするには、<xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> というオブジェクトの種類を使用します。 これには、同じ <xref:Microsoft.SqlServer.Management.Smo.Column> オブジェクトに属するすべての <xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトが含まれます。  
  
 コレクションの各メンバーを反復処理するには、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **For...Each** ステートメントまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **foreach** ステートメントを使用します。  
  
## <a name="examples"></a>使用例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Visual Basic でのコレクションを使用したオブジェクトの参照  
 このコード例では、<xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A> プロパティ、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> プロパティ、および <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> プロパティを使用して、列プロパティを設定する方法を示します。 これらのプロパティはコレクションを表現しており、オブジェクトの名前を指定するパラメーターと共に使用すれば、特定のオブジェクトを識別するために使用できます。 <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> コレクション オブジェクト プロパティには、名前とスキーマが必要です。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Modify a property using the Databases, Tables, and Columns collections to reference a column.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Nullable = True
'Call the Alter method to make the change on the instance of SQL Server.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Alter()
```
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Visual C# でのコレクションを使用したオブジェクトの参照  
 このコード例では、<xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A> プロパティ、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> プロパティ、および <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> プロパティを使用して、列プロパティを設定する方法を示します。 これらのプロパティはコレクションを表現しており、オブジェクトの名前を指定するパラメーターと共に使用すれば、特定のオブジェクトを識別するために使用できます。 <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> コレクション オブジェクト プロパティには、名前とスキーマが必要です。  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a>Visual Basic でのコレクションのメンバーの反復処理  
 このコード例では、<xref:Microsoft.AnalysisServices.Server.Databases%2A> コレクション プロパティを反復処理し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへのすべてのデータベース接続を表示します。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
Dim count As Integer
Dim total As Integer
'Iterate through the databases and call the GetActiveDBConnectionCount method.
Dim db As Database
For Each db In srv.Databases
    count = srv.GetActiveDBConnectionCount(db.Name)
    total = total + count
    'Display the number of connections for each database.
    Console.WriteLine(count & " connections on " & db.Name)
Next
'Display the total number of connections on the instance of SQL Server.
Console.WriteLine("Total connections =" & total)
```
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Visual C# でのコレクションのメンバーの反復処理  
 このコード例では、<xref:Microsoft.AnalysisServices.Server.Databases%2A> コレクション プロパティを反復処理し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへのすべてのデータベース接続を表示します。  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
