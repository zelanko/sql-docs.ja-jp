---
title: "sys.sp_rda_set_rpo_duration (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 82a07f1a75cc35aa05fe47c3a5c1324c0c1c0af4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syssprdasetrpoduration-transact-sql"></a>sys.sp_rda_set_rpo_duration (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  確実に、リモート Azure データベースの完全復元ポイントイン タイム復元が必要な場合にステージング テーブルでは、SQL Server が保持される移行データの時間数を設定します。    
    
 詳細については、次を参照してください。 [Stretch Database が移行された行を一時的に保持して、Azure データのデータ損失のリスクを軽減](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)です。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>構文    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>引数    
 [ @duration_hrs = ] *duration_hrs*    
 時間の数です (null 以外の整数値)、現在の Stretch 対応データベースに保持する SQL Server が必要な移行したデータ。 既定値と最小値は、8 時間です。    
 
 > [!NOTE]
 > 値が大きいほどでは、SQL Server の記憶領域が必要です。
    
## <a name="permissions"></a>権限    
 Db_owner アクセス許可が必要です。    
    
## <a name="remarks"></a>解説    
 実行して、現在の値を取得[sys.sp_rda_get_rpo_duration &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)。    
    
## <a name="see-also"></a>参照    
 [sys.sp_rda_get_rpo_duration &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [データベースの復元 Stretch が有効な (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
