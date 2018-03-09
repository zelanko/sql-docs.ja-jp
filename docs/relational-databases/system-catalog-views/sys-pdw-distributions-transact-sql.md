---
title: "sys.pdw_distributions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07694ebc741c769e97991e81de40fe73023106a0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  アプライアンス上の分布に関する情報を保持します。 これには、配布のアプライアンスごとに 1 行が一覧表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|分布に関連付けられている一意の数値 id です。<br /><br /> このビューのキーです。|1 つのコンピューティング ノードのディストリビューションの数を乗算してアプライアンスにコンピューティング ノードの数に 1 です。|  
|pdw_node_id|**int**|この配布にノードの ID です。|Pdw_node_id を参照してください[sys.dm_pdw_nodes &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)。|  
|name|**nvarchar(32)**|分散テーブルでのサフィックスとして使用される、そのディストリビューションに関連付けられた識別子の文字列を指定します。|文字列の構成の ' A ～ Z'、' a ～ z'、' 0-9'、'_'、'-' です。|  
|position|**int**|そのノード上には、その他の分布をそれぞれのノード内の配布の位置です。|1 つのノードのディストリビューションの数に 1 です。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
