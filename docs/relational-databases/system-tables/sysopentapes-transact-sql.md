---
title: sysopentapes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c6f368356df76c68594443ac5a981ebf8f20bec2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260385"
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在開いているテープ デバイスごとに 1 行のデータを格納します。 このビューは、**マスター**データベース。  
  
> [!IMPORTANT]  
>  このシステム テーブルは、旧バージョンとの互換性のためのビューとして用意されています。 代わりに、使用、 [sys.dm_io_backup_tapes &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md)動的管理ビュー。  
  
> [!NOTE]  
>  削除することはできません、 **sysopentapes**ビュー。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar(64)**|開いているテープ デバイスの物理ファイル名。 詳細については、開くおよびテープ デバイスを解放する、次を参照してください。[バックアップ&#40;TRANSACT-SQL&#41; ](../../t-sql/statements/backup-transact-sql.md)と[復元&#40;TRANSACT-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)です。|  
  
## <a name="permissions"></a>権限  
 ユーザーには、サーバーに対する VIEW SERVER STATE 権限が必要があります。  
  
  
