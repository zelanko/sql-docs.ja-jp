---
title: "セキュリティ拡張機能の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
caps.latest.revision: 22
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: df3ae2c8b5ccde0beffeb2f3f18d68bdb4c4a782
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="security-extensions-overview"></a>セキュリティ拡張機能の概要
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] セキュリティ拡張機能を使用すると、ユーザーまたはグループの認証と承認を行えます。つまり、複数のユーザーがレポート サーバーにログオンし、それぞれ異なるタスクや操作を実行できます。 既定では、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は Windows ベースの認証拡張機能を使用します。この拡張機能は Windows アカウント プロトコルを使用して、システムのアカウントを持っていると主張するユーザーの ID を検証します。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は、ロールベースのセキュリティ システムを使用してユーザーを承認します。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のロールベースのセキュリティ モデルは、他の技術に見られるロールベースのセキュリティ モデルと類似しています。  
  
 セキュリティ拡張機能はオープンで拡張可能な API に基づいているので、認証と承認の新しい拡張機能を [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に作成できます。 以下は、フォームベースの認証と承認を使用する一般的なセキュリティ拡張機能の実装例です。  
  
 ![Reporting Services のセキュリティ拡張フロー](../../../reporting-services/extensions/security-extension/media/rosettasecurityextensionflow.gif "Reporting Services のセキュリティ拡張フロー")  
  
 図に示すように、認証と承認は次のように行われます。  
  
1.  ユーザーが URL を使用してレポート マネージャーへのアクセスを試行します。このユーザーは、クライアント アプリケーションに必要なユーザー資格情報を収集するフォームにリダイレクトされます。  
  
2.  ユーザーが資格情報をフォームに送信します。  
  
3.  ユーザー資格情報は、<xref:ReportService2010.ReportingService2010.LogonUser%2A> メソッドによって Reporting Services Web サービスに送信されます。  
  
4.  Web サービスは顧客指定のセキュリティ拡張機能を呼び出し、カスタム セキュリティ機関に存在するユーザー名とパスワードを検証します。  
  
5.  認証後、Web サービスは認証チケット (クッキー) を作成、管理し、レポート マネージャーのホーム ページに対するユーザーのロールを検証します。  
  
6.  Web サービスがクッキーをブラウザーに返し、レポート マネージャーに適切なユーザー インターフェイスを表示します。  
  
7.  ユーザーの認証後、HTTP ヘッダーにクッキーを追加して転送する際、ブラウザーはレポート マネージャーに要求を発信します。 これらの要求は、レポート マネージャー アプリケーション内でユーザーが行った操作に対応しています。  
  
8.  HTTP ヘッダーのクッキーは、要求されたユーザー操作と共に Web サービスに転送されます。  
  
9. クッキーの有効性が確認された場合は、レポート サーバーがセキュリティ記述子を返します。さらに、要求された操作に関するレポート サーバー データベースからの情報を返します。  
  
10. クッキーが有効な場合、レポート サーバーはセキュリティ拡張機能を呼び出して、ユーザーが特定の操作の実行を許可されているかどうかを調べます。  
  
11. ユーザーに許可が与えられている場合、レポート サーバーは要求された操作を実行して、呼び出し元に制御を返します。  
  
12. ユーザーの認証後、レポート サーバーへの URL アクセスでは常に同じクッキーが使用されます。 クッキーは、HTTP ヘッダーの一部として転送されます。  
  
13. セッションが終了するまで、ユーザーは引き続き、レポート サーバーに対する操作を要求します。  
  
## <a name="when-to-implement-a-security-extension"></a>セキュリティ拡張機能を実装すべき状況  
 できるだけ Windows 認証を使用することをお勧めします。 ただし、次の場合は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] でカスタム認証と承認を使用した方が適していることがあります。  
  
-   Windows アカウントを使用できないインターネット アプリケーションまたはエクストラネット アプリケーションを実行する。  
  
-   ユーザーとロールを独自に定義しており、それに合わせた承認方法を [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] で使用する必要がある。  
  
## <a name="see-also"></a>参照  
 [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)   
 [カスタム認証クッキーを渡すためのレポート マネージャーを構成します。](https://msdn.microsoft.com/library/ms345241(v=sql.110).aspx)  
  
  
