---
title: dm_db_rda_migration_status (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 21e5230e4f3efd86fe90382202f0b21a0187a214
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67937062"
---
# <a name="stretch-database---sysdm_db_rda_migration_status"></a>Stretch Database-sys. dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルインスタンス上の各 Stretch が有効なテーブルから、移行されたデータのバッチごとに1行のデータを格納します。 バッチは、開始時刻と終了時刻によって識別されます。  
  
 **dm_db_rda_migration_status**は、現在のデータベースコンテキストにスコープが設定されています。 移行の状態を確認する Stretch enable テーブルのデータベースコンテキストを使用していることを確認します。  
  
 で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]は、 **dm_db_rda_migration_status**の出力は200行に制限されています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|行が移行されたテーブルの ID。|  
|**database_id**|**int**|行が移行されたデータベースの ID。|  
|**migrated_rows**|**bigint**|このバッチで移行された行の数。|  
|**start_time_utc**|**datetime**|バッチが開始された UTC 時刻。|  
|**end_time_utc**|**datetime**|バッチが終了した UTC 時刻。|  
|**error_number**|**int**|バッチが失敗した場合は、発生したエラーのエラー番号。それ以外の場合は null。|  
|**error_severity**|**int**|バッチが失敗した場合、発生したエラーの重大度。それ以外の場合は null。|  
|**error_state**|**int**|バッチが失敗した場合、発生したエラーの状態。それ以外の場合は null。<br /><br /> **Error_state**は、エラーが発生した条件または場所を示します。|  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
