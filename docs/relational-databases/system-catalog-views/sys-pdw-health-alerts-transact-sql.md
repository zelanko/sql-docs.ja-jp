---
title: sys.pdw_health_alerts (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d1aa54191828a71c66c4575451c571621383ae24
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システムで発生する可能性が別のアラートのプロパティを格納します。これは、アラートのカタログ テーブルです。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|アラートの一意の識別子。<br /><br /> このビューのキーです。|NOT NULL|  
|component_id|**int**|このアラートの対象コンポーネントの ID。 コンポーネントは、「電源装置、」などのコンポーネントの一般的な識別子は、され、インストールに固有ではありません。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)です。|NOT NULL|  
|alert_name|**nvarchar (255)**|アラートの名前です。|NOT NULL|  
|state|**nvarchar(32)**|アラートの状態です。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> ' Operational'<br /><br /> 'NonOperational'<br /><br /> 'Degraded'<br /><br /> 'Failed'|  
|severity|**nvarchar(32)**|アラートの重大度。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> ' 情報 '<br /><br /> 「警告」<br /><br /> 'Error'|  
|型|**nvarchar(32)**|アラートの種類。|NOT NULL<br /><br /> 有効値は次のとおりです。<br /><br /> 状況 - デバイスの状態が変更されました。<br /><br /> しきい値の値は、しきい値を超えました。|  
|description|**nvarchar (4000)**|アラートの説明です。|NOT NULL|  
|condition|**nvarchar (255)**|ときに使用される入力のしきい値を = です。 警告のしきい値の計算方法を定義します。|NULL|  
|ステータス|**nvarchar(32)**|アラートの状態|NULL|  
|condition_value|**bit**|システムの操作中に発生するアラートを許可するかどうかを示します。|NULL<br /><br /> 使用可能な値<br /><br /> 0 - アラートは生成されません。<br /><br /> 1-アラートが生成されます。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
