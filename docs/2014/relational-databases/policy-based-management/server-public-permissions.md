---
title: サーバーのパブリック権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7913c4715f47b8105b72b1c817dbe77e52d40539
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066712"
---
# <a name="server-public-permissions"></a>サーバーのパブリック権限
  このルールでは、public サーバー ロールにサーバー権限があるかどうかを調べます。 サーバー上で作成されたログインは、すべて public サーバー ロールのメンバーです。 この条件が満たされる場合、サーバー上のログインにはすべてサーバー権限が付与されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 public サーバー ロールにサーバー権限を付与しないでください。  
  
> [!IMPORTANT]  
>  セットアップが完了する**PUBLIC**と、 `CONNECT` **専用管理者接続**以外のすべてのエンドポイントに対する権限が PUBLIC ロールに付与されます。 これは正常な動作です。通常は変更しないでください (アクセスの制御には、新しいログインの作成時に自動的に付与される `CONNECT SQL` 権限が使用されます)。  
  
### <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../security/securing-sql-server.md)  
  
  
