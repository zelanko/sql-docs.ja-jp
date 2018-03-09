---
title: "コレクションの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac05072224f6b6cc4e84b2144d827b6059b226d2
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="using-collections"></a>コレクションの使用
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  コレクションとは、同じオブジェクト クラスから作成された、同じ親オブジェクトを持つオブジェクトのリストのことです。 コレクション オブジェクトには、Collection サフィックス付きのオブジェクトの種類の名前が必ず含まれています。 たとえば、指定されたテーブル内の列にアクセスするには、<xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> というオブジェクトの種類を使用します。 これには、同じ <xref:Microsoft.SqlServer.Management.Smo.Column> オブジェクトに属するすべての <xref:Microsoft.SqlServer.Management.Smo.Table> オブジェクトが含まれます。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **をしています.各**ステートメントまたは[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **foreach**ステートメントは、コレクションの各メンバーを反復処理するために使用できます。  
  
## <a name="examples"></a>使用例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Visual Basic でのコレクションを使用したオブジェクトの参照  
 このコード例を使用して列のプロパティを設定する方法を示しています、 <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>、 <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>、および<xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>プロパティです。 これらのプロパティはコレクションを表現しており、オブジェクトの名前を指定するパラメーターと共に使用すれば、特定のオブジェクトを識別するために使用できます。 名前とスキーマが必要、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>コレクション オブジェクト プロパティです。  
  
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
 このコード例を使用して列のプロパティを設定する方法を示しています、 <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>、 <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>、および<xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>プロパティです。 これらのプロパティはコレクションを表現しており、オブジェクトの名前を指定するパラメーターと共に使用すれば、特定のオブジェクトを識別するために使用できます。 名前とスキーマが必要、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>コレクション オブジェクト プロパティです。  
  
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
 このコード例を反復処理、<xref:Microsoft.AnalysisServices.Server.Databases%2A>コレクション プロパティとすべてのデータベースのインスタンスに接続が表示されます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
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
 このコード例を反復処理、<xref:Microsoft.AnalysisServices.Server.Databases%2A>コレクション プロパティとすべてのデータベースのインスタンスに接続が表示されます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
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
  
  
