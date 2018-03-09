---
title: "MSmerge_genhistory (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0408dd3ecc87598117466c03d7b474c23f1ce514
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_genhistory** (、保有期間内で) サブスクライバーを知っている generation 値ごとに 1 つの行がテーブルに含まれています。 これは、変換中に共通する generation 値を送信することを防ぎ、バックアップから復元するサブスクライバーを再同期するために使用されます。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|サブスクライバーの generation 値によって識別される変更のグローバル識別子です。|  
|**pubid**|**uniqueidentifier**|パブリケーション識別子です。|  
|**生成**|**bigint**|generation 値です。|  
|**art_nick**|**int**|アーティクルのニックネームです。|  
|**ニックネーム**|**varbinary(1001)**|この generation 値を持っていることが既に認識されている他のサブスクライバーのニックネームの一覧です。 その変更を既に認識しているサブスクライバーに、generation 値を送信することを防ぐために使用します。 ニックネーム一覧内のニックネームは、検索をより効率化するために並べ替えて管理されます。 このフィールドの範囲を超えるニックネームがある場合、この最適化による恩恵を受けることはありません。|  
|**coldate**|**datetime**|現在の generation 値がテーブルに追加された日付です。|  
|**genstatus**|**tinyint**|generation の状態です。次のいずれかの値をとります。<br /><br /> **0**開くを = です。<br /><br /> **1** = 終了します。<br /><br /> **2** = クローズし、別のサブスクライバーで発生しました。|  
|**changecount**|**int**|指定の generation に反映された変更の数です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
