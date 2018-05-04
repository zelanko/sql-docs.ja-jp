---
title: 変更データ キャプチャ ストアド プロシージャ (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system stored procedures [SQL Server], change data capture
- change data capture [SQL Server], stored procedures
ms.assetid: 7da7068d-6388-465a-b708-a2f27ded1efe
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9f86f5572f837c1203901980f1c74290d15aa5be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="change-data-capture-stored-procedures-transact-sql"></a>変更データ キャプチャ ストアド プロシージャ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更データ キャプチャにより、有効なテーブルで実行されたデータ操作言語 (DML) 利用状況の履歴レコードを、便利なリレーショナル形式で使用できます。 次のストアド プロシージャを使用して、変更データ キャプチャの構成、変更データ キャプチャのエージェント ジョブの管理、および変更データ コンシューマーへの現在のメタデータの提供を実行できます。  
  
|||  
|-|-|  
|[sys.sp_cdc_add_job & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)|[sys.sp_cdc_generate_wrapper_function &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)|  
|[sys.sp_cdc_change_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)|[sys.sp_cdc_get_captured_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)|  
|[sys.sp_cdc_cleanup_change_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-cleanup-change-table-transact-sql.md)|[sys.sp_cdc_get_ddl_history &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)|  
|[sys.sp_cdc_disable_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)|[sys.sp_cdc_help_change_data_capture &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)|  
|[sys.sp_cdc_disable_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-table-transact-sql.md)|[sys.sp_cdc_help_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)|  
|[sys.sp_cdc_drop_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)|[sys.sp_cdc_scan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md)|  
|[sys.sp_cdc_enable_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)|[sys.sp_cdc_start_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)|  
|[sys.sp_cdc_enable_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)|[sys.sp_cdc_stop_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [変更データ キャプチャ テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)  
  
  
