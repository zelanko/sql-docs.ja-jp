---
title: "sp_dropdynamicsnapshot_job (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords: sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3cc6dc65589951513a5d05dbfad68cecb8d92745
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パラメーター化された行フィルターを持つパブリケーションに関する、フィルター選択されたデータ スナップショット ジョブを削除します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。 すべての関連するデータはから削除、ジョブが削除されると、 [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md)システム テーブル。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 フィルター選択されたデータ スナップショット ジョブを削除するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@dynamic_snapshot_jobname** =] **'***dynamic_snapshot_jobname***'**  
 削除対象となる、フィルター選択されたデータ スナップショット ジョブの名前を指定します。 *dynamic_snapshot_jobname*sysname で、既定の設定ではない場合にどのようなジョブ名に関連付けられて*dynamic_snapshot_jobid*です。  
  
 [  **@dynamic_snapshot_jobid** =] **'***dynamic_snapshot_jobid***'**  
 削除対象となる、フィルター選択されたデータ スナップショット ジョブの ID を指定します。 *dynamic_snapshot_jobid*は**uniqueidentifier**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  のみ*dynamic_snapshot_jobid*または*dynamic_snapshot_jobname*を指定できます。 いずれかの値が指定されなかった場合*dynamic_snapshot_jobid*または*dynamic_snapshot_jobname*パブリケーションのすべての動的スナップショット ジョブが削除されます。  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 *ignore_distributor*は**ビット**、既定値は**0**します。 このパラメーターは、ディストリビューターでクリーンアップを実行せずに動的スナップショット ジョブを削除する場合に使用できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropdynamicsnapshot**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_dropdynamicsnapshot**です。  
  
## <a name="see-also"></a>参照  
 [sp_adddynamicsnapshot_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
