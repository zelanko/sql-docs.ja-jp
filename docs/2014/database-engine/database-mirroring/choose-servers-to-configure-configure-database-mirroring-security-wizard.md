---
title: 構成するサーバーを選択する (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 635c8f6bda7c21b915e2b50228eba5255ed001ba
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934403"
---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a>[構成するサーバーを選択する] (データベース ミラーリング セキュリティ構成ウィザード)
  このページを使用すると、構成するサーバー インスタンスを指定できます。 ウィザードを進めるには、少なくとも 1 つのサーバー インスタンスを選択する必要があります。  
  
 サーバー インスタンスのチェック ボックスをオフにすると、このウィザードでは、そのサーバーを変更できなくなります。 ただし、他のサーバー インスタンスの構成の一部としてこのインスタンスの情報を入力し、保存するように求められます。 たとえば、ミラーリング監視サーバー インスタンスのチェック ボックスをオフにした場合でも、ミラーリング監視サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントを入力するように求められます。これは、プリンシパル サーバー インスタンスおよびミラー サーバー インスタンスに保存するセキュリティ構成の中で、このアカウントのログインを作成する必要があるためです。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **[プリンシパル サーバー インスタンス]**  
 プリンシパル サーバーのセキュリティを構成する場合に選択します。  
  
 **[ミラー サーバー インスタンス]**  
 ミラー サーバーのセキュリティを構成する場合に選択します。  
  
 **[ミラーリング監視サーバー インスタンス]**  
 ミラーリング監視サーバー (存在する場合) のセキュリティを構成する場合に選択します。  
  
## <a name="see-also"></a>参照  
 [データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
