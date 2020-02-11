---
title: MSmerge_genhistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf9c38fe71c1282b19b947fc1771714dd138c45a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017702"
---
# <a name="msmerge_genhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_genhistory**テーブルには、サブスクライバーが認識する (保有期間内の) 世代ごとに1行の情報が格納されます。 これは、交換中に共通の世代が送信されないようにし、バックアップから復元されたサブスクライバーを再同期するために使用されます。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**UNIQUEIDENTIFIER**|サブスクライバーの generation 値によって識別される変更のグローバル識別子です。|  
|**pubid**|**UNIQUEIDENTIFIER**|パブリケーション識別子です。|  
|**generation**|**bigint**|生成値。|  
|**art_nick**|**int**|記事のニックネーム。|  
|**ニックネーム**|**varbinary (1001)**|この generation 値を持っていることが既に認識されている他のサブスクライバーのニックネームの一覧です。 その変更を既に認識しているサブスクライバーに、generation 値を送信することを防ぐために使用します。 ニックネームの一覧のニックネームは、検索の効率を高めるために並べ替えられた順序で保持されます。 このフィールドに格納できる数よりも多くのニックネームがある場合、この最適化によるメリットは得られません。|  
|**coldate**|**DATETIME**|現在の generation 値がテーブルに追加された日付です。|  
|**genstatus**|**tinyint**|世代の状態を次に示します。<br /><br /> **0** = 開く。<br /><br /> **1** = Closed。<br /><br /> **2** = 閉じられ、別のサブスクライバーで発生しました。|  
|**changecount**|**int**|特定のジェネレーションに反映された変更の数|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
