---
title: MSpublicationthresholds (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c34a08a1ea9ff903370369c84ce6c827f08f7283
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublicationthresholds**テーブルが監視されている各閾値に対して 1 つの行で、パブリケーションのレプリケーション パフォーマンス基準を追跡するために使用します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|しきい値が設定されていないパブリケーションを識別します。|  
|**metric_id**|**int**|定義されている監視対象のレプリケーション パフォーマンス基準を識別、 [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md)システム テーブル。|  
|**value**|**sql_variant**|監視対象の基準のしきい値です。|  
|**shouldalert**|**bit**|値**1**メトリックは、定義されたしきい値を超えたときに、アラートを生成することを示します。|  
|**isenabled**|**bit**|値**1**このレプリケーション パフォーマンス基準に対する監視が有効になっていることを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
