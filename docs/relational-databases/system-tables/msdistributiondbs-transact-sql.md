---
title: Ms、Db (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistributiondbs_TSQL
- MSdistributiondbs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistributiondbs system table
ms.assetid: d7ffa9df-bf1d-41b8-837e-b762c17c2764
author: stevestein
ms.author: sstein
ms.openlocfilehash: 966a77ae53576488ca14c16b4464ebce2816eb02
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907342"
---
# <a name="msdistributiondbs-transact-sql"></a>Ms、Db (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Msディストリビューション db**テーブルには、ローカルディストリビューターで定義されているディストリビューションデータベースごとに1行のデータが格納されます。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|ディストリビューションデータベースの名前。|  
|**min_distretention**|**int**|トランザクションが削除されるまでの最小保有期間 (時間単位)。|  
|**max_distretention**|**int**|トランザクションが削除されるまでの最大保有期間 (時間単位)。|  
|**history_retention**|**int**|履歴を保持する期間 (時間単位)。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
