---
title: 作成、変更、およびストアド プロシージャの削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe7fb603ae3b0f3550d63d4c9b886934b31a28ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074502"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>ストアド プロシージャの作成、変更、および削除
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理オブジェクト (SMO)、ストアド プロシージャがによって表されるが、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>オブジェクト。  
  
 作成、 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> smo オブジェクトの設定が必要、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A>プロパティを[!INCLUDE[tsql](../../../includes/tsql-md.md)]ストアド プロシージャを定義するスクリプト。 パラメーターが必要な\@プレフィックスし、を使用して個別に作成する必要があります<xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>オブジェクトとへの追加、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>のコレクション、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>オブジェクト。  
  
## <a name="example"></a>例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual Studio .NET で Visual Basic SMO プロジェクトを作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)または[Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>Visual Basic でのストアド プロシージャの作成、変更、および削除  
 このコード例のストアド プロシージャを作成する方法を示しています、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベース。 この例では、従業員 ID 番号が指定されると、従業員の姓を返します。 このストアド プロシージャには、従業員 ID 番号を指定する 1 つの入力パラメーターと、従業員の姓を返す 1 つの出力パラメーターが必要です。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>Visual C# でのストアド プロシージャの作成、変更、および削除  
 このコード例のストアド プロシージャを作成する方法を示しています、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベース。 この例では、従業員 ID 番号 (`BusinessEntityID`) が指定されると、従業員の姓を返します。 このストアド プロシージャには、従業員 ID 番号を指定する 1 つの入力パラメーターと、従業員の姓を返す 1 つの出力パラメーターが必要です。  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>PowerShell でのストアド プロシージャの作成、変更、および削除  
 このコード例のストアド プロシージャを作成する方法を示しています、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベース。 この例では、従業員 ID 番号 (`BusinessEntityID`) が指定されると、従業員の姓を返します。 このストアド プロシージャには、従業員 ID 番号を指定する 1 つの入力パラメーターと、従業員の姓を返す 1 つの出力パラメーターが必要です。  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
$sp  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure `  
-argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.   
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.   
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.   
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.   
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.   
$sp.Drop()  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
  
  
