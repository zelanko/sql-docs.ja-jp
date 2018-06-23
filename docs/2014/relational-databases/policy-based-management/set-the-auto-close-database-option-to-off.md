---
title: AUTO_CLOSE データベース オプションを OFF に設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 88bd1025b928837d68aef3be0b5e4d1fbceb17a2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175134"
---
# <a name="set-the-autoclose-database-option-to-off"></a>AUTO_CLOSE データベース オプションを OFF に設定
  このルールは、AUTO_CLOSE オプションが OFF に設定されているかどうかをチェックします。 AUTO_CLOSE が ON に設定されると、頻繁にアクセスされるデータベースでパフォーマンスが低下する場合があります。これは、接続するたびにデータベースを開いたり閉じたりするオーバーヘッドが増加するためです。 また、AUTO_CLOSE は、接続が終了するたびにプロシージャ キャッシュをフラッシュします。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 頻繁にアクセスされるデータベースでは、AUTO_CLOSE オプションを OFF に設定してください。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
