---
title: sys.pdw_health_alerts (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 41ae6d70399dea79a92cbc4fd77ba6e08f660d7c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025453"
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システムで発生するさまざまなアラートのプロパティを格納します。これは、アラートのカタログ テーブルです。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|アラートの一意の識別子。<br /><br /> このビューのキーです。|NOT NULL|  
|component_id|**int**|このアラートの対象のコンポーネントの ID。 コンポーネント「電源装置、」などのコンポーネントの一般的な識別子であり、インストールに固有ではありません。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)します。|NOT NULL|  
|alert_name|**nvarchar (255)**|アラートの名前。|NOT NULL|  
|state|**nvarchar(32)**|アラートの状態。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> ' Operational'<br /><br /> 'NonOperational'<br /><br /> 'Degraded'<br /><br /> 'Failed'|  
|severity|**nvarchar(32)**|アラートの重大度。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> [情報]<br /><br /> 「警告」<br /><br /> 'Error'|  
|type|**nvarchar(32)**|アラートの種類。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> StatusChange - デバイスの状態が変更されました。<br /><br /> しきい値の値は、しきい値を超えました。|  
|description|**nvarchar (4000)**|アラートの説明。|NOT NULL|  
|condition|**nvarchar (255)**|入力の場合に使用のしきい値を = です。 警告のしきい値の計算方法を定義します。|NULL|  
|status|**nvarchar(32)**|アラートの状態|NULL|  
|condition_value|**bit**|システムの操作中に発生するアラートが許可されているかどうかを示します。|NULL<br /><br /> 使用可能な値<br /><br /> 0 - アラートは生成されません。<br /><br /> 1-アラートが生成されます。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
