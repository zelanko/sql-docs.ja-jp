---
title: "作成、変更、およびユーザー定義関数の削除 |Microsoft ドキュメント"
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
helpviewer_keywords: user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
caps.latest.revision: "49"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2551a7393df1d4e896a78d40f244aa914de0ef5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>ユーザー定義関数の作成、変更、および削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>オブジェクトは、ユーザーがユーザー定義関数をプログラムで管理できる機能を提供[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 ユーザー定義関数では、入力パラメーターおよび出力パラメーターに加えて、テーブル列への直接参照もサポートされます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]これらの前に、データベース内で登録するアセンブリはストアド プロシージャ内で使用、ユーザー定義関数、トリガー、およびユーザー定義データ型が必要です。 SMO は、<xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> オブジェクトを使用してこの機能をサポートします。  
  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>オブジェクト参照を .NET アセンブリ、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>、 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>、および<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A>プロパティです。  
  
 ときに、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>オブジェクト、.NET アセンブリを参照して、作成することで、アセンブリを登録する必要があります、<xref:Microsoft.SqlServer.Management.Smo.SqlAssembly>オブジェクトとに追加すること、<xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection>が属しているオブジェクト、<xref:Microsoft.SqlServer.Management.Smo.Database>オブジェクト。  
  
## <a name="example"></a>例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>Visual Basic でのユーザー定義スカラー関数の作成  
 このコード例は、作成し、入力のあるスカラー ユーザー定義関数を削除する方法を示しています。<xref:System.DateTime>オブジェクト パラメーターおよび整数型を返す[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]です。 ユーザー定義関数が作成された、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベース。 この例では、日付引数を取得して ISO 週番号を計算するユーザー定義関数 ISOweek が作成されます。 この関数で正しい計算を行うためには、関数を呼び出す前に、データベースの DATEFIRST オプションが 1 に設定されている必要があります。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.
Dim udf As UserDefinedFunction
udf = New UserDefinedFunction(db, "IsOWeek")
'Set the TextMode property to false and then set the other properties.
udf.TextMode = False
udf.DataType = DataType.Int
udf.ExecutionContext = ExecutionContext.Caller
udf.FunctionType = UserDefinedFunctionType.Scalar
udf.ImplementationType = ImplementationType.TransactSql
'Add a parameter.
Dim par As UserDefinedFunctionParameter
par = New UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime)
udf.Parameters.Add(par)
'Set the TextBody property to define the user defined function.
udf.TextBody = "BEGIN  DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"
'Create the user defined function on the instance of SQL Server.
udf.Create()
'Remove the user defined function.
udf.Drop()
``` 
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a>Visual C# でのユーザー定義スカラー関数の作成  
 このコード例は、作成し、入力のあるスカラー ユーザー定義関数を削除する方法を示しています。<xref:System.DateTime>オブジェクト パラメーターおよび整数型を返す[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]です。 ユーザー定義関数が作成された、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベース。 この例では、次のユーザー定義関数を作成します。 `ISOweek`」をご覧ください。 この関数は、日付引数を受け取って、ISO 週番号を計算します。 この関数で正しい計算を行うためには、関数を呼び出す前に、データベースの `DATEFIRST` オプションが `1` に設定されている必要があります。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a>PowerShell でのユーザー定義スカラー関数の作成  
 このコード例は、作成し、入力のあるスカラー ユーザー定義関数を削除する方法を示しています。<xref:System.DateTime>オブジェクト パラメーターおよび整数型を返す[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]です。 ユーザー定義関数が作成された、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベース。 この例では、次のユーザー定義関数を作成します。 `ISOweek`」をご覧ください。 この関数は、日付引数を受け取って、ISO 週番号を計算します。 この関数で正しい計算を行うためには、関数を呼び出す前に、データベースの `DATEFIRST` オプションが `1` に設定されている必要があります。  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.   
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction `  
-argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.   
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int   
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter `  
-argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.   
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.   
$udf.Create()  
  
# Remove the user-defined function.   
$udf.Drop()  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
  
  
