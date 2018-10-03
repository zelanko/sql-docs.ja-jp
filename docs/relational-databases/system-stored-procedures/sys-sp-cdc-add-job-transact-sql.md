---
title: sys.sp_cdc_add_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_add_job_TSQL
- sys.sp_cdc_add_job
- sys.sp_cdc_add_job_TSQL
- sp_cdc_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_add_job
ms.assetid: c4458738-ed25-40a6-8294-a26ca5a05bd9
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 544f6d9f8610ff9845df4c417d880fd88c4c180c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812107"
---
# <a name="sysspcdcaddjob-transact-sql"></a>sys.sp_cdc_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに、変更データ キャプチャ機能のクリーンアップ ジョブまたはキャプチャ ジョブを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_add_job [ @job_type = ] 'job_type'  
    [ , [ @start_job = ] start_job ]   
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ , [ @threshold ] = 'delete_threshold' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@job_type=** ] **'***job_type***'**  
 追加するジョブの種類を指定します。 *job_type*は**nvarchar (20)** NULL にすることはできません。 有効な入力は **'capture'** と **'cleanup'** します。  
  
 [  **@start_job=** ] *start_job*  
 ジョブの追加後、そのジョブを直ちに開始するかどうかを指定するフラグです。 *start_job*は**ビット**既定値は 1 です。  
  
 [ **@maxtrans** ] = *max_trans*  
 各スキャン サイクルで処理する最大トランザクション数を指定します。 *max_trans*は**int**既定値は 500 です。 指定する場合、値は正の整数にする必要があります。  
  
 *max_trans*はキャプチャ ジョブでのみ有効です。  
  
 [ **@maxscans** ] **= * * * max_scans*  
 ログからすべての行を抽出するために実行する最大スキャン サイクル数を指定します。 *max_scans*は**int**既定値は 10 です。  
  
 *max_scan*はキャプチャ ジョブでのみ有効です。  
  
 [ **@continuous** ] **= * * * 継続的な*  
 キャプチャ ジョブを連続的に実行するか (1)、1 回だけ実行するか (0) を指定します。 *継続的な*は**ビット**既定値は 1 です。  
  
 ときに*連続*= 1、 [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md)ジョブは、ログをスキャンし、最大処理 (*max_trans* \* *max_scans*)トランザクション。 指定された秒数待機し、 *polling_interval*次のログ スキャンを開始する前にします。  
  
 ときに*連続*= 0 の場合、 **sp_cdc_scan**ジョブが実行されるまで*max_scans*までの処理、ログのスキャン*max_trans*トランザクション中に各スキャン、およびし終了します。  
  
 *継続的な*はキャプチャ ジョブでのみ有効です。  
  
 [ **@pollinginterval** ] **= * * * polling_interval*  
 ログ スキャン サイクルの間隔を秒数で指定します。 *polling_interval*は**bigint**既定値は 5 です。  
  
 *polling_interval*キャプチャに対してのみ有効ですがジョブの場合に*連続*が 1 に設定します。 指定する場合、値には負の数を指定できず、24 時間が上限になります。 値 0 を指定した場合、ログ スキャンの間に待機時間はありません。  
  
 [ **@retention** ] **= * * * 保有期間*  
 変更データ行が変更テーブルに保持される分数を指定します。 *保有期間*は**bigint**既定値は 4320 (72 時間)。 最大値は 52494800 (100 年) です。 指定する場合、値は正の整数にする必要があります。  
  
 *保有期間*はクリーンアップ ジョブでのみ有効です。  
  
 [  **@threshold =** ] **'***delete_threshold***'**  
 クリーンアップ時に 1 つのステートメントを使用して削除できる最大削除エントリ数を指定します *delete_threshold*は**bigint**既定値は 5000 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 クリーンアップ ジョブは、データベースの最初のテーブルの変更データ キャプチャを有効にしたときに既定値を使って作成されます。 キャプチャ ジョブは、データベースの最初のテーブルの変更データ キャプチャを有効にしたとき、そのデータベースにトランザクション パブリケーションが存在しなかった場合に、既定値を使って作成されます。 トランザクション パブリケーションが存在する場合、トランザクション ログ リーダーを使ってキャプチャ メカニズムが実現されます。別個のキャプチャ ジョブは必要ありません (使用することもできません)。  
  
 クリーンアップ ジョブとキャプチャ ジョブは既定で作成されるため、このストアド プロシージャが必要となるのは、ジョブを明示的に削除した後で、再び作成する必要が生じた場合だけです。  
  
 ジョブの名前は**cdc ***。< database_name >***_cleanup**または**cdc ***。< database_name >***_capture**ここで、 *< database_name >* 現在のデータベースの名前を指定します。 名前にピリオドが付加されますと同じ名前のジョブが既に存在する場合 (**.**) などの一意の識別子が続く: **cdc です。AdventureWorks_capture します。A1ACBDED-13FC-428C-8302-10100EF74F52**します。  
  
 クリーンアップまたはキャプチャ ジョブの現在の構成を表示する使用[sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)します。 ジョブの構成を変更する[sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-capture-job"></a>A. キャプチャ ジョブを作成する  
 次の例では、キャプチャ ジョブを作成します。 明示的に削除された既存のクリーンアップ ジョブを改めて作成するという状況を想定しています。 ジョブは既定値を使って作成されます。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job @job_type = N'capture';  
GO  
```  
  
### <a name="b-creating-a-cleanup-job"></a>B. クリーンアップ ジョブを作成する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにクリーンアップ ジョブを作成します。 パラメーター `@start_job` は 0 に、`@retention` は 5760 分 (96 時間) に設定します。 明示的に削除された既存のクリーンアップ ジョブを改めて作成するという状況を想定しています。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job  
     @job_type = N'cleanup'  
    ,@start_job = 0  
    ,@retention = 5760;  
```  
  
## <a name="see-also"></a>参照  
 [dbo.cdc_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
