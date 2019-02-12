---
title: sys.pdw_diag_events (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 59bb3e9c-2829-49a0-b382-652ed1f54f88
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e5cccb7bff26f662cf5a087cedfbb7d53f9c1cad
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56038303"
---
# <a name="syspdwdiagevents-transact-sql"></a>sys.pdw_diag_events (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  システム上の診断のセッションで含めることのできるイベントについての情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar (255)**|固有の診断イベントの名前です。||  
|**source**|**nvarchar (255)**|(エンジン、全般、dms など) は、イベントのソース||  
|**is_enabled**|**bit**|かどうかは、イベントが公開されています。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
