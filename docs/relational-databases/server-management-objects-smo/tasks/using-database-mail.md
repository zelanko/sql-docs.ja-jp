---
title: "データベース メールの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7ddfd4155b0dfe0a5b624935c79098fb82ed0ea
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="using-database-mail"></a>データベース メールの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SMO では、データベース メール サブシステムで表される、<xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>によって参照されるオブジェクト、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>プロパティです。 SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトを使用すると、データベース メール サブシステムを構成して、プロファイルおよびメール アカウントを管理することができます。 SMO<xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>オブジェクトに属している、**サーバー**オブジェクト、メール アカウントのスコープがサーバー レベルにあることを意味します。  
  
## <a name="examples"></a>使用例  
 提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
 プログラムを使用する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース メールは、含める必要があります、 **Imports** Mail 名前空間を修飾するステートメント。 アプリケーションの宣言の前、かつ他の **Imports** ステートメントの後に、次のようにステートメントを挿入します。  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Visual Basic によるデータベース メール アカウントの作成  
 このコード例では、SMO で電子メール アカウントを作成する方法を示します。 データベース メールは <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトで表現され、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティによって参照されます。 SMO は、プログラムでデータベース メールを構成するために使用することはできますが、電子メールを送信したり、受信した電子メールを処理したりするために使用することはできません。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server()
'Define the Database Mail service with a SqlMail object variable and reference it using the Server Mail property.
Dim sm As SqlMail
sm = srv.Mail
'Define and create a mail account by supplying the Database Mail service, name, description, display name, and email address arguments in the constructor.
Dim a As MailAccount
a = New MailAccount(sm, "AdventureWorks Administrator", "AdventureWorks Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com")
a.Create()
```
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Visual C# によるデータベース メール アカウントの作成  
 このコード例では、SMO で電子メール アカウントを作成する方法を示します。 データベース メールは <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトで表現され、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティによって参照されます。 SMO は、プログラムでデータベース メールを構成するために使用することはできますが、電子メールを送信したり、受信した電子メールを処理したりするために使用することはできません。  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>PowerShell によるデータベース メール アカウントの作成  
 このコード例では、SMO で電子メール アカウントを作成する方法を示します。 データベース メールは <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> オブジェクトで表現され、<xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Server> プロパティによって参照されます。 SMO は、プログラムでデータベース メールを構成するために使用することはできますが、電子メールを送信したり、受信した電子メールを処理したりするために使用することはできません。  
  
  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -argumentlist $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
  
  
