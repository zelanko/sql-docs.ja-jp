---
title: cdc.ddl_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.ddl_history_TSQL
- cdc.ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.ddl_history
ms.assetid: cb97ea71-da2f-441a-bbd2-db1f5f48ab49
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08d05d0f9064db1a536bd53e7ab2552eecda7080
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101640"
---
# <a name="cdcddlhistory-transact-sql"></a>cdc.ddl_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更データ キャプチャが有効になっているテーブルに対して行われたデータ定義言語 (DDL) の変更について、各変更に対応する 1 行を返します。 このテーブルでは、ソース テーブルに対して、いつ、どのような DDL の変更が行われたかを確認できます。 このテーブルに含まれるのは、DDL が変更されているソース テーブルのエントリだけです。  
  
 システム テーブルに対して直接クエリを実行することは、できるだけ避けてください。 代わりに、実行、 [sys.sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)ストアド プロシージャ。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**source_object_id**|**int**|DDL の変更が適用されたソース テーブルの ID です。|  
|**object_id**|**int**|ソース テーブルのキャプチャ インスタンスに関連付けられた変更テーブルの ID です。|  
|**required_column_update**|**bit**|ソース テーブルのキャプチャ対象列のデータ型が変更されたことを示します。 この変更により、変更テーブル内の列が更新されています。|  
|**ddl_command**|**nvarchar(max)**|DDL ステートメントは、ソース テーブルに適用します。|  
|**ddl_lsn**|**binary(10)**|DDL 修正のコミットに関連付けられたログ シーケンス番号 (LSN) です。|  
|**ddl_time**|**datetime**|ソース テーブルに対して DDL の変更が加えられた日時です。|  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_help_change_data_capture &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
