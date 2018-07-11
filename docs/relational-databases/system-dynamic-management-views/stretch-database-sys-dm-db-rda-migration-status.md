---
title: sys.dm_db_rda_migration_status (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0ee1d106a9f52dd30518f9ead02847dc879ff2c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422471"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - sys.dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  ローカル インスタンス上のそれぞれの Stretch 対応テーブルから移行されたデータのバッチごとの 1 つの行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 バッチは、開始時刻と終了時刻によって識別されます。  
  
 **sys.dm_db_rda_migration_status**スコープは現在のデータベース コンテキストに設定します。 移行の状態を表示する拡張を有効にするテーブルのデータベースのコンテキストであることを確認してください。  
  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の出力**sys.dm_db_rda_migration_status** 200 行に制限されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|テーブルの行が移行された元の ID です。|  
|**database_id**|**int**|行が移行されたデータベースの ID です。|  
|**migrated_rows**|**bigint**|行の数は、このバッチで移行します。|  
|**start_time_utc**|**datetime**|バッチが開始された UTC 時刻。|  
|**end_time_utc**|**datetime**|バッチの終了を UTC 時刻。|  
|**error_number**|**int**|バッチが失敗した場合は、エラーが発生するエラー数それ以外の場合は null です。|  
|**error_severity**|**int**|バッチが失敗した場合は、エラーが発生の重要度それ以外の場合は null です。|  
|**error_state**|**int**|バッチが失敗した場合は、エラーが発生の状態それ以外の場合は null です。<br /><br /> **Error_state**条件またはエラーが発生した場所を示します。|  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
