---
title: "[メッセージ キュー タスク エディター] ([送信] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msgqueuetask.send.f1"
helpviewer_keywords: 
  - "メッセージ キュー タスク エディター"
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# [メッセージ キュー タスク エディター] ([送信] ページ)
   **[メッセージ キュー タスク エディター]** ダイアログ ボックスの **[送信]** ページを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージからメッセージを送信するメッセージ キュー タスクを構成できます。  
  
 このタスクの詳細については、「 [Message Queue Task](../../integration-services/control-flow/message-queue-task.md)」を参照してください。  
  
## オプション  
 **[UseEncryption]**  
 メッセージを暗号化するかどうかを示します。 既定値は **False**です。  
  
 **[EncryptionAlgorithm]**  
 暗号化を使用する場合は、使用する暗号化アルゴリズムを指定します。 メッセージ キュー タスクでは、RC2 と RC4 のアルゴリズムを使用できます。 既定値は **[RC2]**です。  
  
> [!NOTE]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。  
  
> [!IMPORTANT]  
>  これらは、メッセージ キュー (MSMQ) テクノロジでサポートされる暗号化アルゴリズムです。 現在、いずれの暗号化アルゴリズムも、メッセージ キューでまだサポートされていない最新のアルゴリズムと比較して、暗号強度の弱さが指摘されています。 そのため、メッセージ キュー タスクを使ってメッセージを送信する場合は、必要な暗号強度を満たすことができるかどうかを十分に検討する必要があります。  
  
 **[MessageType]**  
 メッセージ型を指定します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[データ ファイル メッセージ]**|メッセージはファイルに格納されます。 この値を選択すると、動的オプションの **[DataFileMessage]**が表示されます。|  
|**[変数メッセージ]**|メッセージは変数に格納されます。 この値を選択すると、動的オプションの **[VariableMessage]**が表示されます。|  
|**[文字列メッセージ]**|メッセージはメッセージ キュー タスクに格納されます。 この値を選択すると、動的オプションの **[StringMessage]**が表示されます。|  
  
## [MessageType] の動的オプション  
  
### [MessageType] = [データ ファイル メッセージ]  
 **[DataFileMessage]**  
 データ ファイルのパスを入力します。または、参照ボタン (**[...]**) をクリックし、データ ファイルを指定します。  
  
### [MessageType] = [変数メッセージ]  
 **[VariableMessage]**  
 変数名を入力します。または、参照ボタン (**[...]**) をクリックし、変数を指定します。 変数はコンマで区切って指定します。  
  
 **関連項目 :** 「変数の選択」  
  
### [MessageType] = [文字列メッセージ]  
 **[StringMessage]**  
 文字列メッセージを入力します。または、参照ボタン (**[...]**) をクリックし、メッセージを **[メッセージの入力]** ダイアログ ボックスに入力します。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[メッセージ キュー タスク エディター] ([全般] ページ)](../Topic/Message%20Queue%20Task%20Editor%20\(General%20Page\).md)   
 [メッセージ キュー タスク エディター ([受信] ページ)](../Topic/Message%20Queue%20Task%20Editor%20\(Receive%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)  
  
  