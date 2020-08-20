---
description: MSreplication_options (Transact-sql)
title: MSreplication_options (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_options
- MSreplication_options_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_options system table
ms.assetid: 23cf10d7-8bc1-4368-b5eb-e5576421e776
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 44099921a382ca05f0e2e379b2df9d97e1c28f6e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460345"
---
# <a name="msreplication_options-transact-sql"></a>MSreplication_options (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSreplication_options**テーブルには、レプリケーションによって内部的に使用されるメタデータが格納されます。 このテーブルは、 **master** データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|内部使用のみです。|  
|**value**|**bit**|内部使用のみです。|  
|**major_version**|**int**|内部使用のみです。|  
|**minor_version**|**int**|内部使用のみです。|  
|**revision**|**int**|内部使用のみです。|  
|**install_failures**|**int**|内部使用のみです。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
