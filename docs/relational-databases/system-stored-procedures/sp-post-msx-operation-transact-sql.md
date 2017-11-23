---
title: "sp_post_msx_operation (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_post_msx_operation
- sp_post_msx_operation_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_post_msx_operation
ms.assetid: 085deef8-2709-4da9-bb97-9ab32effdacf
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1774a033e119f14e89a0f5fe141dd99ee0453ec9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sppostmsxoperation-transact-sql"></a>sp_post_msx_operation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  操作 (行) を挿入、 **sysdownloadlist**をダウンロードして実行する対象サーバーのシステム テーブル。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_post_msx_operation  
     [ @operation = ] 'operation'  
     [ , [ @object_type = ] 'object' ]   
     { , [ @job_id = ] job_id }   
     [ , [ @specific_target_server = ] 'target_server' ]   
     [ , [ @value = ] value ]  
     [ , [ @schedule_uid = ] schedule_uid ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@operation =**] **'***操作***'**  
 通知する操作の種類を指定します。 *操作*は**varchar (64)**、既定値はありません。 有効な操作によって異なります*object_type*です。  
  
|オブジェクトの種類|操作|  
|-----------------|---------------|  
|**ジョブ**|INSERT<br /><br /> UPDATE<br /><br /> DELETE<br /><br /> START<br /><br /> STOP|  
|**サーバー**|RE-ENLIST<br /><br /> DEFECT<br /><br /> SYNC-TIME<br /><br /> SET-POLL|  
|**スケジュール**|INSERT<br /><br /> UPDATE<br /><br /> DELETE|  
  
 [  **@object_type =**] **'***オブジェクト***'**  
 操作を通知するオブジェクトの種類を指定します。 有効な種類は**ジョブ**、**サーバー**、および**スケジュール**です。 *オブジェクト*は**varchar (64)**、既定値は**ジョブ**です。  
  
 [  **@job_id =**] *job_id*  
 操作が適用されるジョブのジョブ識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値はありません。 **0x00**すべてのジョブを示します。 場合*オブジェクト*は**サーバー**、し*job_id*は必要ありません。  
  
 [  **@specific_target_server =**] **'***target_server***'**  
 指定した操作を適用する対象サーバーの名前を指定します。 場合*job_id*が指定されているが、 *target_server*が指定されていない、すべてのジョブ、ジョブのサーバー操作が通知されます。 *target_server*は**nvarchar (30)**、既定値は NULL です。  
  
 [  **@value =**]*値*  
 ポーリング間隔を秒数で指定します。 *value* のデータ型は **int**で、既定値は NULL です。 場合にのみ、このパラメーターを指定*操作*は**SET-POLL**です。  
  
 [  **@schedule_uid=** ] *schedule_uid*  
 操作が適用されるスケジュールの一意識別子を指定します。 *schedule_uid*は**uniqueidentifier**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_post_msx_operation**から実行する必要があります、 **msdb**データベース。  
  
 **sp_post_msx_operation**常に呼び出せる安全にまずを指定するため、現在のサーバーがマルチ サーバーの Microsoft SQL Server エージェントの場合、必要な場合は、かどうか*オブジェクト*マルチ サーバー ジョブです。  
  
 操作が通知されるに表示され、 **sysdownloadlist**テーブル。 ジョブを作成し通知した後でそのジョブに変更を加える場合は、対象サーバー (TSX) にその変更を伝える必要があります。 これを行うには、ダウンロードの一覧を使用します。  
  
 ダウンロードの一覧は、SQL Server Management Studio を使用して管理することを強くお勧めします。 詳細については、次を参照してください。[の表示または変更ジョブ](http://msdn.microsoft.com/library/57f649b8-190c-4304-abd7-7ca5297deab7)です。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャを実行するユーザーに付与する必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="see-also"></a>参照  
 [sp_add_jobserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_delete_targetserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_resync_targetserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)   
 [sp_start_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_stop_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [sp_update_operator &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
