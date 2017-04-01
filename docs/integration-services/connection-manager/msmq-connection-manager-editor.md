---
title: "MSMQ 接続マネージャー エディター | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msmqconnectionmanager.f1"
helpviewer_keywords: 
  - "MSMQ 接続マネージャー エディター"
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# MSMQ 接続マネージャー エディター
  **[MSMQ 接続マネージャー]** ダイアログ ボックスでは、Message Queuing (MSMQ) メッセージ キューへのパスを指定できます。  
  
 MSMQ 接続マネージャーの詳細については、「 [MSMQ Connection Manager](../../integration-services/connection-manager/msmq-connection-manager.md)」を参照してください。  
  
> [!NOTE]  
>  MSMQ 接続マネージャーでは、ローカルのパブリック キューと専用キュー、およびリモートのパブリック キューがサポートされています。 リモートの専用キューはサポートされていません。 スクリプト タスクを使用する回避策については、「 [Sending to a Remote Private Message Queue with the Script Task](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)」を参照してください。  
  
## オプション  
 **名前**  
 ワークフローにおける MSMQ 接続マネージャーの一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **Description**  
 接続マネージャーの説明を記述します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。  
  
 **[パス]**  
 メッセージ キューの完全なパスを入力します。 パスの形式はキューの種類によって異なります。  
  
|[キューの種類]|パスのサンプル|  
|----------------|-----------------|  
|パブリック|\<コンピューター名>\\<キュー名\>|  
|Private|\<コンピューター名>\Private$\\<キュー名\>|  
  
 "." を使用してローカル コンピューターを表すことができます。  
  
 **テスト**  
 MSMQ 接続マネージャーを構成した後に、**[テスト]** をクリックして、接続が利用可能であることを確認します。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)  
  
  