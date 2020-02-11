---
title: managed_backup。 sp_backup_master_switch (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
- sp_ backup_master_switch_TSQL
- smart_admin.sp_backup_master_switch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
ms.assetid: 1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bb151279d1435c544de406e67384ce9ca1fdd11e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942065"
---
# <a name="managed_backupsp_backup_master_switch-transact-sql"></a>managed_backup。 sp_backup_master_switch (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  を[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]一時停止または再開します。  
  
 一時停止して再開[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]するには、このストアドプロシージャを使用します。 これにより、すべての構成設定はそのまま保持され、サービスの再開時にもその設定は維持されています。 が[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]一時停止されている場合、保有期間は適用されません。 つまり、ファイルをストレージから削除する必要があるかどうか、またはバックアップファイルが壊れているかどうか、またはログチェーンを中断するかどうかを確認するチェックは行われません。  
  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC managed_backup.sp_backup_master_switch   
                     [@new_state = ] { 0 | 1}  
```  
  
##  <a name="Arguments"></a>数値  
 @state  
 の[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]状態を設定します。 @stateパラメーターは**BIT**です。 値を0に設定すると、操作は一時停止されます。値を1に設定すると、操作が再開されます。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>Security  
 このステートメントに関連したセキュリティの問題について説明します。サブセクション (H3 見出し) として「権限」を含めます。 必要に応じて、組み合わせ所有権や監査に関する他のサブセクションを含めることを検討してください。  
  
### <a name="permissions"></a>アクセス許可  
 **Db_backupoperator**データベースロールのメンバーシップ、 **ALTER ANY CREDENTIAL**権限、および**Sp_delete_backuphistory**ストアドプロシージャに対する**EXECUTE**権限が必要です。  
  
## <a name="examples"></a>例  
 次の例を使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を、そのバックアップが実行されているインスタンス上で一時停止できます。  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
 次の例を使用すると、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を再開できます。  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=1;  
Go  
  
```  
  
## <a name="see-also"></a>参照  
 [Microsoft Azure への SQL Server マネージド バックアップ](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
