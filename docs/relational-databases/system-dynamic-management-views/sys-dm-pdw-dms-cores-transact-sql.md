---
title: dm_pdw_dms_cores (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 76a154639a71b22bfe3f119233f3abbcd329f7c3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899525"
---
# <a name="sysdm_pdw_dms_cores-transact-sql"></a>dm_pdw_dms_cores (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  アプライアンスの計算ノードで実行されているすべての DMS サービスに関する情報を保持します。 これには、サービスインスタンスごとに1行が表示されます。これは現在、ノードごとに1行です。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|この DMS コアに関連付けられている一意の数値 id。<br /><br /> このビューのキー。|この DMS コアが実行されているノードの pdw_node_id に設定します。|  
|pdw_node_id|**int**|この DMS サービスが実行されているノードの ID。|『 [Transact-sql&#41;&#40;dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|status|**nvarchar(32)**|DMS サービスの現在の状態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 このビューで保持される最大行数の詳細については、「[容量制限](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)」トピックの「メタデータ」セクションを参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
