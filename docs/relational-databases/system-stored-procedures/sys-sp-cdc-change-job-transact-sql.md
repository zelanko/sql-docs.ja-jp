---
title: sys.sp_cdc_change_job (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: f2aa4413bd9f226bd0bbdf5b676da0da866fde32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705860"
---
# <a name="sysspcdcchangejob-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに、変更データ キャプチャ機能のクリーンアップ ジョブまたはキャプチャ ジョブの構成を変更します。 ジョブの現在の構成を表示するには、クエリ、 [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)テーブル、または使用[sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)します。  
  
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
 [  **@job_type=** ] **'***job_type***'**  
 変更するジョブの種類を指定します。 *job_type*は**nvarchar (20)** 既定値は 'capture' です。 有効な入力値は 'capture' と 'cleanup' です。  
  
 [ **@maxtrans** ] **= * * * max_trans*  
 各スキャン サイクルで処理する最大トランザクション数を指定します。 *max_trans*は**int**既定値は NULL でないことを示しますこのパラメーターに変更します。 指定する場合、値は正の整数にする必要があります。  
  
 *max_trans*はキャプチャ ジョブでのみ有効です。  
  
 [ **@maxscans** ] **= * * * max_scans*  
 ログからすべての行を抽出するために実行する最大スキャン サイクル数を指定します。 *max_scans*は**int**既定値は NULL でないことを示しますこのパラメーターに変更します。  
  
 *max_scan*はキャプチャ ジョブでのみ有効です。  
  
 [ **@continuous** ] **= * * * 継続的な*  
 キャプチャ ジョブを連続的に実行するか (1)、1 回だけ実行するか (0) を指定します。 *継続的な*は**ビット**既定値は NULL でないことを示しますこのパラメーターに変更します。  
  
 ときに*連続*= 1、 [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md)ジョブは、ログをスキャンし、最大処理 (*max_trans* \* *max_scans*)トランザクション。 指定された秒数待機し、 *polling_interval*次のログ スキャンを開始する前にします。  
  
 ときに*連続*= 0 の場合、 **sp_cdc_scan**ジョブが実行されるまで*max_scans*までの処理、ログのスキャン*max_trans*トランザクション中に各スキャン、およびし終了します。  
  
 場合**@continuous** 1 から 0 に変更が**@pollinginterval**は自動的に 0 に設定します。 指定された値**@pollinginterval**以外の 0 は無視されます。  
  
 場合**@continuous**を省略するか明示的に NULL に設定し、 **@pollinginterval**が明示的に設定する値を 0 より大きく、 **@continuous**自動的には1 に設定します。  
  
 *継続的な*はキャプチャ ジョブでのみ有効です。  
  
 [ **@pollinginterval** ] **= * * * polling_interval*  
 ログ スキャン サイクルの間隔を秒数で指定します。 *polling_interval*は**bigint**既定値は NULL でないことを示しますこのパラメーターに変更します。  
  
 *polling_interval*キャプチャに対してのみ有効ですがジョブの場合に*連続*が 1 に設定します。  
  
 [ **@retention** ] **= * * * 保有期間*  
 変更行が変更テーブルに保持される分数を指定します。 *保有期間*は**bigint**既定値は NULL でないことを示しますこのパラメーターに変更します。 最大値は 52494800 (100 年) です。 指定する場合、値は正の整数にする必要があります。  
  
 *保有期間*はクリーンアップ ジョブでのみ有効です。  
  
 [  **@threshold=** ] **'***しきい値を削除***'**  
 クリーンアップ時に 1 つのステートメントを使用して削除できる最大削除エントリ数を指定します。 *しきい値を削除*は**bigint**既定値は NULL でないことを示しますこのパラメーターに変更します。 *しきい値を削除*はクリーンアップ ジョブでのみ有効です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 パラメーターを省略すると、関連する値で、 [dbo.cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)テーブルが更新されません。 明示的に NULL が設定されたパラメーターは、省略されたものとして扱われます。  
  
 指定したパラメーターが、そのジョブの種類では無効であった場合、ステートメントでエラーが発生します。  
  
 使用して、ジョブが停止されるまで、ジョブへの変更は有効になりません[sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md)で再開[sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-a-capture-job"></a>A. キャプチャ ジョブを変更する  
 次の例の更新プログラム、 `@job_type`、 `@maxscans`、および`@maxtrans`でキャプチャ ジョブのパラメーター、`AdventureWorks2012`データベース。 キャプチャ ジョブでは、その他の有効なパラメーター`@continuous`と`@pollinginterval`、省略しています。 その値は変更されません。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>B. クリーンアップ ジョブを変更する  
 次の例のクリーンアップ ジョブの更新、`AdventureWorks2012`データベース。 この有効なパラメーターをすべてのジョブ以外の種類、  **@threshold**が指定されています。 値**@threshold**は変更されません。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [dbo.cdc_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_enable_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
