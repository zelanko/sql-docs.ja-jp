---
title: ミラーリング監視サーバーを含める (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 166d9d3b1c5f685564bdca16f154413459901cd0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68212614"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>[ミラーリング監視サーバーを含める] (データベース ミラーリング セキュリティ構成ウィザード)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このページを使用すると、データベース ミラーリング用に、このセキュリティ構成にミラーリング監視サーバーを含めるかどうかを指定できます。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>オプション  
 **はい**  
 ミラーリング監視サーバー インスタンスをセキュリティ構成に含めるには、これをクリックします。 ミラーリング監視サーバーは、自動フェールオーバーを伴う高い安全性モード (プリンシパル サーバー インスタンスで障害が発生した場合に、ミラー サーバー インスタンスへ自動的に処理をフェールオーバーするモード) に必要です。  
  
 **いいえ**  
 ミラーリング監視サーバーを使用せずにセキュリティを構成するには、これをクリックします。  
  
## <a name="see-also"></a>参照  
 [データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [データベース ミラーリング監視サーバー](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  
