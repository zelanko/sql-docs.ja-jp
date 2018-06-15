---
title: managed_backup.sp_backup_config_advanced (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_backup_config_optional
- sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional
dev_langs:
- TSQL
helpviewer_keywords:
- sp_backup_config_optional
- managed_backup.sp_backup_config_optional
ms.assetid: 4fae8193-1f88-48fd-a94a-4786efe8d6af
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 08c79b906a95c41013f28a559acdc7f98809c186
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238226"
---
# <a name="managedbackupspbackupconfigadvanced-transact-sql"></a>managed_backup.sp_backup_config_advanced (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  高度な設定を構成[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```vb  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="Arguments"></a> 引数  
 @database_name  
 有効にするためのデータベース名は、特定のデータベースでのバックアップを管理します。 NULL の場合、または *、し、この管理対象のバックアップは、サーバー上のすべてのデータベースに適用します。  
  
 @encryption_algorithm  
 バックアップ中にバックアップ ファイルの暗号化に使用する暗号化アルゴリズムの名前。 @encryption_algorithmは**SYSNAME**です。 データベースに対して初めて [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成する場合の必須パラメーターです。 指定**NO_ENCRYPTION**バックアップ ファイルを暗号化したくない場合。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] の構成設定を変更する場合、このパラメーターは省略可能です。パラメーターを指定しない場合は、既存の構成値が保持されます。 このパラメーターで許可される値は次のとおりです。  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 暗号化アルゴリズムの詳細については、「 [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)」をご覧ください。  
  
 @encryptor_type  
 '証明書' を指定できますが、暗号化機能の型または ' ASYMMETRIC_KEY"です。 @encryptor_typeは**nvarchar (32)** です。 このパラメーターは省略可能の NO_ENCRYPTION を指定する場合、@encryption_algorithmパラメーター。  
  
 @encryptor_name  
 バックアップの暗号化に使用する既存の証明書または非対称キーの名前。 @encryptor_nameは**SYSNAME**です。 非対称キーを使用する場合は、拡張キー管理 (EKM) を使用して構成する必要があります。 このパラメーターは省略可能の NO_ENCRYPTION を指定する場合、@encryption_algorithmパラメーター。  
  
 詳しくは、「[拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)」をご覧ください。  
  
 @local_cache_path  
 このパラメーターはまだサポートされていません。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 メンバーシップが必要**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対するアクセス許可**sp_deletebackuphistory**ストアド プロシージャです。  
  
## <a name="examples"></a>使用例  
 次の例は、高度な構成オプションを設定[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]SQL Server のインスタンス。  
  
```  
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>参照  
 [managed_backup.sp_backup_config_basic (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
