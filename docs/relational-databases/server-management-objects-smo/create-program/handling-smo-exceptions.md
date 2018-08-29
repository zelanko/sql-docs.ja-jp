---
title: SMO 例外の処理 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 942550cf7897ef1da84e31c2dfee8207eb0262b0
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085842"
---
# <a name="handling-smo-exceptions"></a>SMO 例外の処理
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  マネージド コードでは、エラーが発生すると例外がスローされます。 SMO のメソッドやプロパティは、戻り値で成功や失敗をレポートしません。 代わりに、例外ハンドラーによって例外のキャッチと処理を行うことができます。  
  
 SMO にはさまざまな例外クラスが存在します。 例外の詳細は、例外に関するテキスト メッセージを指定している **Message** プロパティなどの例外プロパティから抽出することができます。  
  
 例外処理ステートメントは、プログラミング言語に固有です。 たとえば、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic では、**キャッチ**ステートメント。  
  
## <a name="inner-exceptions"></a>内部例外  
 例外は、一般または固有のどちらかです。 一般例外には、固有の例外のセットが含まれています。 いくつかの **Catch** ステートメントを使用して、予想されるエラーの処理を行い、残りのエラーを一般例外の処理コードでは処理されないようにすることができます。 例外は、連鎖シーケンスによってしばしば発生します。 SMO 例外が、別の SQL 例外によって生じていることが少なくありません。 これを検出する方法は、 **InnerException** プロパティを連続的に使用して、最終的なトップレベル例外を発生している元の例外を判断します。  
  
> [!NOTE]  
>  **SQLException**で例外が宣言されている、 **System.Data.SqlClient**名前空間。  
  
 ![元のレベルを示す図を図](../../../relational-databases/server-management-objects-smo/create-program/media/exception-flow.gif "を元のレベルを示す図を図")  
  
 このダイアグラムは、アプリケーションの層を通じた例外のフローを示しています。  
  
## <a name="example"></a>例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。
  
## <a name="catching-an-exception-in-visual-basic"></a>Visual Basic での例外のキャッチ  
 このコード例を使用する方法を示しています、**お試しください.キャッチしてください.最後に**[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] SMO 例外をキャッチするステートメント。 SMO 例外はすべて SmoException 型であり、これらは SMO のリファレンスに一覧されています。 エラーの原因を示すために、内部例外のシーケンスが表示されます。 詳細については、次を参照してください。、 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET ドキュメント。  
  
```VBNET
'This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace is included.
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.
'Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.
Dim op As [Operator]
op = New [Operator](srv.JobServer, "Test_Operator")
op.Create()
'Start exception handling.
Try
    'Create the operator again to cause an SMO exception.
    Dim opx As OperatorCategory
    opx = New OperatorCategory(srv.JobServer, "Test_Operator")
    opx.Create()
    'Catch the SMO exception
Catch smoex As SmoException
    Console.WriteLine("This is an SMO Exception")
    'Display the SMO exception message.
    Console.WriteLine(smoex.Message)
    'Display the sequence of non-SMO exceptions that caused the SMO exception.
    Dim ex As Exception
    ex = smoex.InnerException
    Do While ex.InnerException IsNot (Nothing)
        Console.WriteLine(ex.InnerException.Message)
        ex = ex.InnerException
    Loop
    'Catch other non-SMO exceptions.
Catch ex As Exception
    Console.WriteLine("This is not an SMO exception.")
End Try
``` 
  
## <a name="catching-an-exception-in-visual-c"></a>Visual C# での例外のキャッチ  
 このコード例では、 **Try…Catch…Finally** Visual C# ステートメントを使用して SMO 例外をキャッチする方法を示しています。 SMO 例外はすべて SmoException 型であり、これらは SMO のリファレンスに一覧されています。 エラーの原因を示すために、内部例外のシーケンスが表示されます。 詳細については、C# のドキュメントを参照してください。  
  
```csharp  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
