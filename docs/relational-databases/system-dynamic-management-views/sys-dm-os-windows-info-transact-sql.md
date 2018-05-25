---
title: sys.dm_os_windows_info (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6f6669704242a780d947dc271cb81724429992a
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmoswindowsinfo-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows オペレーティング システムのバージョン情報を示す 1 行のデータを返します。  
  
  Windows で実行されている SQL Server にのみ適用されます。 使用して、Linux などの非 Windows ホストで実行されている SQL Server のような情報を参照する[sys.dm_os_host_info &#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)です。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar (256)**|、Windows のリリース番号を返します。 値と説明の一覧は、次を参照してください。[オペレーティング システムのバージョン (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx)です。 NULL 値は許容されません。|  
|**windows_service_pack_level**|**nvarchar (256)**| Windows の場合は、サービス パック番号を返します。 NULL 値は許容されません。 |  
|**windows_sku**|**int**|Windows の場合に、Windows Stock Keeping 単位 (SKU) ID を返します。 SKU Id と説明の一覧は、次を参照してください。 [GetProductInfo 関数](http://msdn.microsoft.com/library/ms724358.aspx)です。 値が許容されます。 |  
|**os_language_version**|**int**| Windows の場合は、オペレーティング システムの Windows ロケール識別子 (LCID) を返します。 LCID 値と説明の一覧は、次を参照してください。 [Microsoft によるロケール Id 割り当て](http://go.microsoft.com/fwlink/?LinkId=208080)です。 NULL 値は許容されません。|  
  
  
## <a name="permissions"></a>権限  
Sys.dm_os_windows_info に対する SELECT 権限は、既定では、public ロールに与えられます。 失効させた場合、サーバーに対する VIEW SERVER STATE 権限が必要です。  

## <a name="limitations-and-restrictions"></a>制限事項と制約事項
Linux などの非 Windows ホストで実行されている SQL の情報を表示する使用[sys.dm_os_host_info &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)です。 
  
## <a name="examples"></a>使用例  
 次の例は、のすべての列を返して、 **sys.dm_os_windows_info**ビュー。  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 次に結果セットの例を示します。  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>参照  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  

