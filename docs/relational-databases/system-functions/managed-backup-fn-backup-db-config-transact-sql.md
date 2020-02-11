---
title: managed_backup。 fn_backup_db_config (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: a23f8eb64ae99b999cdf6b16f1c888383a88c147
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067778"
---
# <a name="managed_backupfn_backup_db_config-transact-sql"></a>managed_backup。 fn_backup_db_config (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  構成設定が指定された[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 0 行、1行、または複数の行を返します。 指定されたデータベースに対して 1 行を返すか、インスタンス上で [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]によって構成されたすべてのデータベースの情報を返します。  
  
 このストアド プロシージャを使用すると、SQL Server のインスタンス上の特定のデータベースまたはすべてのデータベースの現在の [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成設定を確認または決定することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_backup_db_config ('database_name' | '' | NULL)  
```  
  
##  <a name="Arguments"></a>数値  
 @db_name  
 データベースの名前。 @db_nameパラメーターは**SYSNAME**です。 このパラメーターに空の文字列または NULL 値が渡されると、SQL Server のインスタンス上にあるすべてのデータベースに関する情報が返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|db_name|SYSNAME|データベース名。|  
|db_guid|一意|データベースを一意に識別する識別子。|  
|is_availability_database|BIT|データベースが可用性グループに参加しているかどうか。 値が1の場合は、データベースが可用性データベースであることを示し、それ以外の場合は0を示します。|  
|is_dropped|BIT|値1は、これが削除されたデータベースであることを示します。|  
|credential_name|SYSNAME|ストレージ アカウントへの認証に使用された SQL 資格情報の名前。 NULL 値は、SQL 資格情報が設定されていないことを示します。|  
|retention_days|INT|現在の保有期間 (日数)。 NULL 値は、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]このデータベースに対してが構成されていないことを示します。|  
|is_managed_backup_enabled|INT|このデータベース[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]に対してが現在有効になっているかどうかを示します。 値1は、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が現在有効になっていることを示し、値 0 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]は、がこのデータベースで無効になっていることを示します。|  
|storage_url|NVARCHAR (1024)|ストレージ アカウントの URL。|  
|Encryption_algorithm|NCHAR (20)|バックアップを暗号化するときに使用する現在の暗号化アルゴリズムを返します。|  
|Encryptor_type|NCHAR (15)|暗号化機能の設定 (証明書または非対称キー) を返します。|  
|Encryptor_name|NCHAR(max_length_of_cert/asymm_key_name)|証明書または非対称キーの名前。|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 **ALTER ANY CREDENTIAL**権限を持つ**db_backupoperator**データベースロールのメンバーシップが必要です。 ユーザーは、 **VIEW ANY DEFINITION**権限を拒否することはできません。  
  
## <a name="examples"></a>例  
 次の例では[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 、' TestDB ' の構成を返します。  
  
 各コードでは、言語属性フィールドで "tsql" を選択します。  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config('TestDB')  
```  
  
 次の例では[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 、実行 SQL Server のインスタンス上にあるすべてのデータベースの構成を返します。  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL)  
```  
  
  
