---
title: sys.sp_cdc_drop_job (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_drop_job_TSQL
- sp_cdc_drop_job_TSQL
- sp_cdc_drop_job
- sys.sp_cdc_drop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_drop_job
ms.assetid: e8265846-8051-4848-b28e-fac27c10bdeb
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3c9f5df44d98e28dcd261a01002451a206f6fee5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysspcdcdropjob-transact-sql"></a>sys.sp_cdc_drop_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  msdb から、現在のデータベースの変更データ キャプチャ機能のクリーンアップ ジョブまたはキャプチャ ジョブを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_drop_job [ [ @job_type = ] 'job_type' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @job_type **=** ] '*job_type*'  
 削除するジョブの種類を指定します。 *job_type*は**nvarchar (20)** NULL にすることはできません。 有効な入力値は 'capture' と 'cleanup' です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 Nones  
  
## <a name="remarks"></a>解説  
 sp_cdc_drop_job はによって内部的に呼び出されます[sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)です。  
  
## <a name="permissions"></a>権限  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`AdventureWorks2012` データベースのクリーンアップ ジョブを削除します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_drop_job @job_type = N'cleanup';  
```  
  
## <a name="see-also"></a>参照  
 [dbo.cdc_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_disable_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)   
 [sys.sp_cdc_add_job & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
