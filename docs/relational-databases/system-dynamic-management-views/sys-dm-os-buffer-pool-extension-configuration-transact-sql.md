---
title: "sys.dm_os_buffer_pool_extension_configuration (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_buffer_pool_extension_configuration
- sys.dm_os_buffer_pool_extension_configuration_TSQL
- dm_os_buffer_pool_extension_configuration_TSQL
- sys.dm_os_buffer_pool_extension_configuration
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_buffer_pool_extension_configuration dynamic management view
ms.assetid: d52cc481-4d29-4f33-b63d-231ec35d092f
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d0f473b0e871f0df6ce84830e42caaf29bd21c3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosbufferpoolextensionconfiguration-transact-sql"></a>sys.dm_os_buffer_pool_extension_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  バッファー プール拡張に関する構成情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 バッファー プール拡張ファイルごとに 1 行を返します。  
  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|path|**nvarchar**(256)|バッファー プール拡張キャッシュのパスとファイル名。 Null 値を許容します。|  
|file_id|**int**|バッファー プール拡張ファイルの ID。 NULL 値は許可されません。|  
|state|**int**|バッファー プール拡張機能の状態。 NULL 値は許可されません。<br /><br /> 0 - バッファー プール拡張機能が無効<br /><br /> 1 - バッファー プール拡張機能の無効化<br /><br /> 2 - 将来使用するために予約<br /><br /> 3 - バッファー プール拡張機能の有効化<br /><br /> 4 - 予約済み<br /><br /> 5 - バッファー プール拡張機能が有効|  
|state_description|**nvarchar**(60)|バッファー プール拡張機能の状態を説明します。 NULL 値が許可されます。<br /><br /> 0 = バッファー プール拡張機能が無効<br /><br /> 1 = バッファー プール拡張機能が有効|  
|current_size_in_kb|**bigint**|バッファー プール拡張ファイルの現在のサイズ。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-configuration-buffer-pool-extension-information"></a>A. バッファー プール拡張の構成情報を返す  
 次の例は、sys.dm_os_buffer_pool_extension_configruation DMV のすべての列を返します。  
  
```sql  
SELECT path, file_id, state, state_description, current_size_in_kb  
FROM sys.dm_os_buffer_pool_extension_configuration;  
```  
  
### <a name="b-returning-the-number-of-cached-pages-in-the-buffer-pool-extension-file"></a>B. バッファー プール拡張ファイル内のキャッシュされたページ数を返す  
 次の例は、各バッファー プール拡張ファイル内のキャッシュされたページ数を返します。  
  
```sql  
SELECT COUNT(*) AS cached_pages_count  
FROM sys.dm_os_buffer_descriptors  
WHERE is_in_bpool_extension <> 0  
;  
```  
  
## <a name="see-also"></a>参照  
 [バッファー プール拡張](../../database-engine/configure-windows/buffer-pool-extension.md)   
 [sys.dm_os_buffer_descriptors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-descriptors-transact-sql.md)  
  
  
