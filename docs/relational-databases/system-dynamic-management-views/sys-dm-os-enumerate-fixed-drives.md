---
title: dm_os_enumerate_fixed_drives (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/18/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_enumerate_fixed_drives
- sys.dm_os_enumerate_fixed_drives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_enumerate_fixed_drives dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c45db91b29c85d6ffced4e31e01fb8f24f338c16
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830536"
---
# <a name="sysdm_os_enumerate_fixed_drives-transact-sql"></a>dm_os_enumerate_fixed_drives (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

SQL Server 2019 で導入されました。

などのドライブ文字にマウントされているボリュームを列挙 `C:\` します。

|列名|データ型|説明|
|-----------------|---------------|-----------------|  
|`fixed_drive_path`|`nvarchar(512)`|ボリュームへのパス (など) `C:\` 。|  
|`drive_type`|`int`|ドライブの種類のコード。 「 [ `GetDriveTypeW` 関数](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew)」を参照してください。|
|`drive_type_desc`|`nvarchar(512)`|ドライブの種類の説明。 「 [ `GetDriveTypeW` 関数](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew)」を参照してください。|
|`free_space_in_bytes`|`bigint`|ディスクの空き領域 (バイト単位)。|

## <a name="permissions"></a>アクセス許可

ユーザーは、サーバーに対する権限を持っている必要があり `VIEW SERVER STATE` ます。

## <a name="see-also"></a>参照  

 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I/o 関連の動的管理ビューおよび関数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
