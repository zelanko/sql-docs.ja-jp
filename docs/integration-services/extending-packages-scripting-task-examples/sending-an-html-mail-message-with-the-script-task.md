---
title: "スクリプト タスクによる HTML メール メッセージを送信する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b5f50a79ca83243ea130c77a0d95ab402ba2d31a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="sending-an-html-mail-message-with-the-script-task"></a>スクリプト タスクによる HTML メール メッセージの送信
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の SendMail タスクでは、プレーン テキスト形式のメール メッセージのみがサポートされています。 ただし、.NET Framework のスクリプト タスクとメール機能を使用して、HTML メール メッセージを簡単に送信できます。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>Description  
 次の例では、 **System.Net.Mail**名前空間を構成して、HTML メール メッセージを送信します。 スクリプトから、件名、およびパッケージ変数からの電子メールの本文を取得、それらを新規作成に使用**MailMessag**e、およびセットをその**IsBodyHtml**プロパティを**True**です。 別のパッケージ変数のインスタンスを初期化しますから SMTP サーバー名を取得し、 **System.Net.Mail.SmtpClient**、呼び出しとその**送信**html 形式のメッセージを送信する方法です。 このサンプルでは、メッセージ送信機能をサブルーチンにカプセル化しているため、他のスクリプトで再利用できます。  
  
#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a>このスクリプト タスクの例を SMTP 接続マネージャーを使用せずに構成するには  
  
1.  `HtmlEmailTo`、`HtmlEmailFrom`、および `HtmlEmailSubject` という名前の文字列変数を作成し、これらに適切な値を割り当てて、有効なテスト メッセージを用意します。  
  
2.  `HtmlEmailBody` という名前の文字列変数を作成し、HTML マークアップの文字列を割り当てます。 例:  
  
    ```  
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>  
    ```  
  
3.  `HtmlEmailServer` という名前の文字列変数を作成し、匿名発信メッセージを受け入れる、使用可能な SMTP サーバーの名前を割り当てます。  
  
4.  これらの変数の 5 つすべてを割り当てる、 **ReadOnlyVariables**を新しいスクリプト タスクのプロパティです。  
  
5.  インポート、 **System.Net**と**System.Net.Mail**コードに名前空間。  
  
 このトピックのサンプル コードでは、SMTP サーバー名をパッケージ変数から取得します。 ただし、SMTP 接続マネージャーを利用して接続情報をカプセル化し、コード内で接続マネージャーからサーバー名を抽出することもできます。 SMTP 接続マネージャーの <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> メソッドは、次の形式の文字列を返します。  
  
 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`  
  
 使用することができます、 **String.Split**以上でこの引数のリストをセミコロン (;) で個々 の文字列の配列に分割するメソッドが等号 (=)、およびサーバー名としての配列から 2 番目の引数 (subscript 1) を抽出します。  
  
#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a>このスクリプト タスクの例を SMTP 接続マネージャーを使用して構成するには  
  
1.  スクリプト タスクを削除することで前に構成を変更、`HtmlEmailServer`の一覧から変数**ReadOnlyVariables**です。  
  
2.  サーバー名を取得する次のコード行を置き換えます。  
  
    ```  
    Dim smtpServer As String = _  
      Dts.Variables("HtmlEmailServer").Value.ToString  
    ```  
  
     次の行。  
  
    ```  
    Dim smtpConnectionString As String = _  
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)  
    Dim smtpServer As String = _  
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)  
    ```  
  
## <a name="code"></a>コード  
  
```vb  
Public Sub Main()  
  
  Dim htmlMessageTo As String = _  
    Dts.Variables("HtmlEmailTo").Value.ToString  
  Dim htmlMessageFrom As String = _  
    Dts.Variables("HtmlEmailFrom").Value.ToString  
  Dim htmlMessageSubject As String = _  
    Dts.Variables("HtmlEmailSubject").Value.ToString  
  Dim htmlMessageBody As String = _  
    Dts.Variables("HtmlEmailBody").Value.ToString  
  Dim smtpServer As String = _  
    Dts.Variables("HtmlEmailServer").Value.ToString  
  
  SendMailMessage( _  
      htmlMessageTo, htmlMessageFrom, _  
      htmlMessageSubject, htmlMessageBody, _  
      True, smtpServer)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Sub SendMailMessage( _  
    ByVal SendTo As String, ByVal From As String, _  
    ByVal Subject As String, ByVal Body As String, _  
    ByVal IsBodyHtml As Boolean, ByVal Server As String)  
  
  Dim htmlMessage As MailMessage  
  Dim mySmtpClient As SmtpClient  
  
  htmlMessage = New MailMessage( _  
    SendTo, From, Subject, Body)  
  htmlMessage.IsBodyHtml = IsBodyHtml  
  
  mySmtpClient = New SmtpClient(Server)  
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials  
  mySmtpClient.Send(htmlMessage)  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();  
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();  
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();  
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();  
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();  
  
            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)  
        {  
  
            MailMessage htmlMessage;  
            SmtpClient mySmtpClient;  
  
            htmlMessage = new MailMessage(SendTo, From, Subject, Body);  
            htmlMessage.IsBodyHtml = IsBodyHtml;  
  
            mySmtpClient = new SmtpClient(Server);  
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;  
            mySmtpClient.Send(htmlMessage);  
  
        }  
```  
  
## <a name="see-also"></a>参照  
 [メール送信タスク](../../integration-services/control-flow/send-mail-task.md)  
  
  
