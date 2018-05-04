---
title: sp_changesubstatus (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changesubstatus
- sp_changesubstatus_TSQL
helpviewer_keywords:
- sp_changesubstatus
ms.assetid: 9370e47a-d128-4f15-9224-1c3642770c39
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c28d008a3eba995afce4cb302ecdc1428a5be397
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spchangesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のサブスクライバーの状態を変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changesubstatus [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
        , [ @status = ] 'status'  
    [ , [ @previous_status = ] 'previous_status' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @distribution_jobid = ] distribution_jobid ]  
    [ , [ @from_auto_sync = ] from_auto_sync ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @offloadagent= ] remote_agent_activation ]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] dts_package_location ]  
    [ , [ @skipobjectactivation = ] skipobjectactivation  
  [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%** です。 場合*パブリケーション*が指定されていない、すべてのパブリケーションが影響を受けます。  
  
 [  **@article=**] **'***記事***'**  
 アーティクルの名前を指定します。 アーティクルの名前はパブリケーションに対して一意である必要があります。 *記事*は**sysname**、既定値は **%** です。 場合*記事*が指定されていない、すべてのアーティクルが影響を受けます。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 状態を変更するサブスクライバーの名前を指定します。 *サブスクライバー*は**sysname**、既定値は **%** です。 場合*サブスクライバー*が指定されていない、すべてのサブスクライバーの指定したアーティクルの状態が変更されました。  
  
 [  **@status =**] **'***ステータス***'**  
 サブスクリプションの状態で、 **syssubscriptions**テーブル。 *ステータス*は**sysname**, で、既定値はありませんはこれらの値のいずれかを指定します。  
  
|値|Description|  
|-----------|-----------------|  
|**アクティブ**|サブスクライバーの同期がとられ、データを受信しています。|  
|**非アクティブ**|サブスクライブはしていませんが、サブスクライバーのエントリが存在します。|  
|**サブスクライブしています。**|サブスクライバーはデータを要求していますが、まだ同期はとられていません。|  
  
 [  **@previous_status=**] **'***previous_status***'**  
 サブスクリプションの前の状態を指定します。 *previous_status*は**sysname**、既定値は NULL です。 このパラメーターでは、現在のサブスクリプションの特定のグループの機能できるように、ステータスを持つ任意のサブスクリプションを変更することができます (たとえば、すべてのアクティブな設定をバックアップするサブスクリプション**サブスクライブしている**)。  
  
 [  **@destination_db=**] **'***destination_db***'**  
 対象データベース名を指定します。 *destination_db*は**sysname**、既定値は **%** です。  
  
 [  **@frequency_type=**] *frequency_type*  
 ディストリビューション タスクをスケジュールに組み込む頻度を指定します。 *frequency_type*は**int**、既定値は NULL です。  
  
 [  **@frequency_interval=**] *frequency_interval*  
 設定した頻度に適用する値は、 *frequency_type*です。 *frequency_interval*は**int**、既定値は NULL です。  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 ディストリビューション タスクを実施する日を指定します。 このパラメーターが使用されるときに*frequency_type* 32 (月単位) に設定されています。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
|NULL (既定値)||  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 によって使用される定期実行係数*frequency_type*です。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
 [  **@frequency_subday=**] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を分単位で指定します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (既定値)||  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 間隔は、 *frequency_subday*です。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 ディストリビューション タスクを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 ディストリビューション タスクのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@active_start_date=**] *active_start_date*  
 ディストリビューション タスクを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は NULL です。  
  
 [  **@active_end_date=**] *active_end_date*  
 ディストリビューション タスクのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は NULL です。  
  
 [  **@optional_command_line=**] **'***optional_command_line***'**  
 省略可能なコマンド プロンプトです。 *optional_command_line*は**nvarchar (4000)**、既定値は NULL です。  
  
 [  **@distribution_jobid=**] *distribution_jobid*  
 サブスクリプションの状態を非アクティブからアクティブに変更するときに、サブスクリプションに対して、ディストリビューターにおけるディストリビューション エージェントのジョブ ID を指定します。 その他の場合は、定義されません。 このストアド プロシージャに対する 1 つの呼び出しに複数のディストリビューション エージェントが関係している場合、結果は定義されません。 *distribution_jobid*は**binary (16)**、既定値は NULL です。  
  
 [  **@from_auto_sync=**] *from_auto_sync*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@offloadagent=** ] *remote_agent_activation*  
 > [!NOTE]  
>  リモート エージェント アクティブ化は現在サポートされておらず、非推奨とされます。 このパラメーターは、スクリプトの下位互換性を確保するためだけに用意されています。 設定*remote_agent_activation*以外の値を**0**でエラーが生成されます。  
  
 [  **@offloadserver=** ] **'***remote_agent_server_name***'**  
 > [!NOTE]  
>  リモート エージェント アクティブ化は現在サポートされておらず、非推奨とされます。 このパラメーターは、スクリプトの下位互換性を確保するためだけに用意されています。 設定*remote_agent_server_name* NULL 以外の値にエラーが生成されます。  
  
 [ **@dts_package_name**=] **'***dts_package_name***'**  
 データ変換サービス (DTS) パッケージの名前。 *dts_package_name*は、 **sysname**、既定値は NULL です。 たとえば、という名前のパッケージ**DTSPub_Package**を指定する場合`@dts_package_name = N'DTSPub_Package'`です。  
  
 [ **@dts_package_password**=] **'***dts_package_password***'**  
 パッケージのパスワードを指定します。 *dts_package_password*は**sysname**既定値は NULL の場合、変更されていないパスワード プロパティのままにすることを指定します。  
  
> [!NOTE]  
>  DTS パッケージにはパスワードが必要です。  
  
 [ **@dts_package_location**=] *dts_package_location*  
 パッケージの場所を指定します。 *dts_package_location*は、 **int**、既定値は**0**します。 場合**0**ディストリビューターでは、パッケージの場所。 場合**1**パッケージの場所はサブスクライバーです。 パッケージの場所を指定できます**ディストリビューター**または**サブスクライバー**です。  
  
 [ **@skipobjectactivation**=] *skipobjectactivation*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@distribution_job_name=** ] **'***distribution_job_name***'**  
 ディストリビューション ジョブの名前を指定します。 *distribution_job_name*は**sysname**、既定値は NULL です。  
  
 [ **@publisher**=] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*でアーティクルのプロパティを変更するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changesubstatus**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 **sp_changesubstatus**でサブスクライバーの状態変更、 **syssubscriptions**変更されたステータスを持つテーブルです。 内のアーティクルの状態を更新、必要な場合、 **sysarticles**アクティブまたは非アクティブを示す表。 必要な場合、そのレプリケーション フラグを設定、オンまたはオフ、 **sysobjects**レプリケートされたテーブルのテーブルです。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、またはサブスクリプションの作成者が実行できる**sp_changesubstatus**です。  
  
## <a name="see-also"></a>参照  
 [sp_addsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
