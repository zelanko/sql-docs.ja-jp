---
title: サーバーのパブリック権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 11f478f9cbbdedd246b3b1468572b62b27c86e5b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207914"
---
# <a name="server-public-permissions"></a>サーバーのパブリック権限
  このルールでは、public サーバー ロールにサーバー権限があるかどうかを調べます。 サーバー上で作成されたログインは、すべて public サーバー ロールのメンバーです。 この条件が満たされる場合、サーバー上のログインにはすべてサーバー権限が付与されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 public サーバー ロールにサーバー権限を付与しないでください。  
  
> [!IMPORTANT]  
>  セットアップの完了後、**パブリック**ロールが持つ`CONNECT`以外のすべてのエンドポイントに対する権限、 **Dedicated Admin Connection**します。 これは正常な動作です。通常は変更しないでください (アクセスの制御を使用して、`CONNECT SQL`新しいログインを作成するときに自動的に付与されるアクセス許可)。  
  
### <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../security/securing-sql-server.md)  
  
  
