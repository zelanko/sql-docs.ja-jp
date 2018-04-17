---
title: sys.dm_pdw_nodes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 267eac5c7f4aa7d73827f377002f4383374d853f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  すべてのノードの情報を保持して[!INCLUDE[ssAPS](../../includes/ssaps-md.md)]です。 アプライアンス内のノードごとに 1 行が一覧表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id です。<br /><br /> このビューのキーです。|種類に関係なく、アプライアンスの間で一意です。|  
|型|**nvarchar(32)**|ノードの型。|' COMPUTE'、'コントロール'、'管理'|  
|name|**nvarchar(32)**|ノードの論理名です。|適切な長さの任意の文字列。|  
|address|**nvarchar(32)**|このノードの IP アドレス。|0 ～ 255 の形式。0 ～ 255 です。0 ～ 255 です。0 ～ 255 です。|  
|is_passive|**int**|Node を実行する仮想マシンが割り当てられているサーバーで実行されているかは予備のサーバーにフェールオーバーするかどうかを示します。|0 ～ ノード VM は、元のサーバーで実行されているとします。<br /><br /> 1 – ノードの VM は、予備のサーバーで実行されています。|  
|領域 (region)|**nvarchar(32)**|ノードが実行されている地域です。|' PDW'、'HDINSIGHT'|  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
