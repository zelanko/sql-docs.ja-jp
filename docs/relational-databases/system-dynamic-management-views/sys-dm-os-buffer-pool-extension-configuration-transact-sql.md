---
title: dm_os_buffer_pool_extension_configuration (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_buffer_pool_extension_configuration
- sys.dm_os_buffer_pool_extension_configuration_TSQL
- dm_os_buffer_pool_extension_configuration_TSQL
- sys.dm_os_buffer_pool_extension_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_pool_extension_configuration dynamic management view
ms.assetid: d52cc481-4d29-4f33-b63d-231ec35d092f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38e4e1ad85a5e968d4b0bb33a3a72a829942585b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900218"
---
# <a name="sysdm_os_buffer_pool_extension_configuration-transact-sql"></a>dm_os_buffer_pool_extension_configuration (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バッファープール拡張に関する構成情報を返します。 バッファープール拡張ファイルごとに1行の値を返します。  
  

  
| 列名 | データ型 | 説明 |
| :---------- | :-------- | :---------- |
|パス|**nvarchar**(256)|バッファー プール拡張キャッシュのパスとファイル名。 NULL 値は許可されます。|  
|file_id|**int**|バッファー プール拡張ファイルの ID。 NULL 値は許可されません。|  
|state|**int**|バッファー プール拡張機能の状態。 NULL 値は許可されません。<br /><br /> 0 - バッファー プール拡張機能が無効<br /><br /> 1 - バッファー プール拡張機能の無効化<br /><br /> 2-将来使用するために予約されています<br /><br /> 3 - バッファー プール拡張機能の有効化<br /><br /> 4-将来使用するために予約されています<br /><br /> 5 - バッファー プール拡張機能が有効|  
|state_description|**nvarchar**(60)|バッファー プール拡張機能の状態を説明します。 NULL 値が許可されます。<br /><br /> 0 = バッファー プール拡張機能が無効<br /><br /> 5 = バッファープール拡張機能が有効|
|current_size_in_kb|**bigint**|バッファープール拡張ファイルの現在のサイズ。 NULL 値は許可されません。|
| &nbsp; | &nbsp; | &nbsp; |

## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-returning-configuration-buffer-pool-extension-information"></a>A. バッファー プール拡張の構成情報を返す  
 次の例では、dm_os_buffer_pool_extension_configruation DMV からすべての列を返します。  
  
```sql  
SELECT path, file_id, state, state_description, current_size_in_kb  
FROM sys.dm_os_buffer_pool_extension_configuration;  
```  
  
### <a name="b-returning-the-number-of-cached-pages-in-the-buffer-pool-extension-file"></a>B. バッファープール拡張ファイル内のキャッシュされたページ数を返す  
 次の例は、各バッファー プール拡張ファイル内のキャッシュされたページ数を返します。  
  
```sql  
SELECT COUNT(*) AS cached_pages_count  
FROM sys.dm_os_buffer_descriptors  
WHERE is_in_bpool_extension <> 0  
;  
```  
  
## <a name="see-also"></a>参照  
 [バッファープール拡張機能](../../database-engine/configure-windows/buffer-pool-extension.md)   
 [sys.dm_os_buffer_descriptors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-descriptors-transact-sql.md)  
  
  
