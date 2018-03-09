---
title: "作成、変更、およびスキーマの削除 |Microsoft ドキュメント"
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
- schemas [SMO]
ms.assetid: 3e3619de-c6a2-4280-b2be-4ec9924608fb
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dda6526ab21fca7285166dc9c5196eb1d2afa01a
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="creating-altering-and-removing-schemas"></a>スキーマの作成、変更、および削除
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  <xref:Microsoft.SqlServer.Management.Smo.Schema> オブジェクトは、データベース オブジェクトの所有権コンテキストを表現します。 <xref:Microsoft.SqlServer.Management.Smo.Database.Schemas%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティは、<xref:Microsoft.SqlServer.Management.Smo.Schema> オブジェクトのコレクションを表現します。  
  
## <a name="example"></a>例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="creating-altering-and-removing-a-schema-in-visual-basic"></a>Visual Basic でのスキーマの作成、変更、および削除  
 このコード例では、スキーマを作成してデータベース オブジェクトに割り当てる方法を示します。 その後、ユーザーに権限を許可し、スキーマに新しいテーブルを作成します。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a Schema object variable by supplying the parent database and name arguments in the constructor.
Dim sch As Schema
sch = New Schema(db, "MySchema1")
sch.Owner = "dbo"
'Create the schema on the instance of SQL Server.
sch.Create()
'Define an ObjectPermissionSet that contains the Update and Select object permissions.
Dim obperset As ObjectPermissionSet
obperset = New ObjectPermissionSet()
obperset.Add(ObjectPermission.Select)
obperset.Add(ObjectPermission.Update)
'Grant the set of permissions on the schema to the guest account.
sch.Grant(obperset, "guest")
'Define a Table object variable by supplying the parent database, name and schema arguments in the constructor.
Dim tb As Table
tb = New Table(db, "MyTable", "MySchema1")
Dim mycol As Column
mycol = New Column(tb, "Date", DataType.DateTime)
tb.Columns.Add(mycol)
tb.Create()
'Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.
sch.Owner = "guest"
sch.Alter()
'Run the Drop method for the table and the schema to remove them.
tb.Drop()
sch.Drop()
``` 
  
## <a name="creating-altering-and-removing-a-schema-in-visual-c"></a>Visual C# でのスキーマの作成、変更、および削除  
 このコード例では、スキーマを作成してデータベース オブジェクトに割り当てる方法を示します。 その後、ユーザーに権限を許可し、スキーマに新しいテーブルを作成します。  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.   
         Server srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db = srv.Databases["AdventureWorks2012"];   
        //Define a Schema object variable by supplying the parent database and name arguments in the constructor.   
        Schema sch = new Schema(db, "MySchema1");   
        sch.Owner = "dbo";   
  
        //Create the schema on the instance of SQL Server.   
        sch.Create();   
  
        //Define an ObjectPermissionSet that contains the Update and Select object permissions.   
        ObjectPermissionSet obperset = new ObjectPermissionSet();   
        obperset.Add(ObjectPermission.Select);   
        obperset.Add(ObjectPermission.Update);   
  
        //Grant the set of permissions on the schema to the guest account.   
        sch.Grant(obperset, "guest");   
  
        //Define a Table object variable by supplying the parent database, name and schema arguments in the constructor.   
        Table tb = new Table(db, "MyTable", "MySchema1");   
       Column mycol = new Column(tb, "Date", DataType.DateTime);   
        tb.Columns.Add(mycol);   
        tb.Create();   
  
        //Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.   
        sch.Owner = "guest";   
        sch.Alter();   
  
        //Run the Drop method for the table and the schema to remove them.   
        tb.Drop();   
        sch.Drop();   
}  
```  
  
## <a name="creating-altering-and-removing-a-schema-in-powershell"></a>PowerShell でのスキーマの作成、変更、および削除  
 このコード例では、スキーマを作成してデータベース オブジェクトに割り当てる方法を示します。 その後、ユーザーに権限を許可し、スキーマに新しいテーブルを作成します。  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a schema object variable by supplying the parent database and name arguments in the constructor.   
$sch  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Schema `  
-argumentlist $db, "MySchema1"  
  
# Set schema owner  
$sch.Owner = "dbo"   
  
# Create the schema on the instance of SQL Server.   
$sch.Create()  
  
# Define an ObjectPermissionSet that contains the Update and Select object permissions.   
$obperset  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.ObjectPermissionSet  
$obperset.Add([Microsoft.SqlServer.Management.SMO.ObjectPermission]::Select)  
$obperset.Add([Microsoft.SqlServer.Management.SMO.ObjectPermission]::Update)  
  
# Grant the set of permissions on the schema to the guest account.   
$sch.Grant($obperset, "guest")  
  
#Create a SMO Table with one column and add it to the database  
$tb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Table -argumentlist $db, "MyTable", "MySchema1"  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$mycol =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Date", $Type  
$tb.Columns.Add($mycol)  
$tb.Create()   
  
# Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.   
$sch.Owner = "guest"  
$sch.Alter()  
  
# Run the Drop method for the table and the schema to remove them.   
$tb.Drop()  
$sch.Drop()  
```  
  
  
