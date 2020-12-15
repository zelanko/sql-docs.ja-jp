---
description: sys.dm_pdw_dms_cores (Transact-sql)
title: sys.dm_pdw_dms_cores (Transact-sql) |Microsoft Docs
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 81a59915c6376e45ebcb0203593ea9725ac6a440
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482623"
---
# <a name="sysdm_pdw_dms_cores-transact-sql"></a>sys.dm_pdw_dms_cores (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  アプライアンスの計算ノードで実行されているすべての DMS サービスに関する情報を保持します。 これには、サービスインスタンスごとに1行が表示されます。これは現在、ノードごとに1行です。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|この DMS コアに関連付けられている一意の数値 id。<br /><br /> このビューのキー。|この DMS コアが実行されているノードの pdw_node_id に設定します。|  
|pdw_node_id|**int**|この DMS サービスが実行されているノードの ID。|[Transact-sql&#41;&#40;sys.dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|status|**nvarchar(32)**|DMS サービスの現在の状態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 このビューで保持される最大行数の詳細については、「 [容量制限](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) 」トピックの「メタデータ」セクションを参照してください。  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics と並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
