---
title: managed_backup.sp_backup_config_basic (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/03/2016
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
- sp_backup_config_basic_TSQL
- sp_backup_config_basic
- managed_backup.sp_backup_config_basic
- managed_backup.sp_backup_config_basic_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_basic
- sp_backup_config_basic
ms.assetid: 3ad73051-ae9a-4e41-a889-166146e5508f
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9a84640449375852f4a618afb1c1282401e784be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="managedbackupspbackupconfigbasic-transact-sql"></a>managed_backup.sp_backup_config_basic (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  構成、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]基本設定の特定のデータベースまたはのインスタンスに対して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  この手順呼び出せるで基本的なマネージ バックアップの構成を作成するための独自です。 ただし、高度な機能またはカスタム スケジュールを追加する場合は、最初の構成を使用してこれらの設定[managed_backup.sp_backup_config_advanced &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)と[managed_backup.sp_backup_config_schedule &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)この手順でマネージ バックアップを有効にしてください。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> 引数  
 @enable_backup  
 指定したデータベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効または無効にします。 @enable_backupは**ビット**です。 パラメーターを構成するときに必要な[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の最初のインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 変更する場合は、既存[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成では、このパラメーターは省略可能です。 その場合は、指定されていないすべての構成値は、既存の値を保持します。  
  
 @database_name  
 有効にするためのデータベース名は、特定のデータベースでのバックアップを管理します。  
  
 @container_url  
 バックアップの場所を示す URL です。 ときに@credential_nameが NULL の場合、この URL は、Azure Storage の blob コンテナーへの共有アクセス署名 (SAS) URL と、バックアップは、ブロック blob の機能に新しいバックアップを使用します。 詳細については、「[について SAS](http://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/)です。 ときに@credential_nameが指定されている、これは、ストレージ アカウントの URL と、バックアップは、ページ blob の機能を非推奨のバックアップを使用します。  
  
> [!NOTE]  
>  この時点でこのパラメーターの SAS URL のみがサポートされてです。  
  
 @retention_days  
 バックアップ ファイルの保有期間 (日数)。 @storage_urlは int です。 これは、構成する場合の必須パラメーター[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]のインスタンスで最初に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 変更中に、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成では、このパラメーターは省略可能です。 指定しない場合は、既存の構成値が保持されます。  
  
 @credential_name  
 Windows Azure ストレージ アカウントへの認証に使用する SQL 資格情報の名前。 @credentail_name **SYSNAME**です。 指定した場合、バックアップは、ページ blob に格納されます。 このパラメーターが NULL の場合、バックアップは、ブロック blob として格納されます。 ページ blob へのバックアップには非推奨とされているので、新しいブロック blob のバックアップ機能を使用することをお勧めします。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] の構成を変更するために使用する場合、このパラメーターは省略可能です。 指定しない場合、既存の構成値は保持されます。  
  
> [!WARNING]  
>  **@credential_name**パラメーターは、この時点ではサポートされません。 ブロック blob のみのバックアップはサポートされて、このパラメーターを NULL にする必要があります。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 メンバーシップが必要**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対するアクセス許可**sp_deletebackuphistory**ストアド プロシージャです。  
  
## <a name="examples"></a>使用例  
 ストレージ アカウントのコンテナーと SAS URL の両方を作成するには、最新の Azure PowerShell のコマンドを使用します。 次の例では、mystorageaccount のストレージ アカウントに、mycontainer、新しいコンテナーを作成しに完全なアクセス許可と SAS URL を取得します。  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 次の例では、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]で実行された SQL Server のインスタンスは、30 日間に、保有ポリシーを設定、送信先を 'mycontainer' でストレージ アカウント"mystorageaccount"をという名前をという名前のコンテナーに設定します。  
  
```Transact-SQL 
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=1  
                ,@container_url = 'https://mystorageaccount.blob.core.windows.net/mycontainer'  
                ,@retention_days=30;   
GO  
  
```
  
 次に、実行されている SQL Server インスタンスに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] を無効にする例を示します。  
  
```Transact-SQL  
Use msdb;  
Go  
EXEC managed_backup.sp_backup_config_basic  
                @enable_backup=0;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [managed_backup.sp_backup_config_advanced &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
