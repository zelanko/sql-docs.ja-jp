---
title: sys.dm_pdw_hadoop_operations (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 11c8cc0797bafff6cc8c38bffb55023be00003a9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023964"
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>sys.dm_pdw_hadoop_operations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  1 行の各 map-reduce のジョブ実行の一部として Hadoop に適用されているデータを含む、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 外部の Hadoop テーブルに対するクエリ。 各 map-reduce ジョブでは、クエリで述語の 1 つを表します。 これは、Hadoop の外部テーブルに対するクエリの述語のプッシュ ダウンが有効になっているときにのみ使用されます。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この外部の Hadoop 操作の ID。|ID と同じ[sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|step_index|**int**|この Hadoop 操作に関係するクエリの手順のインデックスです。|Step_index と同じ[sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)します。|  
|operation_type|**nvarchar (255)**|外部の操作の種類について説明します。|' 外部 Hadoop Operation'|  
|operation_name|**nvarchar (4000)**|Map-reduce のジョブのジョブ ID。 これは、後に Hadoop によって返される [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ジョブを送信します。||  
|map_progress|**float**|これまで、マップのジョブで消費された入力のデータの割合。|浮動小数点数の間、および 0 ～ 100 です。|  
|reduce_progress|**int**|Reduce ジョブが完了したことの割合。|浮動小数点数の間、および 0 ～ 100 です。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
