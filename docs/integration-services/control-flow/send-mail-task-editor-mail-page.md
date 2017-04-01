---
title: "[メール送信タスク エディター] ([メール] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sendmailtask.mail.f1"
helpviewer_keywords: 
  - "メール送信タスク エディター"
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# [メール送信タスク エディター] ([メール] ページ)
  **[メール送信タスク エディター]** ダイアログ ボックスの **[メール]** ページを使用すると、受信者、メッセージの種類、メッセージの重要度を指定できます。 メッセージにファイルを添付することもできます。 メッセージ テキストは、入力した文字列、テキストが含まれるファイルへのファイル接続、またはテキストが含まれる変数の名前になります。  
  
 このタスクの詳細については、「 [Send Mail Task](../../integration-services/control-flow/send-mail-task.md)」を参照してください。  
  
## オプション  
 **[SMTPConnection]**  
 一覧で SMTP 接続マネージャーを選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
> [!IMPORTANT]  
>  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
 **関連項目:** [SMTP 接続マネージャー](../../integration-services/connection-manager/smtp-connection-manager.md)  
  
 **From**  
 送信者の電子メール アドレスを指定します。  
  
 **変換先**  
 受信者の電子メール アドレスを指定します。受信者はセミコロンで区切ります。  
  
 **[Cc]**  
 メッセージのコピーを受け取る受信者の電子メール アドレスを指定します。受信者はセミコロンで区切ります。  
  
 **[Bcc]**  
 メッセージのコピーを Bcc として受け取る受信者の電子メール アドレスを指定します。受信者はセミコロンで区切ります。  
  
 **[Subject]**  
 電子メール メッセージの件名を指定します。  
  
 **[MessageSourceType]**  
 メッセージのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|メッセージ テキストをソースとして設定します。 この値を選択すると、動的オプション **[MessageSource]** が表示されます。|  
|**[ファイル接続]**|メッセージ テキストが含まれるファイルをソースとして設定します。 この値を選択すると、動的オプション **[MessageSource]** が表示されます。|  
|**変数**|メッセージ テキストが含まれる変数をソースとして設定します。 この値を選択すると、動的オプション **[MessageSource]** が表示されます。|  
  
 **[Priority]**  
 メッセージの重要度を設定します。  
  
 **[Attachments]**  
 電子メール メッセージに添付するファイル名を指定します。ファイル名はパイプ文字 (|) で区切ります。  
  
> [!NOTE]  
>  [宛先]、[CC]、[BCC] 行の文字数は、インターネット標準に従って 256 文字に制限されています。  
  
## MessageSourceType 動的オプション  
  
### [MessageSourceType] = [直接入力]  
 **[MessageSource]**  
 メッセージ テキストを入力するか、参照ボタン ([...]) をクリックして **[メッセージの送信元]** ダイアログ ボックスにメッセージを入力します。  
  
### [MessageSourceType] = [ファイル接続]  
 **[MessageSource]**  
 一覧でファイル接続マネージャーを選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### [MessageSourceType] = [変数]  
 **[MessageSource]**  
 一覧で変数を選択するか、**[\<新しい変数>]** をクリックして新しい変数を作成します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](../Topic/Add%20Variable.md)  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[メール送信タスク エディター] &#40;[全般] ページ&#41;](../Topic/Send%20Mail%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)  
  
  