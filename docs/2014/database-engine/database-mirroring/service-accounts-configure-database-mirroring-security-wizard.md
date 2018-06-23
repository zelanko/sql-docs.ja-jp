---
title: サービス アカウント (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fdca44263bfa60ebf7a2a2a3d66d0c827c3d0868
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176465"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>[サービス アカウント] (データベース ミラーリング セキュリティ構成ウィザード)
  Windows 認証でサーバー インスタンスが別のアカウントを使用している場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービス アカウントを指定します。 これらのサービス アカウントは、すべて (同じドメインまたは信頼関係のあるドメインの) ドメイン アカウントである必要があります。  
  
 すべてのサーバー インスタンスが同じアカウントを使用している場合、または証明書ベースの認証を使用している場合、フィールドは空のままにします。 **[完了]** をクリックするだけで、現在のウィザードのアカウントに基づいてアカウントが自動的に構成されます。  
  
> [!IMPORTANT]  
>  サーバー インスタンスのデータベース ミラーリング エンドポイントで証明書を使用するように構成されている場合は、サービス アカウント フィールドをすべて空にする必要があります。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>および  
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
 [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [ログイン アカウントのデータベース ミラーリングまたは AlwaysOn 可用性グループを設定&#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  