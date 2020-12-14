---
description: sys.pdw_diag_sessions (Transact-sql)
title: sys.pdw_diag_sessions (Transact-sql) |Microsoft Docs
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
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 3418e974be1c5b52b3fe4bcdcca8fa6dd4bfcc57
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97404568"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-sql)
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
 [Azure Synapse Analytics と Parallel Data Warehouse のカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
