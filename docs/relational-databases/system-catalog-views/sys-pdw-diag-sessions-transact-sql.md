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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68127687"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>pdw_diag_sessions (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システムで作成されたさまざまな診断セッションに関する情報を保持します。  
  
|列名|データ型|[説明]|Range|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|診断セッションの名前。<br /><br /> このビューのキー。||  
|**xml_data**|**nvarchar(4000)**|セッションを説明する XML ペイロード。||  
|**is_active**|**bit**|フラグがアクティブかどうかを示すフラグです。||  
|**host_address**|**nvarchar(255)**|セッション定義 (コントロールノード) をホストしているコンピューターのアドレス。||  
|**principal_id**|**int**|データベースレベルでセッションを作成したユーザーの ID。||  
|**database_id**|**int**|診断セッションのスコープであるデータベースの ID。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスのカタログビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
