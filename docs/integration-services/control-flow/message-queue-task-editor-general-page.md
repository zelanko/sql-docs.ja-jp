---
title: "メッセージ キュー タスク エディター (全般 ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 25313cc6decaea073409143e468621a1ed40993c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="message-queue-task-editor-general-page"></a>[メッセージ キュー タスク エディター] ([全般] ページ)
  **[メッセージ キュー タスク エディター]** の **[全般]** ページを使用すると、メッセージ キュー タスクの名前と説明を設定したり、メッセージの形式を指定したり、タスクでメッセージを送受信できるかどうかを指定したりできます。  
  
 このタスクの詳細については、「 [Message Queue Task](../../integration-services/control-flow/message-queue-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **名前**  
 メッセージ キュー タスクの固有の名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **Description**  
 メッセージ キュー タスクの説明を入力します。  
  
 **[Use2000Format]**  
 Message Queuing (MSMQ) の 2000 形式を使用するかどうかを指定します。 既定値は **False**です。  
  
 **[MSMQConnection]**  
 既存の MSMQ 接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック**: [MSMQ 接続マネージャー](../../integration-services/connection-manager/msmq-connection-manager.md)、[MSMQ 接続マネージャー エディター](../../integration-services/connection-manager/msmq-connection-manager-editor.md)  
  
 **メッセージ**  
 メッセージ キュー タスクでメッセージを送信するのか、受信するのかを指定します。 **[メッセージの送信]**を選択すると、ダイアログ ボックスの左側のペインに [送信] ページが表示されます。 **[メッセージの受信]**を選択すると、[受信] ページが表示されます。 既定では、 **[メッセージの送信]**に設定されています。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [メッセージ キュー タスク エディター & #40 です。受信ページ"&"#41;](../../integration-services/control-flow/message-queue-task-editor-receive-page.md)   
 [メッセージ キュー タスク エディター & #40 です。送信する ページ &#41;](../../integration-services/control-flow/message-queue-task-editor-send-page.md)   
 [「式」 ページ](../../integration-services/expressions/expressions-page.md)  
  
  
