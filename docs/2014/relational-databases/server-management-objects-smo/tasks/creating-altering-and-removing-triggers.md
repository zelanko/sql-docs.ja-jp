---
title: トリガーの作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13b494e4c2d8d822eb6d25d53d3b50962a65ef49
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85037659"
---
# <a name="creating-altering-and-removing-triggers"></a>トリガーの作成、変更、および削除
  SMO では、<xref:Microsoft.SqlServer.Management.Smo.Trigger> オブジェクトを使用してトリガーが表現されます。 トリガーが [!INCLUDE[tsql](../../../includes/tsql-md.md)] 起動されたときに実行されるコードは、 <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> トリガーオブジェクトのプロパティによって設定されます。 トリガーの型は、<xref:Microsoft.SqlServer.Management.Smo.Trigger> プロパティなど、<xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> オブジェクトのその他のプロパティを使用することで設定します。 これは、親テーブル上のレコードの `UPDATE` によってトリガーが起動されるかどうかを指定する、ブール型のプロパティです。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Trigger> オブジェクトは、従来のデータ操作言語 (DML) トリガーを表します。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降のバージョンでは、データ定義言語 (DDL) トリガーもサポートされます。 DDL トリガーは、<xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> オブジェクトで表現します。  
  
## <a name="example"></a>例  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>Visual Basic でのトリガーの作成、変更、および削除  
 このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。 トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>Visual C# でのトリガーの作成、変更、および削除  
 このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。 トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>PowerShell でのトリガーの作成、変更、および削除  
 このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。 トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = Get-Item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger -argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.
$tr.Create()  
  
#Remove the trigger.
$tr.Drop()  
```  
