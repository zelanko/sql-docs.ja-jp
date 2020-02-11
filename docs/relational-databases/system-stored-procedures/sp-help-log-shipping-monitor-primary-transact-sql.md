---
title: sp_help_log_shipping_monitor_primary (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_primary
- sp_help_log_shipping_monitor_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_primary
ms.assetid: d9dfcb8f-1da6-49ca-a2c8-411574915434
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b3f579fb9a263b69755baaa1be84f6d51e9beac1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68113843"
---
# <a name="sp_help_log_shipping_monitor_primary-transact-sql"></a>sp_help_log_shipping_monitor_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  監視テーブルからプライマリ データベースに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_log_shipping_monitor_primary  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>引数  
`[ @primary_server = ] 'primary_server'`ログ配布構成[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]におけるのプライマリインスタンスの名前。 *primary_server*は**sysname**であり、NULL にすることはできません。  
  
`[ @primary_database = ] 'primary_database'`プライマリサーバー上のデータベースの名前を指定します。 *primary_database*は**sysname**であり、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|[説明]|  
|-----------------|-----------------|  
|**primary_id**|ログ配布構成のプライマリデータベースの ID。|  
|**primary_server**|ログ配布構成における [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のプライマリ インスタンスの名前。|  
|**primary_database**|ログ配布構成のプライマリデータベースの名前。|  
|**backup_threshold**|バックアップ操作の間に、アラートが生成されるまでの経過時間 (分) です。|  
|**threshold_alert**|バックアップのしきい値を超えたときに発生するアラート。|  
|**threshold_alert_enabled**|バックアップしきい値アラートを有効にするかどうかを決定します。 1 = 有効。0 = 無効です。|  
|**last_backup_file**|最新のトランザクションログバックアップの絶対パス。|  
|**last_backup_date**|プライマリデータベースでの最後のトランザクションログバックアップ操作の日時。|  
|**last_backup_date_utc**|プライマリデータベースでの最後のトランザクションログバックアップ操作の日時。協定世界時で表されます。|  
|**history_retention_period**|指定したプライマリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>解説  
 **sp_help_log_shipping_monitor_primary**は、監視サーバーの**master**データベースから実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
