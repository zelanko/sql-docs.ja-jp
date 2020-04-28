---
title: pdw_health_alerts (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c47bcc342bf8a052aed93649ca0ad8475d937608
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127537"
---
# <a name="syspdw_health_alerts-transact-sql"></a>pdw_health_alerts (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システムで発生する可能性があるさまざまなアラートのプロパティを格納します。これは、アラートのカタログテーブルです。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|警告の一意識別子。<br /><br /> このビューのキー。|NOT NULL|  
|component_id|**int**|このアラートが適用されるコンポーネントの ID。 コンポーネントは、"パワーサプライ" などの一般的なコンポーネント識別子であり、インストールに固有のものではありません。 「 [Sys. pdw_health_components &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。|NOT NULL|  
|alert_name|**nvarchar(255)**|アラートの名前。|NOT NULL|  
|state|**nvarchar(32)**|アラートの状態。|NOT NULL<br /><br /> 指定できる値<br /><br /> 操作<br /><br /> 'NonOperational'<br /><br /> Degraded<br /><br /> 障害|  
|severity|**nvarchar(32)**|アラートの重大度。|NOT NULL<br /><br /> 指定できる値<br /><br /> 専用<br /><br /> 要する<br /><br /> エラー|  
|type|**nvarchar(32)**|アラートの種類。|NOT NULL<br /><br /> 指定できる値<br /><br /> StatusChange-デバイスの状態が変更されました。<br /><br /> しきい値-値がしきい値を超えました。|  
|description|**nvarchar (4000)**|アラートの説明。|NOT NULL|  
|condition|**nvarchar(255)**|Type = Threshold の場合に使用します。 アラートのしきい値の計算方法を定義します。|NULL|  
|status|**nvarchar(32)**|Alert status|NULL|  
|condition_value|**bit**|システム操作中に警告を発生させることができるかどうかを示します。|NULL<br /><br /> 設定可能な値<br /><br /> 0-アラートは生成されません。<br /><br /> 1-アラートが生成されます。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
