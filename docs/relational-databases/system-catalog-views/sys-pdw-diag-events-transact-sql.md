---
description: sys.pdw_diag_events (Transact-sql)
title: sys.pdw_diag_events (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 59bb3e9c-2829-49a0-b382-652ed1f54f88
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 68cdc1013969dde85bbdc0bded31610a1673b91d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461613"
---
# <a name="syspdw_diag_events-transact-sql"></a>sys.pdw_diag_events (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  システム上の診断セッションに含めることができるイベントに関する情報を保持します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar (255)**|特定の診断イベントの名前。||  
|**source**|**nvarchar (255)**|イベントのソース (エンジン、全般、dms など)||  
|**is_enabled**|**bit**|イベントが発行されているかどうか。||  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics と Parallel Data Warehouse のカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
