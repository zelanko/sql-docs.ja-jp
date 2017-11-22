---
title: "sys.sp_rda_reconcile_batch (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba2e281c7f5593425bd67b817e02d81ee29a4742
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  リモートの Azure テーブルに格納されているバッチ ID を持つ SQL Server の Stretch 対応テーブルに格納されているバッチ ID を調整します。  
  
 通常のみ実行する必要が**sp_rda_reconcile_batch**リモート テーブルから、最近に移行されたデータを手動で削除した場合。 最新のバッチを含むリモート データを手動で削除するときに、バッチ Id は同期と移行が停止します。  
 
 既に Azure に移行されたデータを削除するのには、このページで、「解説」を参照してください。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>引数  
 @objname = '*@objname*'  
 SQL Server の Stretch 対応テーブルの名前。  
  
## <a name="permissions"></a>Permissions  
 Db_owner アクセス許可が必要です。  
  
## <a name="remarks"></a>解説  
 Azure に既に移行済みのデータを削除する場合は、次の手順に従います。  
  
1.  データ移行を一時停止します。 詳細については、次を参照してください。[一時停止と再開データの移行 &#40;です。Stretch Database &#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  STAGE_ONLY ヒントと DELETE コマンドを実行して、SQL Server のステージング テーブルからデータを削除します。 詳細については、次を参照してください。[管理者用の更新および削除を行う](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints)です。
  
3.  REMOTE_ONLY ヒントと DELETE コマンドを実行して、リモート Azure テーブルから同じデータを削除します。  
  
4.  実行**sp_rda_reconcile_batch**です。  
  
5.  データ移行を再開します。 詳細については、次を参照してください。[一時停止と再開データの移行 &#40;です。Stretch Database &#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>例  
 バッチ Id を調整するには、次のステートメントを実行します。  
  
```tsql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
