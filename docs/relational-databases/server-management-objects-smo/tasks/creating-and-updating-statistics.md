---
title: "作成して、統計の更新 |Microsoft ドキュメント"
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
- statistical information [SMO]
ms.assetid: 47a0a172-a969-4deb-bca9-dd04401a0fe1
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c1a24487cf7460024fd26e1f4101c791d29589d
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="creating-and-updating-statistics"></a>統計の作成と更新
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]SMO を使用して、データベース内のクエリの処理に関する統計情報を収集できます、<xref:Microsoft.SqlServer.Management.Smo.Statistic>オブジェクト。  
  
 任意の列に対する統計の作成は、<xref:Microsoft.SqlServer.Management.Smo.Statistic> および <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> オブジェクトを使用して行うことができます。 <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> メソッドを実行して、<xref:Microsoft.SqlServer.Management.Smo.Statistic> オブジェクト内の統計を更新することができます。 結果は、クエリ オプティマイザーで表示できます。  
  
## <a name="example"></a>例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="creating-and-update-statistics-in-visual-basic"></a>Visual Basic での統計の作成および更新  
 このコード例では、既存のデータベースに新しいテーブルを作成し、<xref:Microsoft.SqlServer.Management.Smo.Statistic> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> オブジェクトを作成しています。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Reference the CreditCard table.
Dim tb As Table
tb = db.Tables("CreditCard", "Sales")
'Define a Statistic object by supplying the parent table and name arguments in the constructor.
Dim stat As Statistic
stat = New Statistic(tb, "Test_Statistics")
'Define a StatisticColumn object variable for the CardType column and add to the Statistic object variable.
Dim statcol As StatisticColumn
statcol = New StatisticColumn(stat, "CardType")
stat.StatisticColumns.Add(statcol)
'Create the statistic counter on the instance of SQL Server.
stat.Create()
``` 
  
## <a name="creating-and-update-statistics-in-visual-c"></a>Visual C# での統計の作成および更新  
 このコード例では、既存のデータベースに新しいテーブルを作成し、<xref:Microsoft.SqlServer.Management.Smo.Statistic> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> オブジェクトを作成しています。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Reference the CreditCard table.   
  
           Table tb = db.Tables["CreditCard", "Sales"];  
            //Define a Statistic object by supplying the parent table and name   
            //arguments in the constructor.   
            Statistic stat = default(Statistic);  
            stat = new Statistic(tb, "Test_Statistics");  
            //Define a StatisticColumn object variable for the CardType column   
            //and add to the Statistic object variable.   
            StatisticColumn statcol = default(StatisticColumn);  
            statcol = new StatisticColumn(stat, "CardType");  
            stat.StatisticColumns.Add(statcol);  
            //Create the statistic counter on the instance of SQL Server.   
            stat.Create();  
        }  
```  
  
## <a name="creating-and-update-statistics-in-powershell"></a>PowerShell での統計の作成および更新  
 このコード例では、既存のデータベースに新しいテーブルを作成し、<xref:Microsoft.SqlServer.Management.Smo.Statistic> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> オブジェクトを作成しています。  
  
```powershell  
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
CD AdventureWorks2012\tables  
  
#Get a reference to the table  
$tb = get-item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -argumentlist $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -argumentlist $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index   
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -argumentlist $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
  
  
