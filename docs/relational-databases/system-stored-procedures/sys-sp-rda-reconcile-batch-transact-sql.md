---
title: sys.sp_rda_reconcile_batch (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 54bdac5237ff190f3620bb29dabbf684868c0b75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982928"
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  リモートの Azure テーブルに格納されているバッチ ID を持つ、Stretch 対応 SQL Server テーブルに格納されているバッチ ID を調整します。  
  
 通常のみ実行する必要が**sp_rda_reconcile_batch**リモート テーブルから、最近に移行されたデータを手動で削除した場合。 リモート データを最新バッチを含むを手動で削除すると、バッチ Id は、同期し、移行が停止します。  
 
 既に Azure に移行されたデータを削除するのには、このページで、「解説」を参照してください。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>引数  
 \@objname = ' *\@objname*'  
 Stretch 対応 SQL Server テーブルの名前。  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  
  
## <a name="remarks"></a>コメント  
 既に Azure に移行するデータを削除する場合は、次のことを行います。  
  
1.  データ移行の一時停止します。 詳細については、「[データ移行の一時停止と再開 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)」を参照してください。  
  
2.  STAGE_ONLY ヒントと DELETE コマンドを実行して、SQL Server のステージング テーブルからデータを削除します。 詳細については、次を参照してください。[管理更新と削除を行う](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints)します。
  
3.  REMOTE_ONLY ヒントと DELETE コマンドを実行して、リモート Azure テーブルから同じデータを削除します。  
  
4.  実行**sp_rda_reconcile_batch**します。  
  
5.  データ移行を再開します。 詳細については、「[データ移行の一時停止と再開 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)」を参照してください。  
  
## <a name="example"></a>例  
 バッチ Id を調整するには、次のステートメントを実行します。  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
