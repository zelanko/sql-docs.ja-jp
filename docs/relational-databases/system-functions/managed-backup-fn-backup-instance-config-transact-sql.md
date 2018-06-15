---
title: managed_backup.fn_backup_instance_config (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_backup_instance_config
- smart_admin.fn_backup_instance_config_TSQL
- fn_backup_instance_config_TSQL
- smart_admin.fn_backup_instance_config
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_instance_config
- fn_backup_instance_config
ms.assetid: 2382a547-c0c9-4e1d-87c9-d8526192eb5a
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4dae80911e6508a1a398cf208300bf4145faeecc
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229996"
---
# <a name="managedbackupfnbackupinstanceconfig-transact-sql"></a>managed_backup.fn_backup_instance_config (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  SQL Server インスタンスを対象とした、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の既定の構成設定を含む行を 1 つ返します。  
  
 このストアド プロシージャを使用して、確認または現在を決定するを[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]既定の SQL Server のインスタンスの構成設定。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_backup_db_config ()  
```  
  
##  <a name="Arguments"></a> 引数  
 なし  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|is_smart_backup_enabled|INT|1 の場合に表示されます[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が有効な場合は 0 と[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]は無効になります。|  
|credential_name|SYSNAME|ストレージへの認証に使用された既定の SQL 資格情報。|  
|retention_days|INT|インスタンス レベルで設定されている既定の保有期間。|  
|storage_url|NVARCHAR (1024)|インスタンス レベルで設定されている既定のストレージ アカウントの URL。|  
|encryption_algorithm|SYSNAME|暗号化アルゴリズムの名前。 暗号化が指定されていない場合は、NULL に設定されます。|  
|encryptor_type|NVARCHAR (32)|使用される暗号化機能の種類 (証明書または非対称キー)。 暗号化機能が指定されていない場合は、NULL に設定されます。|  
|encryptor_name|SYSNAME|証明書または非対称キーの名前。 名前が指定されていない場合は、NULL に設定されます。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 メンバーシップが必要、 **db_backupoperator**を持つデータベース ロール**ALTER ANY CREDENTIAL**アクセス許可。 ユーザーが拒否されていない必要があります**VIEW ANY DEFINITION**アクセス許可。  
  
## <a name="examples"></a>使用例  
 次の例を返します、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の既定の構成設定インスタンス上で実行されます。  
  
```  
Use msdb;  
GO  
SELECT * FROM managed_backup.fn_backup_instance_config ();  
  
```  
  
  
