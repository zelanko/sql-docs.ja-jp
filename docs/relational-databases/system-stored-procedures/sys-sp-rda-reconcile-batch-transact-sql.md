---
title: sp_rda_reconcile_batch (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c8ce7b946005eca97d57ef709557ec9b4334339c
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053175"
---
# <a name="syssp_rda_reconcile_batch-transact-sql"></a>sp_rda_reconcile_batch (Transact-sql)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Stretch が有効な SQL Server テーブルに格納されているバッチ ID と、リモート Azure テーブルに格納されているバッチ ID を調整します。  
  
 通常は、リモートテーブルから最後に移行されたデータを手動で削除した場合にのみ**sp_rda_reconcile_batch**を実行する必要があります。 最新のバッチを含むリモートデータを手動で削除すると、バッチ Id は同期されなくなり、移行が停止します。  
 
 Azure に既に移行されているデータを削除する方法については、このページの「解説」を参照してください。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>引数  
 \@objname = '* \@ objname*'  
 Stretch が有効な SQL Server テーブルの名前。  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner のアクセス許可が必要です。  
  
## <a name="remarks"></a>注釈  
 Azure に既に移行されているデータを削除する場合は、次の操作を行います。  
  
1.  データ移行を一時停止します。 詳細については、「[データ移行の一時停止と再開 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)」を参照してください。  
  
2.  STAGE_ONLY ヒントと共に DELETE コマンドを実行して、SQL Server ステージングテーブルからデータを削除します。 詳細については、「[管理者の更新と削除を行う](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints)」を参照してください。
  
3.  REMOTE_ONLY ヒントと共に DELETE コマンドを実行して、リモート Azure テーブルから同じデータを削除します。  
  
4.  **Sp_rda_reconcile_batch**を実行します。  
  
5.  データ移行を再開します。 詳細については、「[データ移行の一時停止と再開 &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md)」を参照してください。  
  
## <a name="example"></a>例  
 バッチ Id を調整するには、次のステートメントを実行します。  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
