---
title: ユーザー データベースに対する guest の権限 | Microsoft Docs
description: guest ユーザーが SQL Server のユーザー データベースにアクセスする権限を持っているかどうかを調べます。 必要でない場合は、guest ユーザーの権限を取り消します。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b6a911c84574c0b064c1c71bf9ff68aa725fc9c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749377"
---
# <a name="guest-permissions-on-user-databases"></a>ユーザー データベースに対する guest の権限
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このルールでは、guest ユーザーがデータベースにアクセスする権限を持っているかどうかを調べます。 このルールはユーザー データベースにのみ適用されます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 必要でない場合は、データベースにアクセスする権限を guest ユーザー権限から取り消します。  
  
 guest ユーザーは削除できませんが、master、tempdb、または msdb 以外のデータベースでは、REVOKE CONNECT FROM GUEST を実行して CONNECT 権限を取り消すことにより、guest ユーザーを無効にできます。  
  
## <a name="for-more-information"></a>詳細情報  
 [SQL Server の保護](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
