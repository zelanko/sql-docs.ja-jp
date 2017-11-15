---
title: "信頼可能なビット | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a9aeb335d60738a872cfb6ffde9e1c4de4a4158
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="trustworthy-bit"></a>信頼可能なビット
  このルールでは、sysadmin 固定サーバー ロールにデータベースの dbo ロールが割り当てられているかどうか、およびデータベースの信頼可能なビットがオンに設定されているかどうかを確認します。  
  
 これらの条件が満たされている場合、権限のあるデータベース ユーザーは、特権を sysadmin ロールに昇格させることができます。 このロールでは、ユーザーはシステムを危険にさらす安全ではないアセンブリを作成して実行できます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 信頼可能なビットをオフにするか、dbo データベース ロールから sysadmin 権限を取り消します。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
