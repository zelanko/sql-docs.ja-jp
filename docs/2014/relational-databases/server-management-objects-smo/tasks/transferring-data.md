---
title: データの転送 |Microsoft Docs
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3fa6ee3b25169e2dafe6ed7ad8380169dfe91d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164742"
---
# <a name="transferring-data"></a>データの転送
  <xref:Microsoft.SqlServer.Management.Smo.Transfer> クラスは、オブジェクトおよびデータを転送するツールを提供するユーティリティ クラスです。  
  
 データベース スキーマ内のオブジェクトは、生成されたスクリプトを対象サーバー上で実行することで転送されます。 <xref:Microsoft.SqlServer.Management.Smo.Table> データは、動的に作成された DTS パッケージによって転送されます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトには、DMO の <xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトのすべての機能、および追加の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能が含まれています。 ただし、SMO での[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]、<xref:Microsoft.SqlServer.Management.Smo.Transfer>オブジェクトで使用、 [SQLBulkCopy](http://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx)データを転送する API。 また、データ転送を実行するために使用されるメソッドおよびプロパティは、<xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトではなく <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトに存在します。 インスタンス クラスからユーティリティ クラスに機能を移動することは、タスクのコードが必要時にのみ読み込まれることを意味するので、軽量化されたオブジェクト モデルに適合する概念です。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのバージョンより前の <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> を持つ対象データベースへのデータ転送はサポートしていません。  
  
## <a name="example"></a>例  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a>Visual Basic でのデータベース間でのスキーマおよびデータの転送  
 このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトを使用してデータベースのスキーマおよびデータを別のデータベースに転送する方法を示します。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a>Visual C# でのデータベース間でのスキーマおよびデータの転送  
 このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトを使用してデータベースのスキーマおよびデータを別のデータベースに転送する方法を示します。  
  
```  
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a>PowerShell でのデータベース間でのスキーマおよびデータの転送  
 このコード例では、<xref:Microsoft.SqlServer.Management.Smo.Transfer> オブジェクトを使用してデータベースのスキーマおよびデータを別のデータベースに転送する方法を示します。  
  
```  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -argumentlist $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -argumentlist $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
  
  
