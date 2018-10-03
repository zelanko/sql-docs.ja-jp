---
title: log_shipping_secondary_databases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary_databases_TSQL
- log_shipping_secondary_databases
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary_databases system table
ms.assetid: ba2374af-86b8-480c-a10c-51e7c4e3ae23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2311b37f3d804cd402715a1b9b9b1197ced78e2c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727820"
---
# <a name="logshippingsecondarydatabases-transact-sql"></a>log_shipping_secondary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各ログ配布構成内のセカンダリ データベースごとに、1 つのレコードを格納します。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**secondary_database**|**sysname**|ログ配布構成におけるセカンダリ データベースの名前。|  
|**secondary_id**|**uniqueidentifier**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**restore_delay**|**int**|指定されたバックアップ ファイルを復元するまでセカンダリ サーバーが待機する時間 (分単位)。 既定値は、0 分です。|  
|**restore_all**|**bit**|場合は、復元ジョブの実行時に、1、セカンダリ サーバーに設定はすべてのトランザクション ログ バックアップを復元します。 1 以外に設定すると、セカンダリ サーバーは 1 つのファイルが復元された後で停止します。|  
|**restore_mode**|**bit**|セカンダリ データベースの復元モードを指定します。<br /><br /> 0 = NORECOVERY でログを復元します。<br /><br /> 1 = STANDBY でログを復元します。|  
|**disconnect_users**|**bit**|かどうか 1 に設定、ユーザーが切断、セカンダリ データベースから復元操作を実行します。 既定値 = 0。|  
|**block_size**|**int**|バックアップ デバイスのブロック サイズに使用されるサイズ (バイト単位)。|  
|**buffer_count**|**int**|バックアップまたは復元操作で使用されるバッファーの総数。|  
|**max_transfer_size**|**int**|サイズをバイト単位の最大入力または出力要求によって発行された[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ デバイスにします。|  
|**last_restored_file**|**nvarchar(500)**|セカンダリ データベースに復元された最後のバックアップ ファイルの名前。|  
|**last_restored_date**|**datetime**|セカンダリ データベースに対して最後に復元操作を行った日時。|  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [log_shipping_secondary &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
