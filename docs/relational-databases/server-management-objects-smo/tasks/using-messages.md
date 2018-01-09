---
title: "メッセージを使用して |Microsoft ドキュメント"
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
helpviewer_keywords: messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cf26f0e7f9795e793f9da85d312f39fe44b611f7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="using-messages"></a>メッセージの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SMO では、システム メッセージがによって表される、<xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection>オブジェクトに属し、**サーバー**オブジェクト。 システム メッセージが変更されることはできません、ため**SystemMessage**オブジェクトのプロパティは読み取り専用です。  
  
 SMO では、プログラム上では <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> オブジェクトを使用してユーザー定義メッセージを表現します。 既存のユーザー定義メッセージは、コレクションを反復処理することで検索することができます。 新しいをインスタンス化して、新しいユーザー定義のメッセージを作成できます**UserDefinedMessage**オブジェクトと適切なプロパティを設定します。  
  
## <a name="examples"></a>使用例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Visual Basic での特定のシステム メッセージの検索  
 このコード例では、システム メッセージを ID 番号で識別してメッセージを表示する方法を示します。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference an existing system message using the ItemByIdAndLanguage method.
Dim msg As SystemMessage
msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")
'Display the message ID and  text.
Console.WriteLine(msg.ID.ToString + " " + msg.Text)
```
  
## <a name="finding-a-particular-system-message-in-visual-c"></a>Visual C# での特定のシステム メッセージの検索  
 このコード例では、システム メッセージを ID 番号で識別してメッセージを表示する方法を示します。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a>PowerShell での特定のシステム メッセージの検索  
 このコード例では、システム メッセージを ID 番号で識別してメッセージを表示する方法を示します。  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Visual Basic での新しいユーザー定義メッセージの追加  
 コード例では、50000 より大きい ID を使用してユーザー定義メッセージを作成する方法を示します。  
  
```VBNET  
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a>Visual C# での新しいユーザー定義メッセージの追加  
 コード例では、50000 より大きい ID を使用してユーザー定義メッセージを作成する方法を示します。  
  
```csharp  
{  
  
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a>PowerShell での新しいユーザー定義メッセージの追加  
 コード例では、50000 より大きい ID を使用してユーザー定義メッセージを作成する方法を示します。  
  
```powershell  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message  
  
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -argumentlist `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
  
  
