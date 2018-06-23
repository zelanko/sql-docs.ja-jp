---
title: 作成、変更、および既定の設定を削除する |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7daddec0a7c96776938f2824635b719341ecbe4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073219"
---
# <a name="creating-altering-and-removing-defaults"></a>既定値の作成、変更、および削除
  SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト) では、既定の制約は <xref:Microsoft.SqlServer.Management.Smo.Default> オブジェクトで表現します。  
  
 挿入する値を設定するには、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Default> プロパティを使用します。 挿入する値は、定数であっても、GETDATE() などの定数値を返す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントであってもかまいません。 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> プロパティは、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドを使用して変更することはできません。 <xref:Microsoft.SqlServer.Management.Smo.Default> オブジェクトをいったん削除してから再作成する必要があります。  
  
## <a name="example"></a>例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual Studio .NET で Visual Basic SMO プロジェクトを作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)または[Visual C を作成する&#35;Visual Studio .NET での SMO プロジェクト](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>Visual Basic での既定値の作成、変更、および削除  
 このコード例では、シンプル テキストである既定値と [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントである別の既定値を作成する方法を示します。 既定値を列にアタッチするには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> メソッドを使用し、列からのデタッチには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> メソッドを使用する必要があります。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>Visual C# での既定値の作成、変更、および削除  
 このコード例では、シンプル テキストである既定値と [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントである別の既定値を作成する方法を示します。 既定値を列にアタッチするには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> メソッドを使用し、列からのデタッチには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> メソッドを使用する必要があります。  
  
```  
{  
  
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a>PowerShell での既定値の作成、変更、および削除  
 このコード例では、シンプル テキストである既定値と [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントである別の既定値を作成する方法を示します。 既定値を列にアタッチするには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> メソッドを使用し、列からのデタッチには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> メソッドを使用する必要があります。  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
  
  