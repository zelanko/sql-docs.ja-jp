---
title: sys.dm_os_host_info (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_os_host_info
- sys.dm_os_host_info_TSQL
- dm_os_host_info
- dm_os_host_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_host_info dynamic management view
ms.assetid: 9bb6ef86-957b-4ca1-ad20-ca2f8460a86d
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0aa5f28f52c9d0df4e942809612e1ca59a1cb3c5
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmoshostinfo-transact-sql"></a>sys.dm_os_host_info (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

オペレーティング システムのバージョン情報を表示する 1 つの行を返します。  
  
|列名 |データ型 |Description |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar (256)** |オペレーティング システムの種類: Windows または Linux |
|**host_distribution** |**nvarchar (256)** |オペレーティング システムの説明です。 |
|**host_release**|**nvarchar (256)**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows オペレーティング システムのリリース (バージョン番号)。 値と説明の一覧は、次を参照してください。[オペレーティング システムのバージョン (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx)です。 <br> Linux、空の文字列を返します。 |  
|**host_service_pack_level**|**nvarchar (256)**|Windows オペレーティング システムの Service Pack のレベル。 <br> Linux、空の文字列を返します。 |  
|**host_sku**|**int**|Windows 在庫商品識別番号 (SKU) ID。 SKU Id と説明の一覧は、次を参照してください。 [GetProductInfo 関数](http://msdn.microsoft.com/library/ms724358.aspx)です。 NULL 値が許可されます。 <br> Linux、NULL を返します。 |  
|**os_language_version**|**int**|オペレーティング システムの Windows ロケール識別子 (LCID)。 LCID 値と説明の一覧は、次を参照してください。 [Microsoft によるロケール Id 割り当て](http://go.microsoft.com/fwlink/?LinkId=208080)です。 null にすることはできません。|  

## <a name="remarks"></a>解説  
このビューがに似ていますが[sys.dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)、Windows および Linux を区別する列を追加します。
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
`SELECT`に対する権限`sys.dm_os_host_info`に与えられる、`public`既定ロール。 失効させた場合、必要`VIEW SERVER STATE`サーバーに対する権限。   
 
>  [!CAUTION]
>  以降のバージョンで[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.3[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)]バージョン 17 で必要な`SELECT`に対する権限`sys.dm_os_host_info`に接続するために[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 場合`SELECT`から権限を取り消す`public`を持つログインだけ`VIEW SERVER STATE`権限は、最新バージョンの SSMS で接続できます。 (などの他のツール`sqlcmd.exe`しなくても接続できます`SELECT`に対する権限`sys.dm_os_host_info`)。

  
## <a name="examples"></a>使用例  
 次の例は、のすべての列を返して、 **sys.dm_os_host_info**ビュー。  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Windows 上でサンプルの結果を次に示します。
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

結果セットを Linux 上のサンプルを次に示します。
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>参照  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 

