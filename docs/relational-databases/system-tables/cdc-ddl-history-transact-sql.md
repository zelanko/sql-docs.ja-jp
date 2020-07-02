---
title: cdc. ddl_history (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.ddl_history_TSQL
- cdc.ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.ddl_history
ms.assetid: cb97ea71-da2f-441a-bbd2-db1f5f48ab49
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f94e292f9376abe583cc16ecef93437192d9568d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758703"
---
# <a name="cdcddl_history-transact-sql"></a>cdc. ddl_history (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  変更データ キャプチャが有効になっているテーブルに対して行われたデータ定義言語 (DDL) の変更について、各変更に対応する 1 行を返します。 このテーブルでは、ソース テーブルに対して、いつ、どのような DDL の変更が行われたかを確認できます。 DDL が変更されていないソーステーブルには、このテーブルのエントリはありません。  
  
 システムテーブルに対して直接クエリを実行しないことをお勧めします。 代わりに、 [sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)ストアドプロシージャを実行します。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**source_object_id**|**int**|DDL の変更が適用されたソーステーブルの ID。|  
|**object_id**|**int**|ソーステーブルのキャプチャインスタンスに関連付けられている変更テーブルの ID。|  
|**required_column_update**|**bit**|ソース テーブルのキャプチャ対象列のデータ型が変更されたことを示します。 この変更により、変更テーブルの列が変更されています。|  
|**ddl_command**|**nvarchar(max)**|ソーステーブルに適用される DDL ステートメントです。|  
|**ddl_lsn**|**binary(10)**|DDL 変更のコミットメントに関連付けられているログシーケンス番号 (LSN)。|  
|**ddl_time**|**datetime**|DDL の変更がソーステーブルに対して行われた日付と時刻。|  
  
## <a name="see-also"></a>関連項目  
 [sp_cdc_help_change_data_capture &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [cdc. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-sql&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
