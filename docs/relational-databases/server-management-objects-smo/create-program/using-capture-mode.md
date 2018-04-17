---
title: キャプチャ モードを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, capture mode
- capture mode [SMO]
- SMO [SQL Server], capture mode
ms.assetid: ace29bf0-705a-434f-82e4-db99d01c5008
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d2c40023b2a4bab78f6d3d68c059ba7c8e8f2232
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-capture-mode"></a>キャプチャ モードの使用
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO プログラムは、プログラムによって実行されるステートメントの代替または追加として、プログラムによって発行される同等の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントのキャプチャおよび記録を行うことができます。 キャプチャ モードを有効にするには、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用するか、<xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティを使用します。  
  
## <a name="example"></a>例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual C を作成する&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  

  
## <a name="enabling-capture-mode-in-visual-basic"></a>Visual Basic でのキャプチャ モードの有効化  
 このコードの例では、キャプチャ モードを有効化し、次に、キャプチャ バッファーに保持されている [!INCLUDE[tsql](../../../includes/tsql-md.md)] コマンドを表示しています。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Set the execution mode to CaptureSql for the connection.
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql
'Make a modification to the server that is to be captured.
srv.UserOptions.AnsiNulls = True
srv.Alter()
'Iterate through the strings in the capture buffer and display the captured statements.
Dim s As String
For Each s In srv.ConnectionContext.CapturedSql.Text
    Console.WriteLine(s)
Next
'Execute the captured statements.
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text)
'Revert to immediate execution mode. 
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql
```
  
## <a name="enabling-capture-mode-in-visual-c"></a>Visual C# でのキャプチャ モードの有効化  
 このコードの例では、キャプチャ モードを有効化し、次に、キャプチャ バッファーに保持されている [!INCLUDE[tsql](../../../includes/tsql-md.md)] コマンドを表示しています。  
  
```csharp  
{   
// Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
// Set the execution mode to CaptureSql for the connection.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql;   
// Make a modification to the server that is to be captured.   
srv.UserOptions.AnsiNulls = true;   
srv.Alter();   
// Iterate through the strings in the capture buffer and display the captured statements.   
string s;   
foreach ( String p_s in srv.ConnectionContext.CapturedSql.Text ) {   
   Console.WriteLine(p_s);   
}   
// Execute the captured statements.   
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text);   
// Revert to immediate execution mode.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
  
