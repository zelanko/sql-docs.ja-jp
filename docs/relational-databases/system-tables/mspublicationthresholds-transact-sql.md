---
title: MSpublicationthresholds (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2025dac432856e944dfd7e12e591907ef05a3565
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831959"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpublicationthresholds**テーブルは、パブリケーションのレプリケーションパフォーマンスメトリックを追跡するために使用され、監視対象のしきい値ごとに1つの行が含まれます。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|しきい値が設定されていないパブリケーションを識別します。|  
|**metric_id**|**int**|[MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md)システムテーブルで定義されている監視対象のレプリケーションパフォーマンスメトリックを識別します。|  
|**value**|**sql_variant**|監視されているメトリックのしきい値。|  
|**shouldalert**|**bit**|値**1**は、メトリックが定義されたしきい値を超えたときにアラートを生成する必要があることを示します。|  
|**isenabled**|**bit**|値**1**は、このレプリケーションパフォーマンスメトリックで監視が有効になっていることを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
