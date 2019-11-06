---
title: サービス アカウント (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9c0fb67d173ed0f4ade469c5233a7fdff59dd1a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025249"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>[サービス アカウント] (データベース ミラーリング セキュリティ構成ウィザード)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Windows 認証でサーバー インスタンスが別のアカウントを使用している場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービス アカウントを指定します。 これらのサービス アカウントは、すべて (同じドメインまたは信頼関係のあるドメインの) ドメイン アカウントである必要があります。  
  
 すべてのサーバー インスタンスが同じアカウントを使用している場合、または証明書ベースの認証を使用している場合、フィールドは空のままにします。 **[完了]** をクリックするだけで、現在のウィザードのアカウントに基づいてアカウントが自動的に構成されます。  
  
> [!IMPORTANT]  
>  サーバー インスタンスのデータベース ミラーリング エンドポイントで証明書を使用するように構成されている場合は、サービス アカウント フィールドをすべて空にする必要があります。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>オプション  
 **プリンシパル**  
 プリンシパル サーバー インスタンスのサービス アカウントを指定します。 ドメイン名を大文字で入力します。  
  
 *DOMAINNAME*\\*username*  
  
 **ミラー**  
 ミラー サーバー インスタンスのサービス アカウントを指定します。 ドメイン名を大文字で入力します。  
  
 *DOMAINNAME*\\*username*  
  
 **ミラーリング監視サーバー**  
 ミラーリング監視サーバー インスタンスのサービス アカウントを指定します。 ドメイン名を大文字で入力します。  
  
 *DOMAINNAME*\\*username*  
  
## <a name="see-also"></a>参照  
 [データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [データベース ミラーリングまたは Always On 可用性グループのログイン アカウントの設定 &#40;SQL Server&#41;](../../database-engine/database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
