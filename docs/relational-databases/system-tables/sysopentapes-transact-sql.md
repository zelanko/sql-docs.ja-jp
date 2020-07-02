---
title: sysopentapes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysopentapes
- sysopentapes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 55ac6d0811e701a4a541b889884c86cb3a83c296
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759990"
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  現在開いているテープ デバイスごとに 1 行のデータを格納します。 このビューは、 **master**データベースに格納されます。  
  
> [!IMPORTANT]  
>  このシステムテーブルは、下位互換性のためのビューとして含まれています。 代わりに、 [dm_io_backup_tapes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md)動的管理ビューを使用します。  
  
> [!NOTE]  
>  **Sysopentapes**ビューを削除することはできません。  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar (64)**|開いているテープ デバイスの物理ファイル名。 テープデバイスを開いて解放する方法の詳細については、「 [transact-sql&#41;のバックアップ &#40;](../../t-sql/statements/backup-transact-sql.md) 」および「 [&#40;Transact-sql&#41;の復元](../../t-sql/statements/restore-statements-transact-sql.md)」を参照してください。|  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーは、サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
  
