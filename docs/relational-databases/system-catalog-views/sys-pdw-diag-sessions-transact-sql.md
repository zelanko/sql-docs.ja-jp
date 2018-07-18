---
title: sys.pdw_diag_sessions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fa98b2980f226b515c5ae202eea0972326d998bc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37987094"
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システム上に作成されているさまざまな診断のセッションに関する情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar (255)**|診断セッションの名前です。<br /><br /> このビューのキーです。||  
|**xml_data**|**nvarchar (4000)**|XML ペイロードは、セッションを記述します。||  
|**is_active**|**bit**|フラグがアクティブであるかどうかを示すフラグ。||  
|**host_address**|**nvarchar (255)**|セッションの定義 (コントロールのノード) をホストしているコンピューターのアドレス。||  
|**principal_id**|**int**|データベース レベルでセッションを作成したユーザーの ID です。||  
|**database_id**|**int**|診断セッションのスコープとなっているデータベースの ID です。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
