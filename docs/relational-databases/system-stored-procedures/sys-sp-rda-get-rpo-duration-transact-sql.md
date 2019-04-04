---
title: sys.sp_rda_get_rpo_duration (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_get_rpo_duration
- sys.sp_rda_get_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_get_rpo_duration stored procedure
ms.assetid: 35882067-3072-47ff-9024-ca453c0f49a7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0882344345c315f13d6cca11b7a1d1db88c9417b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769700"
---
# <a name="syssprdagetrpoduration-transact-sql"></a>sys.sp_rda_get_rpo_duration (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  ポイントイン タイム リストアが必要な場合、リモート Azure データベースの完全復元をことを確認するためにステージング テーブルでは、SQL Server を保持する移行されたデータの時間数を取得します。 
  
  詳細については、[Stretch Database は、移行済みの行を一時的に保持して、Azure のデータのデータ損失のリスクを軽減](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)を参照してください。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>構文    
    
```    
    
sp_rda_get_rpo_duration @durationinhours output    
    
```    
    
## <a name="output-parameter"></a>出力パラメーター    
 *@durationinhours*    
  時間数です (null 以外の整数値) の現在の Stretch 対応データベースの SQL Server を保持する移行されたデータ。    
    
## <a name="permissions"></a>アクセス許可    
 Db_owner アクセス許可が必要です。    
    
## <a name="remarks"></a>コメント    
 実行して、値を変更する[sys.sp_rda_set_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)します。    
    
## <a name="see-also"></a>参照    
 [sys.sp_rda_set_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)     
 [Stretch 対応データベース (Stretch Database) の復元します。](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)    
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
