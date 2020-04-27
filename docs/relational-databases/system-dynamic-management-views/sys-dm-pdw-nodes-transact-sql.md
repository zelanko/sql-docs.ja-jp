---
title: dm_pdw_nodes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 61593522e09ed86ec10f08a6ad8ff7a941a2e10e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899345"
---
# <a name="sysdm_pdw_nodes-transact-sql"></a>dm_pdw_nodes (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  のすべてのノードに関する情報を[!INCLUDE[ssAPS](../../includes/ssaps-md.md)]保持します。 アプライアンス内のノードごとに1行が一覧表示されます。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id。<br /><br /> このビューのキー。|種類に関係なく、アプライアンス全体で一意です。|  
|型|**nvarchar(32)**|ノードの種類。|' COMPUTE '、' CONTROL '、' MANAGEMENT '|  
|name|**nvarchar(32)**|ノードの論理名。|適切な長さの任意の文字列。|  
|address|**nvarchar(32)**|このノードの IP アドレス。|[0-255] の形式で指定します。[0-255]。[0-255]。[0-255]。|  
|is_passive|**int**|ノードを実行している仮想マシンが、割り当てられたサーバー上で実行されているか、またはスペアサーバーにフェールオーバーしたかどうかを示します。|0-ノード VM は元のサーバーで実行されています。<br /><br /> 1-ノード VM は、スペアサーバーで実行されています。|  
|region|**nvarchar(32)**|ノードが実行されているリージョン。|' PDW '、' HDINSIGHT '|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
