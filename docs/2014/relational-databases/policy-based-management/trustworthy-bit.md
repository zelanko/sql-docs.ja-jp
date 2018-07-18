---
title: 信頼可能なビット | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 186a90bd7fa5884dea1887b6273338e16f76081e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279086"
---
# <a name="trustworthy-bit"></a>信頼可能なビット
  このルールでは、sysadmin 固定サーバー ロールにデータベースの dbo ロールが割り当てられているかどうか、およびデータベースの信頼可能なビットがオンに設定されているかどうかを確認します。  
  
 これらの条件が満たされている場合、権限のあるデータベース ユーザーは、特権を sysadmin ロールに昇格させることができます。 このロールでは、ユーザーはシステムを危険にさらす安全ではないアセンブリを作成して実行できます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 信頼可能なビットをオフにするか、dbo データベース ロールから sysadmin 権限を取り消します。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
