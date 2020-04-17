---
title: 接続の偽装と資格情報 |マイクロソフトドキュメント
description: SQL Server CLR 統合では、呼び出し元を偽装する場合は、プロパティを使用して Windows 認証します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 382185c036055bb9ea689f551c256a26ee83b0b4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485327"
---
# <a name="impersonation-and-credentials-for-connections"></a>接続の権限借用と資格情報
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR (共通言語ランタイム) 統合では、複雑な Windows 認証を使用する方が、SQL Server 認証を使用するよりもセキュリティが向上します。 Windows 認証を使用する場合には、次の点を考慮してください。  
  
 Windows に接続する SQL Server プロセスは、SQL Server Windows サービス アカウントのセキュリティ コンテキストを既定で取得します。 ただし、CLR 関数をプロキシ ID にマッピングすることにより、その発信接続に対し、Windows サービス アカウントとは異なるセキュリティ コンテキストを設定することができます。  
  
 場合によっては、サービス アカウントとして実行する代わりに **、SqlContext.WindowsIdentity**プロパティを使用して呼び出し元を偽装する必要があります。 **WindowsIdentity**インスタンスは、呼び出し元のコードを呼び出したクライアントの ID を表し、クライアントが Windows 認証を使用した場合にのみ使用できます。 **WindowsIdentity**インスタンスを取得した後、スレッドのセキュリティ トークンを変更する**Impersonate**を呼び出し、クライアントの代理でADO.NET接続を開くことができます。  
  
 呼び出すと、ローカル データにアクセスできず、システム データにアクセスできなくなります。 データに再びアクセスするには、呼び出す必要があります。  
  
 次の例は、**呼**び出し元を偽装する方法を示しています。  
  
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
>  偽装の動作の変更については、「 [SQL Server 2016 のデータベース エンジン機能の変更点を取り上](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)める 」を参照してください。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ID インスタンスを取得した場合、既定では、そのインスタンスを別のコンピューターに反映できません。既定では、Windows セキュリティ インフラストラクチャによりこの操作が制限されます。 ただし、"委任" というメカニズムを使用すると、信頼関係のある複数のコンピューターに Windows ID を反映できるようになります。 委任の詳細については、TechNet の記事[「Kerberos プロトコルの移行と制約付き委任」を参照してください](https://go.microsoft.com/fwlink/?LinkId=50419)。  
  
## <a name="see-also"></a>参照  
 [SqlContext オブジェクト](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
