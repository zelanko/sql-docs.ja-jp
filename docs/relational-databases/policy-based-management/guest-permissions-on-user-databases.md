---
title: "ユーザー データベースに対する guest の権限 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd16791702b01180158b894145f69211017281ad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="guest-permissions-on-user-databases"></a>ユーザー データベースに対する guest の権限
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、guest ユーザーがデータベースにアクセスする権限を持っているかどうかを調べます。 このルールはユーザー データベースにのみ適用されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 必要でない場合は、データベースにアクセスする権限を guest ユーザー権限から取り消します。  
  
 guest ユーザーは削除できませんが、master、tempdb、または msdb 以外のデータベースでは、REVOKE CONNECT FROM GUEST を実行して CONNECT 権限を取り消すことにより、guest ユーザーを無効にできます。  
  
## <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
