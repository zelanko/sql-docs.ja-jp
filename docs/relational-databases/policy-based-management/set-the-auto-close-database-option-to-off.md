---
title: AUTO_CLOSE データベース オプションを OFF に設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bc10818d1c868036be461a92eb57e24b476066df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806123"
---
# <a name="set-the-autoclose-database-option-to-off"></a>AUTO_CLOSE データベース オプションを OFF に設定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールは、AUTO_CLOSE オプションが OFF に設定されているかどうかをチェックします。 AUTO_CLOSE が ON に設定されると、頻繁にアクセスされるデータベースでパフォーマンスが低下する場合があります。これは、接続するたびにデータベースを開いたり閉じたりするオーバーヘッドが増加するためです。 また、AUTO_CLOSE は、接続が終了するたびにプロシージャ キャッシュをフラッシュします。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 頻繁にアクセスされるデータベースでは、AUTO_CLOSE オプションを OFF に設定してください。  
  
## <a name="for-more-information"></a>詳細情報  
 [ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
