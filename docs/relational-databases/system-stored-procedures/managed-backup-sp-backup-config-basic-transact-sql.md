---
title: managed_backup.sp_backup_config_basic (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d09fa38377910c2960b43eb6534dba4546538b4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942113"
---
# <a name="managedbackupspbackupconfigbasic-transact-sql"></a>managed_backup.sp_backup_config_basic (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  構成、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]特定のデータベースまたはインスタンスの基本設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
> [!NOTE]  
>  この手順は呼び出せますで基本的なマネージ バックアップの構成を作成するための独自です。 ただし、高度な機能またはカスタム スケジュールを追加する場合は、まずこれらの設定を使用して[managed_backup.sp_backup_config_advanced &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)と[managed_backup.sp_backup_config_schedule &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)からこの手順でマネージ バックアップを有効にします。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```Transact-SQL   
EXEC managed_backup.sp_backup_config_basic  
    [@enable_backup = ] { 0 | 1}    ,[@database_name = ] 'database_name'    ,[@container_url = ] 'Azure_Storage_blob_container  
    ,[@retention_days = ] 'retention_period_in_days'    ,[@credential_name = ] 'sql_credential_name'  
```  
  
##  <a name="Arguments"></a> 引数  
 @enable_backup  
 指定したデータベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効または無効にします。 @enable_backupは **ビット** します。 パラメーターを構成するときに必要な[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の最初のインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 変更する場合は、既存[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成では、このパラメーターは省略可能です。 その場合は、指定されていない、構成値は、既存の値を保持します。  
  
 @database_name  
 特定のデータベースでマネージ バックアップを有効にするためのデータベース名。  
  
 @container_url  
 バックアップの場所を示す URL。 ときに@credential_nameが null の場合、この URL は、Azure Storage に blob コンテナーに shared access signature (SAS) URL と、バックアップは、ブロック blob の機能に新しいバックアップを使用します。 詳細についてを参照してください[について SAS](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/)します。 ときに@credential_nameこれは、ストレージ アカウントの URL と、バックアップ ページ blob の機能を非推奨のバックアップを使用して、指定します。  
  
> [!NOTE]  
>  SAS URL のみがこの時点でこのパラメーターのサポートします。  
  
 @retention_days  
 バックアップ ファイルの保有期間 (日数)。 @storage_urlは INT です。 構成するときにこのパラメーターが必要なパラメーター[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]のインスタンスで初めて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 変更中に、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成では、このパラメーターは省略可能です。 指定しない場合は、既存の構成値が保持されます。  
  
 @credential_name  
 Windows Azure ストレージ アカウントを認証するために使用する SQL 資格情報の名前。 @credentail_name **SYSNAME**します。 指定した場合、バックアップ ページ blob に格納されます。 このパラメーターが NULL の場合、バックアップは、ブロック blob として格納されます。 ページ blob へのバックアップは推奨されていませんので、新しいブロック blob のバックアップ機能を使用することが推奨されます。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] の構成を変更するために使用する場合、このパラメーターは省略可能です。 指定しない場合、既存の構成値は保持されます。  
  
> [!WARNING]
>  **\@credential_name** パラメーターは、この時点ではサポートされていません。 ブロック blob のみのバックアップはサポートされて、このパラメーターを NULL にする必要があります。  
  
## <a name="return-code-value"></a>リターン コード値  
 0 (成功) または 1 (失敗)  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および**EXECUTE**に対する**sp_deletebackuphistory**ストアド プロシージャ。  
  
## <a name="examples"></a>使用例  
 ストレージ アカウントのコンテナーと SAS URL の両方を作成するには、最新の Azure PowerShell コマンドを使用します。 次の例では、mystorageaccount のストレージ アカウントで、mycontainer、新しいコンテナーを作成し、その完全なアクセス許可を持つ SAS URL を取得します。  
  
```powershell  
$context = New-AzureStorageContext -StorageAccountName mystorageaccount -StorageAccountKey (Get-AzureStorageKey -StorageAccountName mystorageaccount).Primary  
New-AzureStorageContainer -Name mycontainer -Context $context  
New-AzureStorageContainerSASToken -Name mycontainer -Permission rwdl -FullUri -Context $context  
```  
  
 次の例で[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]実行されている、SQL Server のインスタンスでは、30 日間に、保有ポリシーを設定、送信先を 'mycontainer' でストレージ アカウント"mystorageaccount"をという名前をという名前のコンテナーに設定します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [managed_backup.sp_backup_config_advanced &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
