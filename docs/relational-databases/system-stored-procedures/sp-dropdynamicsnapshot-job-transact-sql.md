---
title: sp_dropdynamicsnapshot_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0c9f33c4f50f77ed8ded47b6d7f69a2476f49227
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830167"
---
# <a name="sp_dropdynamicsnapshot_job-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パラメーター化された行フィルターを持つパブリケーションに関する、フィルター選択されたデータ スナップショット ジョブを削除します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。 ジョブが削除されると、すべての関連データが[Msdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md)システムテーブルから削除されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`フィルター選択されたデータスナップショットジョブを削除するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'`削除するフィルター選択されたデータスナップショットジョブの名前を指定します。 *dynamic_snapshot_jobname*は sysname です。指定されていない場合は、 *dynamic_snapshot_jobid*に関連付けられているジョブ名が既定値になります。  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'`削除するフィルター選択されたデータスナップショットジョブの識別子を選択します。 *dynamic_snapshot_jobid*は**uniqueidentifier**,、既定値は NULL です。  
  
> [!IMPORTANT]  
>  *Dynamic_snapshot_jobid*または*dynamic_snapshot_jobname*のみを指定できます。 *Dynamic_snapshot_jobid*または*dynamic_snapshot_jobname*のいずれにも値が指定されていない場合は、パブリケーションのすべての動的スナップショットジョブが削除されます。  
  
`[ @ignore_distributor = ] ignore_distributor`*ignore_distributor*は**ビット**,、既定値は**0**です。 このパラメーターは、ディストリビューターでクリーンアップを実行せずに動的スナップショット ジョブを削除する場合に使用できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropdynamicsnapshot**は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_dropdynamicsnapshot**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_adddynamicsnapshot_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
