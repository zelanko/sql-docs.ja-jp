---
title: sp_help_log_shipping_monitor (TRANSACT-SQL) |Microsoft ドキュメント
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
f1_keywords:
- sp_help_log_shipping_monitor_TSQL
- sp_help_log_shipping_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor
ms.assetid: a4e96c45-6dcd-471a-a494-b5c619459855
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d48e5d889890c9ab657733aec2d564bb1c2f7eb5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelplogshippingmonitor-transact-sql"></a>sp_help_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プライマリ サーバー、セカンダリ サーバー、または監視サーバー上にあるプライマリおよびセカンダリの登録データベースに関して、状態とその他の情報を含む結果セットを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_log_shipping_monitor  
```  
  
## <a name="arguments"></a>引数  
 [なし] :  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**ステータス**|**bit**|ログ配布データベースのエージェントに関する全般的な状態。<br /><br /> **0**正常な状態でないエージェントの障害を = です。<br /><br /> **1** = それ以外の場合。|  
|**is_primary**|**bit**|この行がプライマリ データベースのものかどうか。<br /><br /> **1** = 行は、プライマリ データベースです。<br /><br /> **0** = 行は、セカンダリ データベースです。|  
|**server**|**sysname**|このデータベースが存在するプライマリまたはセカンダリ サーバーの名前。|  
|**database_name**|**sysname**|データベース名です。|  
|**time_since_last_backup**|**int**|前回のログ バックアップから経過した時間 (分単位)。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**last_backup_file**|**nvarchar(500)**|前回正常に作成されたログ バックアップ ファイルの名前。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**backup_threshold**|**int**|前回のバックアップが行われてから、threshold_alert エラーが発生するまでの期間 (分単位)。 **backup_threshold**は**int**、既定値は**60 分**です。<br /><br /> NULL = 情報が使用できないか該当しません。<br /><br /> 使用して、この値を変更することができます[sp_add_log_shipping_primary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)です。|  
|**is_backup_alert_enabled**|**bit**|アラートがあるかどうかを示す場合に発生**backup_threshold**を超過します。 いずれかの値 (**1**) で、既定値は、アラートを発行することを意味します。<br /><br /> NULL = 情報が使用できないか該当しません。<br /><br /> 使用して、この値を変更することができます[sp_add_log_shipping_primary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)です。|  
|**time_since_last_copy**|**int**|前回のログ バックアップがコピーされてから経過した時間 (分単位)。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**last_copied_file**|**nvarchar(500)**|前回正常にコピーされたログ バックアップ ファイルの名前。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**time_since_last_restore**|**int**|前回のログ バックアップが復元されてから経過した時間 (分単位)。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**last_restored_file**|**nvarchar(500).**|前回正常に復元されたログ バックアップ ファイルの名前。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**last_restored_latency**|**int**|前回バックアップを作成してから復元するまでに経過した時間 (分単位)。<br /><br /> NULL = 情報が使用できないか該当しません。|  
|**restore_threshold**|**int**|復元操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。 **restore_threshold** NULL にすることはできません。|  
|**is_restore_alert_enabled**|**bit**|アラートが発生するかどうかを指定と**restore_threshold**を超過します。 いずれかの値 (**1**) で、既定値は、アラートが発生したことを意味します。<br /><br /> NULL = 情報が使用できないか該当しません。<br /><br /> 復元のしきい値を設定するには、使用[sp_add_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)です。|  
  
## <a name="remarks"></a>解説  
 **sp_help_log_shipping_monitor**から実行する必要があります、**マスター**監視サーバー上のデータベースです。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ログ配布 & #40; についてSQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
