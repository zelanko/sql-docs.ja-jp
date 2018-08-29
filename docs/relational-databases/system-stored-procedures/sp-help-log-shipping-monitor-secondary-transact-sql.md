---
title: sp_help_log_shipping_monitor_secondary (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_secondary
- sp_help_log_shipping_monitor_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_secondary
ms.assetid: 3ac091ea-c9a8-4c05-a0b6-1ccf4e001339
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 598f988483e3bef6ffe784f7be18145ebf1a89e5
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028006"
---
# <a name="sphelplogshippingmonitorsecondary-transact-sql"></a>sp_help_log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  監視テーブルからセカンダリ データベースに関する情報を返します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_log_shipping_monitor_secondary  
[ @secondary_server = ] 'secondary_server',  
[ @secondary_database = ] 'secondary_database'  
```  
  
## <a name="arguments"></a>引数  
 [  **@secondary_server =** ] '*secondary_server*'  
 セカンダリ サーバーの名前を指定します。 *secondary_server*は**sysname**、既定値はありません。  
  
 [  **@secondary_database =** ] '*secondary_database*'  
 セカンダリ データベースの名前を指定します。 *secondary_database*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|[列]|説明|  
|------------|-----------------|  
|**secondary_server**|セカンダリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。|  
|**secondary_database**|ログ配布構成におけるセカンダリ データベースの名前。|  
|**secondary_id**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**primary_server**|ログ配布構成における [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のプライマリ インスタンスの名前。|  
|**primary_database**|ログ配布構成におけるプライマリ データベースの名前。|  
|**restore_threshold**|復元操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。|  
|**threshold_alert**|復元のしきい値を超えたときに発生する警告。|  
|**threshold_alert_enabled**|復元のしきい値の警告を有効にするかどうか。<br /><br /> 1 = 有効にします。<br /><br /> 0 = 無効。|  
|**last_copied_file**|セカンダリ サーバーにコピーされた最後のバックアップ ファイルの名前。|  
|**last_copied_date**|セカンダリ サーバーに対して最後にコピー操作を行った日時。|  
|**last_copied_date_utc**|セカンダリ サーバーに対して最後にコピー操作を行った日時。協定世界時 (UTC) で表されます。|  
|**last_restored_file**|セカンダリ データベースに復元された最後のバックアップ ファイルの名前。|  
|**last_restored_date**|セカンダリ データベースに対して最後に復元操作を行った日時。|  
|**last_restored_date_utc**|セカンダリ データベースに対して最後に復元操作を行った日時。協定世界時 (UTC) で表されます。|  
|**history_retention_period**|指定したセカンダリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>コメント  
 **sp_help_log_shipping_monitor_secondary**から実行する必要があります、**マスター**監視サーバー上のデータベース。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="see-also"></a>関連項目  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
