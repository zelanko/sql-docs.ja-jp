---
title: dm_pdw_sys_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 93e0020fb0da67538b37c171b3252ba029184554
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197022"
---
# <a name="sysdm_pdw_sys_info-transact-sql"></a>dm_pdw_sys_info (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  アプライアンスの全体的なアクティビティを反映するアプライアンスレベルのカウンターのセットを提供します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|現在システム内にあるセッションの数。|0を max_active_sessions (下記参照)。|  
|idle_sessions|**int**|現在アイドル状態のセッションの数。||  
|active_requests|**int**|現在実行中のアクティブな要求の数。||  
|queued_requests|**int**|現在キューに置かれている要求の数。||  
|active_loads|**int**|システムで現在実行されている読み込みの数。||  
|queued_loads|**int**|実行を待機しているキューに置かれた読み込みの数。||  
|active_backups|**int**|現在実行中のバックアップの数。||  
|active_restores|**int**|現在実行中のバックアップ復元の数。||  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
