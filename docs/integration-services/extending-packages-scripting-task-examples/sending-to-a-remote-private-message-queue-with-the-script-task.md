---
title: "スクリプト タスクによるリモート プライベート メッセージ キューに送信する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5ab9314ef0825486914d1801bfa2b9613883b43e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>スクリプト タスクによるリモート プライベート メッセージ キューへの送信
  メッセージ キュー (MSMQ) では、開発者がメッセージを送受信することにより、アプリケーション プログラムとすばやく確実に通信できます。 メッセージ キューは、ローカル コンピューターまたはリモート コンピューターに存在し、パブリックであることも、プライベートであることもあります。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の MSMQ 接続マネージャーとメッセージ キュー タスクでは、リモート コンピューター上のプライベート キューへの送信はサポートされません。 ただし、スクリプト タスクを使用することにより、リモート プライベート キューにメッセージを簡単に送信できます。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>Description  
 次の例では、オブジェクトおよび System.Messaging 名前空間のメソッドと共に、既存の MSMQ 接続マネージャーを使用して、リモート プライベート メッセージ キューにパッケージ変数に含まれているテキストを送信します。 MSMQ 接続マネージャーの M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) メソッドの呼び出しが返された、 **MessageQueue**オブジェクト**送信**メソッドは、このタスクを実行します。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  既定の名前を使用して MSMQ 接続マネージャーを作成します。 有効なリモート プライベート キューのパスを次の形式で設定します。  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]という名前の変数**MessageText**型の**文字列**メッセージ テキストをスクリプトに渡す。 この変数の値として既定のメッセージを入力します。  
  
3.  スクリプト タスクをデザイン画面に追加して編集します。 **スクリプト**のタブ、**スクリプト タスク エディター**、追加、`MessageText`変数を**ReadOnlyVariables**変数をスクリプト内で使用できるようにするプロパティ.  
  
4.  をクリックして**スクリプトの編集**を開くには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) スクリプト エディターです。  
  
5.  スクリプト プロジェクト内の参照を追加、 **System.Messaging**名前空間。  
  
6.  スクリプト ウィンドウの内容を、次のコードで置き換えます。  
  
## <a name="code"></a>コード  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
## <a name="see-also"></a>参照  
 [メッセージ キュー タスク](../../integration-services/control-flow/message-queue-task.md)  
  
  

