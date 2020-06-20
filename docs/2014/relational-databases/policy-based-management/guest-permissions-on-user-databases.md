---
title: ユーザー データベースに対する guest の権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 344c5fd0639876998f1585c32fac5f7599f664e7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061658"
---
# <a name="guest-permissions-on-user-databases"></a>ユーザー データベースに対する guest の権限
  このルールでは、guest ユーザーがデータベースにアクセスする権限を持っているかどうかを調べます。 このルールはユーザー データベースにのみ適用されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 必要でない場合は、データベースにアクセスする権限を guest ユーザー権限から取り消します。  
  
 guest ユーザーは削除できませんが、master、tempdb、または msdb 以外のデータベースでは、REVOKE CONNECT FROM GUEST を実行して CONNECT 権限を取り消すことにより、guest ユーザーを無効にできます。  
  
## <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../security/securing-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
