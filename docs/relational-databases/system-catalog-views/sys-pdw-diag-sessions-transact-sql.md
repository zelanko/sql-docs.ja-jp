---
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
ms.openlocfilehash: fa06005679e31381f723b30b9f68e5ce0d89ae1e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127687"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>pdw_diag_sessions (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システムで作成されたさまざまな診断セッションに関する情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|診断セッションの名前。<br /><br /> このビューのキー。||  
|**xml_data**|**nvarchar (4000)**|セッションを説明する XML ペイロード。||  
|**is_active**|**bit**|フラグがアクティブかどうかを示すフラグです。||  
|**host_address**|**nvarchar(255)**|セッション定義 (コントロールノード) をホストしているコンピューターのアドレス。||  
|**principal_id**|**int**|データベースレベルでセッションを作成したユーザーの ID。||  
|**database_id**|**int**|診断セッションのスコープであるデータベースの ID。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
