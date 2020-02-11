---
title: managed_backup。 sp_backup_config_advanced (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cbbbfbf442d36a5f78771e4d097888a86b441065
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942142"
---
# <a name="managed_backupsp_backup_config_advanced-transact-sql"></a>managed_backup。 sp_backup_config_advanced (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  の詳細設定を[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成します。  
  
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
  
##  <a name="Arguments"></a>数値  
 @database_name  
 特定のデータベースでマネージバックアップを有効にするためのデータベース名。 NULL または * の場合、このマネージバックアップはサーバー上のすべてのデータベースに適用されます。  
  
 @encryption_algorithm  
 バックアップ中にバックアップファイルを暗号化するために使用される暗号化アルゴリズムの名前。 @encryption_algorithmは**SYSNAME**です。 データベースに対して初めて [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成する場合の必須パラメーターです。 バックアップファイルを暗号化しない場合は、 **NO_ENCRYPTION**を指定します。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成設定を変更する場合、このパラメーターは省略可能です。パラメーターが指定されていない場合は、既存の構成値が保持されます。 このパラメーターに指定できる値は次のとおりです。  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 暗号化アルゴリズムの詳細については、「 [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)」をご覧ください。  
  
 @encryptor_type  
 暗号化機能の種類。 "CERTIFICATE" または "ASYMMETRIC_KEY" のいずれかになります。 @encryptor_typeは**nvarchar (32)** です。 パラメーターに NO_ENCRYPTION を指定した場合、 @encryption_algorithmこのパラメーターは省略可能です。  
  
 @encryptor_name  
 バックアップの暗号化に使用する既存の証明書または非対称キーの名前。 @encryptor_nameは**SYSNAME**です。 非対称キーを使用する場合は、拡張キー管理 (EKM) を使用して構成する必要があります。 パラメーターに NO_ENCRYPTION を指定した場合、 @encryption_algorithmこのパラメーターは省略可能です。  
  
 詳しくは、「[拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)」をご覧ください。  
  
 @local_cache_path  
 このパラメーターは、まだサポートされていません。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 **Db_backupoperator**データベースロールのメンバーシップ、 **ALTER ANY CREDENTIAL**権限、および**Sp_delete_backuphistory**ストアドプロシージャに対する**EXECUTE**権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、SQL Server の[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]インスタンスのの詳細な構成オプションを設定します。  
  
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
 [managed_backup。 sp_backup_config_basic (Transact-sql)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup sp_backup_config_schedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
