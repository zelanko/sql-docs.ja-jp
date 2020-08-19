---
description: pdw_diag_sessions (Transact-sql)
title: pdw_diag_sessions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4615bce79c1a748a76a9af02d1991585e4550e12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420026"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>pdw_diag_sessions (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  システムで作成されたさまざまな診断セッションに関する情報を保持します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar (255)**|診断セッションの名前。<br /><br /> このビューのキー。||  
|**xml_data**|**nvarchar (4000)**|セッションを説明する XML ペイロード。||  
|**is_active**|**bit**|フラグがアクティブかどうかを示すフラグです。||  
|**host_address**|**nvarchar (255)**|セッション定義 (コントロールノード) をホストしているコンピューターのアドレス。||  
|**principal_id**|**int**|データベースレベルでセッションを作成したユーザーの ID。||  
|**database_id**|**int**|診断セッションのスコープであるデータベースの ID。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
