---
title: 信頼可能なビット | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c887b1e8f2243e89d9390bbdd043a5d2483856b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="trustworthy-bit"></a>信頼可能なビット
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、sysadmin 固定サーバー ロールにデータベースの dbo ロールが割り当てられているかどうか、およびデータベースの信頼可能なビットがオンに設定されているかどうかを確認します。  
  
 これらの条件が満たされている場合、権限のあるデータベース ユーザーは、特権を sysadmin ロールに昇格させることができます。 このロールでは、ユーザーはシステムを危険にさらす安全ではないアセンブリを作成して実行できます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 信頼可能なビットをオフにするか、dbo データベース ロールから sysadmin 権限を取り消します。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
