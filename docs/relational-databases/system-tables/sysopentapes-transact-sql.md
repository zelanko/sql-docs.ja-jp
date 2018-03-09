---
title: "sysopentapes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c899ae69ff42eff84bd85a3553c4ff3f1b64c651
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在開いているテープ デバイスごとに 1 行のデータを格納します。 このビューは、**マスター**データベース。  
  
> [!IMPORTANT]  
>  このシステム テーブルは、旧バージョンとの互換性のためのビューとして用意されています。 代わりに、使用、 [sys.dm_io_backup_tapes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md)動的管理ビュー。  
  
> [!NOTE]  
>  削除することはできません、 **sysopentapes**ビュー。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar(64)**|開いているテープ デバイスの物理ファイル名。 詳細については、開くおよびテープ デバイスを解放する、次を参照してください。[バックアップ &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/backup-transact-sql.md)と[復元 &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/restore-statements-transact-sql.md)。|  
  
## <a name="permissions"></a>権限  
 ユーザーには、サーバーに対する VIEW SERVER STATE 権限が必要があります。  
  
  
