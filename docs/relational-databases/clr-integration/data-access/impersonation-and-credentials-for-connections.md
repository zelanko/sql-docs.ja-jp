---
title: "権限借用と接続の資格情報 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3c4495b75f9464eb0e8211eeea6529264053c61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="impersonation-and-credentials-for-connections"></a>接続の権限借用と資格情報
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 認証を使用して、共通言語ランタイム (CLR) 統合は複雑では SQL Server 認証を使用するよりも安全です。 Windows 認証を使用する場合には、次の点を考慮してください。  
  
 Windows に接続する SQL Server プロセスは、SQL Server Windows サービス アカウントのセキュリティ コンテキストを既定で取得します。 ただし、CLR 関数をプロキシ ID にマッピングすることにより、その発信接続に対し、Windows サービス アカウントとは異なるセキュリティ コンテキストを設定することができます。  
  
 場合によってを使用して、呼び出し元を偽装する可能性があります、 **SqlContext.WindowsIdentity**サービス アカウントとして実行するのではなくプロパティです。 **WindowsIdentity**インスタンスは、呼び出し元のコードを呼び出すし、クライアントが Windows 認証を使用する場合にのみ使用するクライアントの id を表します。 取得した後、 **WindowsIdentity**呼び出すことができますのインスタンス、 **Impersonate**スレッドのセキュリティ トークンを変更し、クライアントの代わりに ADO.NET 接続を開きます。  
  
 SQLContext.WindowsIdentity.Impersonate を呼び出した後は、ローカル データにアクセスすることはできませんし、システム データにアクセスすることはできません。 もう一度、データにアクセスするには、WindowsImpersonationContext.Undo を呼び出す必要があります。  
  
 次の例を使用して、呼び出し元を偽装する方法を示しています、 **SqlContext.WindowsIdentity**プロパティです。  
  
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
>  権限借用の動作変更については、次を参照してください。 [SQL Server 2016 におけるデータベース エンジン機能の重大な変更](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)です。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ID インスタンスを取得した場合、既定では、そのインスタンスを別のコンピューターに反映できません。既定では、Windows セキュリティ インフラストラクチャによりこの操作が制限されます。 ただし、"委任" というメカニズムを使用すると、信頼関係のある複数のコンピューターに Windows ID を反映できるようになります。 TechNet の記事で委任の詳細については、"[Kerberos プロトコル遷移および制約付き委任](http://go.microsoft.com/fwlink/?LinkId=50419)"です。  
  
## <a name="see-also"></a>参照  
 [SqlContext オブジェクト](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
