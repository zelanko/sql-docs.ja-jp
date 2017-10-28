---
title: "PowerShell: 自分の Azure Key Vault キーを使用して TDE を有効にする | Microsoft Docs"
description: "PowerShell を使用して保存時の暗号化に Transparent Data Encryption (TDE) の使用を開始するように、Azure SQL Database と Data Warehouse を構成する方法について説明します。"
keywords: 
services: sql-database
documentationcenter: 
author: becczhang
manager: jhubbard
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: Inactive
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.translationtype: HT
ms.sourcegitcommit: 46b16dcf147dbd863eec0330e87511b4ced6c4ce
ms.openlocfilehash: cf8f46ab01c08e68fa22f65a4f86f4ff16f16ba3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---


# <a name="powershell-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vault"></a>PowerShell: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

この操作方法ガイドでは、SQL Database または Data Warehouse で Transparent Data Encryption (TDE) 用の Azure Key Vault のキーを使用する手順について説明します。 Bring Your Own Key (BYOK) がサポートされた TDE の詳細については、「[TDE Bring Your Own Key to Azure SQL](transparent-data-encryption-byok-azure-sql.md)」(Azure SQL への TDE の Bring Your Own Key) を参照してください。 

## <a name="prerequisites"></a>前提条件

- Azure サブスクリプションを所有し、そのサブスクリプションの管理者である必要があります。
- [推奨されますが、省略可能] TDE プロテクター キー マテリアルのローカル コピーを作成するためのハードウェア セキュリティ モジュール (HSM) またはローカル キー ストア。
- Azure PowerShell バージョン 4.2.0 以降をインストールして実行しておく必要があります。 
- TDE に使用する Azure Key Vault とキーを作成します。
   - [Key Vault からの PowerShell の手順](https://docs.microsoft.com/azure/key-vault/key-vault-get-started)
   - [ハードウェア セキュリティ モジュール (HSM) と Key Vault の使用手順](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
- TDE に使用するには、キーに次の属性が必要です。
   - 有効期限がない
   - 無効ではない
   - *キーの取得*、*キーのラップ*、*キーのラップ解除*操作を実行できる

## <a name="step-1-assign-an-aad-identity-to-your-server"></a>手順 1. サーバーに AAD ID を割り当てる 

既存のサーバーがある場合、以下を使用して AAD ID をサーバーに追加します。

   ```powershell
   $server = Set-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -AssignIdentity
   ```

サーバーを作成する場合、サーバーの作成時にタグ -Identity を指定して [New-AzureRmSqlServer](/powershell/module/azurerm.sql/new-azurermsqlserver) コマンドレットを使用し、AAD ID を追加します。

   ```powershell
   $server = New-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -Location <RegionName> `
   -ServerName <LogicalServerName> `
   -ServerVersion "12.0" `
   -SqlAdministratorCredentials <PSCredential> `
   -AssignIdentity 
   ```

## <a name="step-2-grant-key-vault-permissions-to-your-server"></a>手順 2. Key Vault のアクセス許可をサーバーに付与する

[Set-AzureRmKeyValutAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) コマンドレットを使用して、Key Vault へのアクセスをサーバーに付与してから、Key Vault のキーを TDE に使用します。

   ```powershell
   Set-AzureRmKeyVaultAccessPolicy  `
   -VaultName <KeyVaultName> `
   -ObjectId $server.Identity.PrincipalId `
   -PermissionsToKeys get, wrapKey, unwrapKey
   ```

## <a name="step-3-add-the-key-vault-key-to-the-server-and-set-the-tde-protector"></a>手順 3. Key Vault キーをサーバーに追加し、TDE プロテクターを設定する

- [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) コマンドレットを使用して、Key Vault のキーをサーバーに追加します。
- [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使用して、すべてのサーバー リソースの TDE プロテクターとしてキーを設定します。
- [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使用して、TDE プロテクターが意図したとおりに構成されたことを確認します。

> [!Note]
> Key Vault 名とキー名を組み合わせた長さの上限は 94 文字です。
> 

>[!Tip]
>Key Vault の KeyId の例: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
>

   ```powershell
   <# Add the key from Key Vault to the server #>
   Add-AzureRmSqlServerKeyVaultKey `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -KeyId <KeyVaultKeyId>

   <# Set the key as the TDE protector for all resources under the server #>
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> 

   <# To confirm that the TDE protector was configured as intended: #>
   Get-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> 
   ```

## <a name="step-4-turn-on-tde"></a>手順 4. TDE を有効にする 

[Set-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) コマンドレットを使用して TDE を有効にします。

   ```powershell
   Set-AzureRMSqlDatabaseTransparentDataEncryption `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName> `
   -State "Enabled"
   ```

データベースまたはデータ ウェアハウスで、Key Vault の暗号化キーを使用して TDE が有効になりました。

## <a name="step-5-check-the-encryption-state-and-encryption-activity-of-the-database-or-data-warehouse"></a>手順 5. データベースまたはデータ ウェアハウスの暗号化の状態と暗号化アクティビティを確認する

[Get-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) を使用して暗号化状態を取得し、[Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) を使用してデータベースまたはデータ ウェアハウスの暗号化の進行状況を確認します。

   ```powershell
   # Get the encryption state
   Get-AzureRMSqlDatabaseTransparentDataEncryption `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName> `

   <# Check the encryption progress for a database or data warehouse #>
   Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName>  
   ```

## <a name="other-useful-powershell-cmdlets"></a>その他の便利な PowerShell コマンドレット

- [Set-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) コマンドレットを使用して、TDE を無効にします。

   ```powershell
   Set-AzureRMSqlDatabaseTransparentDataEncryption `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -DatabaseName <DatabaseName> `
   -State "Disabled”
   ```
 
- [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) コマンドレットを使用して、サーバーに追加された Key Vault キーの一覧を返します。

   ```powershell
   <# KeyId is an optional parameter, to return a specific key version #>
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>
   ```
 
- [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) を使用して、サーバーから Key Vault キーを削除します。

   ```powershell
   <# The key set as the TDE Protector cannot be removed. #>
   Remove-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>   
   ```
 
## <a name="troubleshooting"></a>トラブルシューティング

問題が発生した場合は、以下を確認します。
- Key Vault が見つからない場合は、[Get-AzureRmSubscription](/powershell/module/azurerm.profile/get-azurermsubscription) コマンドレットを使用して適切なサブスクリプションを使用していることを確認します。

   ```powershell
   Get-AzureRmSubscription `
   -SubscriptionId <SubscriptionId>
   ```

- 新しいキーをサーバーに追加できない場合、または TDE プロテクターとして新しいキーを更新できない場合は、以下を確認します。
   - キーに有効期限がないこと
   - キーの*取得*、*キーのラップ*、*キーのラップ解除*操作が有効である必要があります。

## <a name="next-steps"></a>次の手順

- セキュリティ要件に準拠するようにサーバーの TDE プロテクターをローテーションする方法については、「[Rotate the Transparent Data Encryption protector Using PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md)」(PowerShell を使用して Transparent Data Encryption プロテクターをローテーションする) を参照してください。
- セキュリティ リスクが発生した場合、侵害された可能性のある TDE プロテクターを削除する方法については、「[Remove a potentially compromised key](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)」(PowerShell を使用して Transparent Data Encryption (TDE) プロテクターを削除する) を参照してください。 



