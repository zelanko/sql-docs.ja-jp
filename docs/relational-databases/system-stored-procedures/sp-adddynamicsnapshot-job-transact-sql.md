---
title: sp_adddynamicsnapshot_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddynamicsnapshot_job
- sp_adddynamicsnapshot_job_TSQL
helpviewer_keywords:
- sp_adddynamicsnapshot_job
ms.assetid: ef50ccf6-e360-4e4b-91b9-6706b8fabefa
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d725b9cbec3d00bf8536954caf423edeae628764
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072745"
---
# <a name="spadddynamicsnapshotjob-transact-sql"></a>sp_adddynamicsnapshot_job (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パラメーター化された行フィルターを使用したパブリケーションのフィルター選択されたデータ スナップショットを生成するエージェント ジョブを作成します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。 このストアド プロシージャは、サブスクライバーのフィルター選択されたデータ スナップショット ジョブを手動で作成する、管理者が使用されます。  
  
> [!NOTE]  
>  フィルター選択されたデータ スナップショット ジョブを作成するためには、パブリケーションの標準スナップショット ジョブが既に存在する必要があります。  
  
 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]   
    [ , [ @host_name = ] 'host_name' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' OUTPUT ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' OUTPUT ]   
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` フィルター選択されたデータ スナップショット ジョブを追加するパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @suser_sname = ] 'suser_sname'` 値によってフィルター選択は、サブスクリプションのフィルター選択されたデータ スナップショットを作成するときに使用される値は、 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)サブスクライバーでの関数。 *suser_sname*は**sysname**、既定値はありません。 *suser_sname*この関数は、パブリケーションを動的にフィルター選択に使用しない場合は NULL になります。  
  
`[ @host_name = ] 'host_name'` 値によってフィルター選択は、サブスクリプションのフィルター選択されたデータ スナップショットを作成するときに使用される値は、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)サブスクライバーでの関数。 *host_name*は**sysname**、既定値はありません。 *host_name*この関数は、パブリケーションを動的にフィルター選択に使用しない場合は NULL になります。  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'` 作成するフィルター選択されたデータ スナップショット ジョブの名前です。 *dynamic_snapshot_jobname*は**sysname**、既定値は NULL の場合は省略可能な出力パラメーター。 指定した場合*dynamic_snapshot_jobname*ディストリビューター側で一意なジョブに解決する必要があります。 指定しない場合、ジョブ名が自動的に生成され、名前が作成されている次のように、結果セットで返されます。  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
> [!NOTE]  
>  動的スナップショット ジョブの名前を生成するときに、標準スナップショット ジョブの名前が切り捨てられる可能性があります。  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'` 作成するフィルター選択されたデータ スナップショット ジョブの識別子です。 *dynamic_snapshot_jobid*は**uniqueidentifier**、既定値は NULL の場合は省略可能な出力パラメーター。  
  
`[ @frequency_type = ] frequency_type` フィルター選択されたデータ スナップショット ジョブをスケジュールする頻度です。 *frequency_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4** (既定値)|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64**|自動開始|  
|**128**|定期的な|  
  
`[ @frequency_interval = ] frequency_interval` フィルター選択されたデータ スナップショット ジョブが実行されると期間 (日単位) です。 *frequency_interval*は**int**、既定値は 1、の値に依存して*frequency_type*します。  
  
|値*frequency_type*|影響を与える*frequency_interval*|  
|--------------------------------|-------------------------------------|  
|**1**|*frequency_interval*は使用されません。|  
|**4** (既定値)|すべて*frequency_interval*既定値は日単位、日。|  
|**8**|*frequency_interval*は、次の 1 つ以上 (と組み合わせて、 [ &#124; &#40;ビットごとの OR&#41; &#40;TRANSACT-SQL&#41; ](../../t-sql/language-elements/bitwise-or-transact-sql.md)論理演算子)。<br /><br /> **1**日曜日&#124; **2** = 月曜日&#124; **4** = 火曜日&#124; **8** = 水曜日&#124; **16** =木曜日&#124; **32** = 金曜日&#124; **64** = 土曜日|  
|**16**|*Frequency_interval*します月の日。|  
|**32**|*frequency_interval*は、次の 1 つです。<br /><br /> **1**日曜日&#124; **2** = 月曜日&#124; **3** = 火曜日&#124; **4** = 水曜日&#124; **5** =木曜日&#124; **6** = 金曜日&#124; **7** = 土曜日&#124; **8**日 = &#124; **9** Weekday&#124; **10** = 土日|  
|**64**|*frequency_interval*は使用されません。|  
|**128**|*frequency_interval*は使用されません。|  
  
`[ @frequency_subday = ] frequency_subday` 単位を指定します*frequency_subday_interval*します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|Second|  
|**4** (既定値)|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 数は、 *frequency_subday*ジョブの実行の間で発生する期間。 *frequency_subday_interval*は**int**、既定値は 5 です。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` 1 か月あたりで、フィルター選択されたデータ スナップショット ジョブの発生です。 このパラメーターが使用されるときに *frequency_type* に設定されている **32** (月単位)。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1** (既定値)|First|  
|**2**|第 2 週|  
|**4**|サードパーティ|  
|**8**|4 番目|  
|**16**|Last|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は 0。  
  
`[ @active_start_date = ] active_start_date` フィルター選択されたデータ スナップショット ジョブの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値は NULL です。  
  
`[ @active_end_date = ] active_end_date` フィルター選択されたデータ スナップショット ジョブが停止されているスケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_end_date*は**int**、既定値は NULL です。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` フィルター選択されたデータ スナップショット ジョブの時間を最初にスケジュール、hhmmss 形式で指定として書式設定します。 *active_start_time_of_day* は **int** 、既定値は NULL です。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` フィルター選択されたデータ スナップショット ジョブが停止されているスケジュールに、hhmmss 形式で指定として書式設定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|フィルター選択されたデータ スナップショット ジョブの識別、 [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md)システム テーブル。|  
|**dynamic_snapshot_jobname**|**sysname**|フィルター選択されたデータ スナップショット ジョブの名前です。|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|一意に識別する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ディストリビューターでエージェント ジョブ。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_adddynamicsnapshot_job**パラメーター化されたフィルターを使用するパブリケーションのマージ レプリケーションに使用されます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-adddynamicsnapshot-jo_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_adddynamicsnapshot_job**します。  
  
## <a name="see-also"></a>関連項目  
 [パラメーター化されたフィルターによるマージ パブリケーションのスナップショットを作成します。](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [sp_dropdynamicsnapshot_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md)   
 [sp_helpdynamicsnapshot_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md)  
  
  
