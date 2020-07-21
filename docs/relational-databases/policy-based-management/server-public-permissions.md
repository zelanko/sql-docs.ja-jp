---
title: サーバーのパブリック権限 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ffdcfcecf88bfaa12a9d1defee2fc40ef3900c0b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774212"
---
# <a name="server-public-permissions"></a>サーバーのパブリック権限
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このルールでは、public サーバー ロールにサーバー権限があるかどうかを調べます。 サーバー上で作成されたログインは、すべて public サーバー ロールのメンバーです。 この条件が満たされる場合、サーバー上のログインにはすべてサーバー権限が付与されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 public サーバー ロールにサーバー権限を付与しないでください。  
  
> [!IMPORTANT]  
>  セットアップの完了後、 **PUBLIC** ロールには、 **専用管理者接続** 以外のすべてのエンドポイントに対する **CONNECT**権限が付与されます。 これは正常な動作です。通常は変更しないでください (アクセスの制御には、新しいログインの作成時に自動的に付与される **CONNECT SQL** 権限が使用されます)。  
  
### <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)  
  
  
