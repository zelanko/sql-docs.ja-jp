---
title: dm_os_host_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 052402d3a394e8da3e08828992127d3cd89b95ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900158"
---
# <a name="sysdm_os_host_info-transact-sql"></a>dm_os_host_info (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

オペレーティングシステムのバージョン情報を表示する1行を返します。  
  
|列名 |データ型 |[説明] |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |オペレーティングシステムの種類: Windows または Linux |
|**host_distribution** |**nvarchar(256)** |オペレーティングシステムの説明。 |
|**host_release**|**nvarchar(256)**|[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows オペレーティングシステムのリリース (バージョン番号)。 値と説明の一覧については、「[オペレーティングシステムのバージョン (Windows)](/windows/desktop/SysInfo/operating-system-version)」を参照してください。 <br> Linux の場合、は空の文字列を返します。 |  
|**host_service_pack_level**|**nvarchar(256)**|Windows オペレーティングシステムの Service pack のレベル。 <br> Linux の場合、は空の文字列を返します。 |  
|**host_sku**|**int**|Windows 株価保持ユニット (SKU) ID。 SKU Id と説明の一覧については、「 [Getproductinfo 関数](https://msdn.microsoft.com/library/ms724358.aspx)」を参照してください。 NULL 値が許可されます。 <br> Linux の場合、は NULL を返します。 |  
|**os_language_version**|**int**|オペレーティングシステムの Windows ロケール識別子 (LCID)。 LCID 値と説明の一覧については、「 [Microsoft によって割り当てられたロケール id](https://go.microsoft.com/fwlink/?LinkId=208080)」を参照してください。 null にすることはできません。|  

## <a name="remarks"></a>解説  
このビューは、Windows と Linux を区別するために列を追加する dm_os_windows_info に似てい[ます。](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
既定`SELECT`では`sys.dm_os_host_info` 、 `public`に対する権限がロールに付与されます。 取り消す場合は、 `VIEW SERVER STATE`サーバーに対する権限が必要です。   
 
> [!CAUTION]
>  バージョン[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.3 以降では[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] 、に`SELECT` [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]接続するため`sys.dm_os_host_info`に、バージョン17でに対するアクセス許可が必要です。 権限`SELECT`がから`public`取り消された場合、最新`VIEW SERVER STATE`バージョンの SSMS で接続できるのは、権限を持つログインのみです。 (などの他のツール`sqlcmd.exe`は、に`SELECT` `sys.dm_os_host_info`対する権限なしで接続できます)。

  
## <a name="examples"></a>例  
 次の例では、 **dm_os_host_info**ビューからすべての列を返します。  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Windows での結果セットの例を次に示します。
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Linux での結果セットの例を次に示します。
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>参照  
 [dm_os_sys_info &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [dm_os_windows_info (Transact-sql)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 

