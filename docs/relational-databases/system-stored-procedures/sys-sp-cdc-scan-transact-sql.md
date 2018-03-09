---
title: "sys.sp_cdc_scan (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8cd29ff4ce371f6d893ceb396bb3a69d20bcab2
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcscan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更データ キャプチャのログ スキャン操作を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@maxtrans=** ] *max_trans*  
 各スキャン サイクルで処理する最大トランザクション数を指定します。 *max_trans*は**int**既定値は 500 です。  
  
 [  **@maxscans=** ] *max_scans*  
 ログからすべての行を抽出するために実行する最大スキャン サイクル数を指定します。 *max_scans*は**int**既定値は 10 です。  
  
 [  **@continuous=** ]*連続*  
 ストアド プロシージャが単一のスキャン サイクル (0) の実行後に終了するかによって指定された時間一時停止、継続的に実行するかどうかを示す*polling_interval*してスキャン サイクル (1) の前にします。 *継続的な*は**tinyint**既定値は 0 です。  
  
 [  **@pollinginterval=** ] *polling_interval*  
 ログ スキャン サイクルの間隔を秒数で指定します。 *polling_interval*は**bigint**既定値は 0 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのキャプチャ ジョブが変更データ キャプチャによって使用されている場合、sys.sp_cdc_scan は sys.sp_MScdc_capture_job によって内部的に呼び出されます。 変更データ キャプチャのログ スキャン操作が既にアクティブである場合、またはデータベースのトランザクション レプリケーションが有効になっている場合は、プロシージャは明示的に実行できません。 自動的に構成されているキャプチャ ジョブの動作をカスタマイズする管理者向けでは、このストアド プロシージャを使用してください。  
  
## <a name="permissions"></a>Permissions  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [dbo.cdc_jobs &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
