---
title: スクリプト タスクによるリモート プライベート メッセージ キューへの送信 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e4791e826adccb925241b02312900ea524f228e0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62768468"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>スクリプト タスクによるリモート プライベート メッセージ キューへの送信
  メッセージ キュー (MSMQ) では、開発者がメッセージを送受信することにより、アプリケーション プログラムとすばやく確実に通信できます。 メッセージ キューは、ローカル コンピューターまたはリモート コンピューターに存在し、パブリックであることも、プライベートであることもあります。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の MSMQ 接続マネージャーとメッセージ キュー タスクでは、リモート コンピューター上のプライベート キューへの送信はサポートされません。 ただし、スクリプト タスクを使用することにより、リモート プライベート キューにメッセージを簡単に送信できます。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>説明  
 次の例では、既存の MSMQ 接続マネージャーを System.Messaging 名前空間のオブジェクトおよびメソッドと共に使用して、パッケージ変数に含まれているテキストをリモート プライベート メッセージ キューに送信します。 MSMQ 接続マネージャーの M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection (System.object) メソッドを呼び出すと、このタスクを処理**MessageQueue**するメソッドを`Send`持つ MessageQueue オブジェクトが返されます。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  既定の名前を使用して MSMQ 接続マネージャーを作成します。 有効なリモート プライベート キューのパスを次の形式で設定します。  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  メッセージテキスト[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]をスクリプトに渡すために`String` 、型の**messagetext**という名前の変数を作成します。 この変数の値として既定のメッセージを入力します。  
  
3.  スクリプト タスクをデザイン画面に追加して編集します。 **[スクリプト タスク エディター]** の **[スクリプト]** タブで、`MessageText`ReadOnlyVariables**プロパティに** 変数を追加し、この変数をスクリプト内で使用できるようにします。  
  
4.  **[スクリプトの編集]** をクリックして、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) スクリプト エディターを開きます。  
  
5.  スクリプト プロジェクトに `System.Messaging` 名前空間への参照を追加します。  
  
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
  
![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [Message Queue Task](../control-flow/message-queue-task.md)  
  
  
