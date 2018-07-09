---
title: sys.dm_db_rda_schema_update_status (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_schema_update_status
- sys.dm_db_rda_schema_update_status_TSQL
- dm_db_rda_schema_update_status
- dm_db_rda_schema_update_status_TSQL
helpviewer_keywords:
- sys.dm_db_rda_schema_update_status dynamic management view
ms.assetid: 364e3caa-a7c6-4be5-a029-0b19da34de3e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbd99f97902dbbd3c097b76b1f119f400f97c6f6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420061"
---
# <a name="stretch-database---sysdmdbrdaschemaupdatestatus"></a>Stretch Database - sys.dm_db_rda_schema_update_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch 対応の各テーブルの現在のデータベースのリモート データのアーカイブ対象の各スキーマの更新タスクの 1 つの行が含まれています。 タスクは、そのタスク id によって識別されます。  
  
 **dm_db_rda_schema_update_status**スコープは現在のデータベース コンテキストに設定します。 Stretch が有効なテーブルのスキーマの更新プログラムの状態を参照してください。 対象となるは、データベース コンテキストを使用していることを確認します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|リモートのデータが含まれるスキーマをアーカイブするローカルの拡張が有効なテーブルの ID を更新しています。|  
|**database_id**|**int**|ローカルの拡張が有効なテーブルが含まれているデータベースの ID。|  
|**task_id**|**bigint**|リモート データ アーカイブのスキーマの更新タスクの ID。|  
|**task_type**|**int**|リモート データ アーカイブのスキーマの更新タスクの型。|  
|**task_type_desc**|**nvarchar**|リモート データ アーカイブのスキーマの更新タスクの種類の説明。|  
|**task_state**|**int**|リモート データ アーカイブのスキーマの更新タスクの状態。|  
|**task_state_des**|**nvarchar**|リモート データ アーカイブのスキーマの更新タスクの状態の説明。|  
|**start_time_utc**|**datetime**|リモートのデータが開始されたスキーマの更新をアーカイブを UTC 時刻。|  
|**end_time_utc**|**datetime**|リモートのデータがスキーマの更新をアーカイブする UTC 時刻が完了しました。|  
|**error_number**|**int**|リモート データのアーカイブ スキーマの更新が失敗した場合は、エラーが発生するエラー数それ以外の場合は null です。|  
|**error_severity**|**int**|リモート データのアーカイブ スキーマの更新が失敗した場合は、エラーが発生の重要度それ以外の場合は null です。|  
|**error_state**|**int**|リモート データのアーカイブ スキーマの更新が失敗した場合は、エラーが発生の状態それ以外の場合は null です。 Error_state は、条件またはエラーが発生した場所を示します。|  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
