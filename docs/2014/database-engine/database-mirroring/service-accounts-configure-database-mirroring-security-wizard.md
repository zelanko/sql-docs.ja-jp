---
title: サービス アカウント (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69877c6a20e37e012925185d0b807e9579066e35
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754394"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>[サービス アカウント] (データベース ミラーリング セキュリティ構成ウィザード)
  Windows 認証でサーバー インスタンスが別のアカウントを使用している場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービス アカウントを指定します。 これらのサービス アカウントは、すべて (同じドメインまたは信頼関係のあるドメインの) ドメイン アカウントである必要があります。  
  
 すべてのサーバー インスタンスが同じアカウントを使用している場合、または証明書ベースの認証を使用している場合、フィールドは空のままにします。 **[完了]** をクリックするだけで、現在のウィザードのアカウントに基づいてアカウントが自動的に構成されます。  
  
> [!IMPORTANT]  
>  サーバー インスタンスのデータベース ミラーリング エンドポイントで証明書を使用するように構成されている場合は、サービス アカウント フィールドをすべて空にする必要があります。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>オプション  
 **第一**  
 プリンシパル サーバー インスタンスのサービス アカウントを指定します。 ドメイン名を大文字で入力します。  
  
 *DOMAINNAME*\\*username*  
  
 **ミラー**  
 ミラー サーバー インスタンスのサービス アカウントを指定します。 ドメイン名を大文字で入力します。  
  
 *DOMAINNAME*\\*username*  
  
 **ミラーリング監視サーバー**  
 ミラーリング監視サーバー インスタンスのサービス アカウントを指定します。 ドメイン名を大文字で入力します。  
  
 *DOMAINNAME*\\*username*  
  
## <a name="see-also"></a>参照  
 [[データベースのプロパティ] &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [&#40;SQL Server Management Studio を開始データベースミラーリングモニター&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [データベースミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [データベースミラーリングまたは AlwaysOn 可用性グループ &#40;SQL Server のログインアカウントを設定&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
