---
title: 権限借用と接続の資格情報 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f2cc3fc4695c9e0b2a723668f09fc1bf388dabaa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176624"
---
# <a name="impersonation-and-credentials-for-connections"></a>接続の権限借用と資格情報
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR (共通言語ランタイム) 統合では、複雑な Windows 認証を使用する方が、SQL Server 認証を使用するよりもセキュリティが向上します。 Windows 認証を使用する場合には、次の点を考慮してください。  
  
 Windows に接続する SQL Server プロセスは、SQL Server Windows サービス アカウントのセキュリティ コンテキストを既定で取得します。 ただし、CLR 関数をプロキシ ID にマッピングすることにより、その発信接続に対し、Windows サービス アカウントとは異なるセキュリティ コンテキストを設定することができます。  
  
 場合によっては、サービス アカウントで実行する代わりに、`SqlContext.WindowsIdentity` プロパティを使用して呼び出し元の権限を借用することもあります。 `WindowsIdentity` インスタンスは、呼び出し元のコードを実行するクライアントの ID を表し、クライアントで Windows 認証を使用する場合のみ入手できます。 `WindowsIdentity` インスタンスを取得すると、`Impersonate` を呼び出してスレッドのセキュリティ トークンを変更し、その後でクライアントの代わりに ADO.NET 接続を開くことができます。  
  
 SQLContext.WindowsIdentity.Impersonate を呼び出した後は、ローカル データにアクセスすることはできませんし、システム データにアクセスすることはできません。 もう一度、データにアクセスするには、WindowsImpersonationContext.Undo を呼び出す必要があります。  
  
 次の例では、`SqlContext.WindowsIdentity` プロパティを使用して呼び出し元の権限を借用します。  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  権限借用の動作変更については、次を参照してください。 [SQL Server 2014 におけるデータベース エンジン機能の重大な変更](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)です。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ID インスタンスを取得した場合、既定では、そのインスタンスを別のコンピューターに反映できません。既定では、Windows セキュリティ インフラストラクチャによりこの操作が制限されます。 ただし、"委任" というメカニズムを使用すると、信頼関係のある複数のコンピューターに Windows ID を反映できるようになります。 TechNet の記事で委任の詳細については、"[Kerberos プロトコル遷移および制約付き委任](http://go.microsoft.com/fwlink/?LinkId=50419)"です。  
  
## <a name="see-also"></a>参照  
 [SqlContext オブジェクト](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  