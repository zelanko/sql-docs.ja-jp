---
title: managed_backup.fn_backup_db_config (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_backup_db_config
- smart_admin.fn_backup_db_config_TSQL
- fn_backup_db_config
- fn_backup_db_config_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_db_config
- fn_backup_db_config
ms.assetid: 7c755d8a-64dd-44b2-be5e-735d30758900
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ae0d84ba18a350adb47ca9a9aeeaf966a90af2a8
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52409579"
---
# <a name="managedbackupfnbackupdbconfig-transact-sql"></a>managed_backup.fn_backup_db_config (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成設定を含む 0 行または 1 行以上の行を返します。 指定されたデータベースに対して 1 行を返すか、インスタンス上で [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]によって構成されたすべてのデータベースの情報を返します。  
  
 このストアド プロシージャを使用すると、SQL Server のインスタンス上の特定のデータベースまたはすべてのデータベースの現在の [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成設定を確認または決定することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_backup_db_config ('database_name' | '' | NULL)  
```  
  
##  <a name="Arguments"></a> 引数  
 @db_name  
 データベースの名前。 @db_nameパラメーターが**SYSNAME**します。 このパラメーターに空の文字列または NULL 値が渡されると、SQL Server のインスタンス上にあるすべてのデータベースに関する情報が返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|db_name|SYSNAME|データベース名。|  
|db_guid|UNIQUEIDENTIFIER|データベースを一意に識別する識別子。|  
|is_availability_database|BIT|データベースが可用性グループに参加しているかどうか。 値が 1 の場合は、データベースが可用性データベースであることを示します。0 の場合は、可用性データベースではないことを示します。|  
|is_dropped|BIT|値が 1 の場合は、削除されたデータベースであることを示します。|  
|credential_name|SYSNAME|ストレージ アカウントへの認証に使用された SQL 資格情報の名前。 NULL 値は、SQL 資格情報が設定されていないことを示します。|  
|retention_days|INT|現在の保有期間 (日数)。 NULL 値は、このデータベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が構成されていないことを示します。|  
|is_managed_backup_enabled|INT|このデータベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が現在有効になっているかどうかを示します。 値が 1 の場合は、このデータベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が現在有効であることを示します。0 の場合は、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が無効であることを示します。|  
|storage_url|NVARCHAR (1024)|ストレージ アカウントの URL。|  
|Encryption_algorithm|NCHAR (20) 型|バックアップを暗号化するときに使用する、現在の暗号化アルゴリズムを返します。|  
|Encryptor_type|NCHAR(15)|暗号化機能の設定が返されます。証明書キーまたは非対称キー。|  
|Encryptor_name|NCHAR(max_length_of_cert/asymm_key_name)|証明書または非対称キーの名前。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_backupoperator**を持つデータベース ロール**ALTER ANY CREDENTIAL**アクセス許可。 ユーザーが拒否されていない必要があります**VIEW ANY DEFINITION**アクセス許可。  
  
## <a name="examples"></a>使用例  
 次の例を返します、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 'TestDB' の構成  
  
 各コードでは、言語属性フィールドで "tsql" を選択します。  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config('TestDB')  
```  
  
 次の例では、実行されている SQL Server のインスタンス上にあるすべてのデータベースの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成が返されます。  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL)  
```  
  
  
