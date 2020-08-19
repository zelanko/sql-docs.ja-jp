---
description: log_shipping_primary_secondaries (Transact-sql)
title: log_shipping_primary_secondaries (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_primary_secondaries_TSQL
- log_shipping_primary_secondaries
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_primary_secondaries system table
ms.assetid: 4b315c70-7265-4acd-b35b-a4dbb7881d98
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e731cf42d7ad0228d5746a315ffd70aa5862db85
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469076"
---
# <a name="log_shipping_primary_secondaries-transact-sql"></a>log_shipping_primary_secondaries (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  各プライマリデータベースをセカンダリデータベースにマップします。 このテーブルは、 **msdb** データベースに格納されます。  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**primary_id**|**uniqueidentifier**|ログ配布構成のプライマリデータベースの ID。|  
|**secondary_server**|**sysname**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ログ配布構成におけるのセカンダリインスタンスの名前です。|  
|**secondary_database**|**sysname**|ログ配布構成のセカンダリデータベースの名前。|  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_secondary &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql.md)   
 [sp_delete_log_shipping_primary_secondary &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql.md)   
 [sp_help_log_shipping_primary_secondary &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql.md)   
 [システム テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
