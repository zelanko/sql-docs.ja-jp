---
title: sys.dm_resource_governor_external_resource_pools (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/02/2018
ms.suite: sql
ms.prod: sql
ms.prod_service: database-engine
ms.technology: machine-learning
ms.component: dmv's
ms.reviewer: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pools_TSQL
- sys.dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_external_resource_pools
- sys.dm_resource_governor_external_resource_pools
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7a499aaa0c1377d1f64df4a5aed645c31ca3ebbf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmresourcegovernorexternalresourcepools-transact-sql"></a>sys.dm_resource_governor_external_resource_pools (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

外部リソース プールの現在の状態、リソース プール、およびリソース プール統計の現在の構成に関する情報を返します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
|Colmn 名      |データ型      |Description|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。 |
| name|**sysname**|リソース プールの名前。 NULL 値は許可されません。 
| pool_version|**int**|内部バージョン番号です。|
| max_cpu_percent|**int**|CPU の競合がある場合にリソース プールのすべての要求に許可される最大平均 CPU 帯域幅の現在の構成。 NULL 値は許可されません。 |
| max_processes|**int**|同時実行の外部プロセスの最大数。 既定値は 0 で、制限がないことを示します。 NULL 値は許可されません。|
| max_memory_percent|**int**|このリソース プールの要求で使用できる合計サーバー メモリの割合の現在の構成。 NULL 値は許可されません。 |
| statistics_start_time|**datetime**|このプールの統計がリセットされた時刻。 NULL 値は許可されません。 
| peak_memory_kb|**bigint**|彼は最大使用メモリの量、キロバイト単位でリソース プール用です。 NULL 値は許可されません。 |
| write_io_count|**int**|リソース ガバナー統計がリセットされた後に発行された書き込み IO の合計。 NULL 値は許可されません。 |
| read_io_count|**int**|リソース ガバナー統計がリセットされた後に発行された読み取り IO の合計。 NULL 値は許可されません。 |
| total_cpu_kernel_ms|**bigint**|累積 CPU ユーザー時間 (リソース ガバナー統計がリセットされた後のミリ秒単位)。 NULL 値は許可されません。 |
| total_cpu_user_ms|**bigint**|累積 CPU ユーザー時間 (リソース ガバナー統計がリセットされた後のミリ秒単位)。 NULL 値は許可されません。 |
| active_processes_count|**int**|要求した時点で実行されている外部のプロセスの数。 NULL 値は許可されません。 |

 
## <a name="permissions"></a>権限

`VIEW SERVER STATE` 権限が必要です。

## <a name="see-also"></a>参照  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
