---
title: "AUTO_SHRINK データベース オプションを OFF に設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f5e28b02301c50d41e15654250f36f0779f6858f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="set-the-autoshrink-database-option-to-off"></a>AUTO_SHRINK データベース オプションを OFF に設定
  このルールでは、AUTO_SHRINK データベース オプションが OFF に設定されているかどうかをチェックします。 データベースの圧縮と拡張により、物理的な断片化が発生することがよくあります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 AUTO_SHRINK データベース オプションを OFF に設定します。 再利用している領域が今後不要になることがわかっている場合は、データベースを手動で圧縮して領域を再利用できます。  
  
## <a name="for-more-information"></a>詳細情報  
 サポート技術情報の資料 [315512](http://go.microsoft.com/fwlink/?linkid=117750)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

