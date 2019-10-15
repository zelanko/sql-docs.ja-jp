---
title: sp_cdc_change_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_change_job_TSQL
- sys.sp_cdc_change_job
- sp_cdc_change_job_TSQL
- sp_cdc_change_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_change_job
ms.assetid: ea918888-0fc5-4cc1-b301-26b2a9fbb20d
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bd906f9a359a73a15d89a4cb60b6646a2abe53a
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305064"
---
# <a name="syssp_cdc_change_job-transact-sql"></a>sp_cdc_change_job (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースの変更データキャプチャのクリーンアップジョブまたはキャプチャジョブの構成を変更します。 ジョブの現在の構成を表示するには、 [dbo. cdc ジョブ](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)テーブルに対してクエリを実行するか、 [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_change_job [ [ @job_type = ] 'job_type' ]  
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ @threshold = ] 'delete threshold'  
```  
  
## <a name="arguments"></a>引数  
`[ @job_type = ] 'job_type'` 変更するジョブの種類。 *job_type*は**nvarchar (20)** 既定値は ' capture ' です。 有効な入力は ' capture ' と ' cleanup ' です。  
  
@no__t-各スキャンサイクルで処理するトランザクションの最大数。 *max_trans*は**int**既定値は NULL の場合、このパラメーターに変更がないことを示します。 指定する場合、値は正の整数である必要があります。  
  
 *max_trans*はキャプチャジョブに対してのみ有効です。  
  
@no__t-ログからすべての行を抽出するために実行するスキャンサイクルの最大数。 *max_scans*は**int**既定値は NULL の場合、このパラメーターに変更がないことを示します。  
  
 *max_scan*はキャプチャジョブに対してのみ有効です。  
  
`[ @continuous ] = continuous_` は、キャプチャジョブを連続的に実行するか (1)、1回だけ実行するか (0) を示します。 *continuous*は**bit**で、既定値は NULL です。これは、このパラメーターに変更がないことを示します。  
  
 *Continuous* = 1 の場合、 [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md)ジョブはログをスキャンし、最大 (*max_trans* \* *max_scans*) トランザクションを処理します。 次のログスキャンを開始する前に、 *polling_interval*で指定された秒数を待機します。  
  
 *Continuous* = 0 の場合、 **sp_cdc_scan**ジョブは、ログの最大*max_scans*スキャンを実行し、各スキャン中に最大で*max_trans*トランザクションを処理してから終了します。  
  
 **@No__t-1continuous**が1から0に変更された場合、 **@no__t 3pollinginterval**は自動的に0に設定されます。 0以外の **@no__t 1pollinginterval**に指定された値は無視されます。  
  
 **@No__t-1continuous**が省略されているか、明示的に NULL に設定されており、 **@no__t 3pollinginterval**が明示的に0よりも大きい値に設定されている場合、 **\@continuous**は自動的に1に設定されます。  
  
 *continuous*は、キャプチャジョブに対してのみ有効です。  
  
@no__t-ログスキャンサイクルの間隔を秒数で指定します。 *polling_interval*は**bigint** 、既定値は NULL の場合、このパラメーターに変更がないことを示します。  
  
 *polling_interval*は、 *continuous*が1に設定されている場合にのみ、キャプチャジョブに対して有効です。  
  
@no__t-変更行を変更テーブルに保持する時間 (分)。 *retention*は**bigint**であり、既定値は NULL です。これは、このパラメーターに変更がないことを示します。 最大値は 52494800 (100 年) です。 指定する場合、値は正の整数である必要があります。  
  
 *リテンション期間*はクリーンアップジョブに対してのみ有効です。  
  
@no__t-クリーンアップ時に1つのステートメントを使用して削除できる削除エントリの最大数。 *delete threshold*は**bigint**であり、既定値は NULL です。これは、このパラメーターに変更がないことを示します。 *削除のしきい値*は、クリーンアップジョブに対してのみ有効です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 パラメーターを省略した場合、 [dbo. cdc ジョブ](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)テーブルの関連する値は更新されません。 明示的に NULL に設定されたパラメーターは、パラメーターが省略されているかのように扱われます。  
  
 ジョブの種類に対して無効なパラメーターを指定すると、ステートメントは失敗します。  
  
 ジョブに対する変更は、 [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md)を使用してジョブを停止し、 [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)を使用して再起動するまで有効になりません。  
  
## <a name="permissions"></a>アクセス許可  
 **Db_owner**固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-a-capture-job"></a>A. キャプチャ ジョブを変更する  
 次の例では、`AdventureWorks2012` データベースのキャプチャジョブの `@job_type`、`@maxscans`、および `@maxtrans` パラメーターを更新します。 キャプチャジョブに対して有効な他のパラメーター (`@continuous` と `@pollinginterval`) は省略されています。これらの値は変更されません。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>B. クリーンアップジョブの変更  
 次の例では、`AdventureWorks2012` データベースのクリーンアップジョブを更新します。 **@No__t-1**を除く、このジョブの種類の有効なパラメーターはすべて指定されています。 **@No__t-1**の値は変更されません。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [dbo. cdc ジョブ&#40;transact-sql&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sp_cdc_enable_table &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
