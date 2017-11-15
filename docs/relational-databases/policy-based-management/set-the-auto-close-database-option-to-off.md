---
title: "AUTO_CLOSE データベース オプションを OFF に設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5ff479c4c08237044cdb5af57bd29a58deb54d06
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-autoclose-database-option-to-off"></a>AUTO_CLOSE データベース オプションを OFF に設定
  このルールは、AUTO_CLOSE オプションが OFF に設定されているかどうかをチェックします。 AUTO_CLOSE が ON に設定されると、頻繁にアクセスされるデータベースでパフォーマンスが低下する場合があります。これは、接続するたびにデータベースを開いたり閉じたりするオーバーヘッドが増加するためです。 また、AUTO_CLOSE は、接続が終了するたびにプロシージャ キャッシュをフラッシュします。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 頻繁にアクセスされるデータベースでは、AUTO_CLOSE オプションを OFF に設定してください。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
