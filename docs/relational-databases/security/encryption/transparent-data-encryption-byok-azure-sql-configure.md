---
title: 'PowerShell と CLI: 自分の Azure Key Vault キーを使用して SQL TDE を有効にする | Microsoft Docs'
description: PowerShell または CLI を使用して、保存時の暗号化に Transparent Data Encryption (TDE) の使用を開始するように、Azure SQL Database と Data Warehouse を構成する方法について説明します。
keywords: ''
documentationcenter: ''
author: aliceku
manager: craigg
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.component: security
ms.workload: On Demand
ms.tgt_pltfrm: ''
ms.devlang: azurecli, powershell
ms.topic: article
ms.date: 03/15/2018
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: eed635cc4b58c5ec975f0b77f8e3b69f87fd65ff
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vault"></a>PowerShell と CLI: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

この操作方法ガイドでは、SQL Database または Data Warehouse で Transparent Data Encryption (TDE) 用の Azure Key Vault のキーを使用する手順について説明します。 Bring Your Own Key (BYOK) がサポートされた TDE の詳細については、「[TDE Bring Your Own Key to Azure SQL](transparent-data-encryption-byok-azure-sql.md)」(Azure SQL への TDE の Bring Your Own Key) を参照してください。 

## <a name="prerequisites-for-powershell"></a>PowerShell の前提条件

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

## <a name="step-1-assign-an-azure-ad-identity-to-your-server"></a>手順 1. サーバーに Azure AD ID を割り当てる 

既存のサーバーがある場合、以下を使用して Azure AD ID をサーバーに追加します。

   ```powershell
   $server = Set-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -AssignIdentity
   ```

サーバーを作成する場合、サーバーの作成時にタグ -Identity を指定して [New-AzureRmSqlServer](/powershell/module/azurerm.sql/new-azurermsqlserver) コマンドレットを使用し、Azure AD ID を追加します。

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

[Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) コマンドレットを使用して、Key Vault へのアクセスをサーバーに付与してから、Key Vault のキーを TDE に使用します。

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
>Key Vault からの KeyId の例: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
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

## <a name="step-5-check-the-encryption-state-and-encryption-activity"></a>手順 5. 暗号化の状態と暗号化のアクティビティを確認する

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

## <a name="prerequisites-for-cli"></a>CLI の前提条件

- Azure サブスクリプションを所有し、そのサブスクリプションの管理者である必要があります。
- [推奨されますが、省略可能] TDE プロテクター キー マテリアルのローカル コピーを作成するためのハードウェア セキュリティ モジュール (HSM) またはローカル キー ストア。
- コマンド ライン インターフェイス バージョン 2.0 以降。 最新バージョンをインストールして Azure サブスクリプションに接続する方法については、[Azure クロスプラットフォーム コマンド ライン インターフェイス 2.0 のインストールと構成](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)に関するページを参照してください。 
- TDE に使用する Azure Key Vault とキーを作成します。
   - [CLI 2.0 を使用した Key Vault の管理](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-manage-with-cli2)
   - [ハードウェア セキュリティ モジュール (HSM) と Key Vault の使用手順](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
- TDE に使用するには、キーに次の属性が必要です。
   - 有効期限がない
   - 無効ではない
   - *キーの取得*、*キーのラップ*、*キーのラップ解除*操作を実行できる
   
## <a name="step-1-create-a-server-and-assign-an-azure-ad-identity-to-your-server"></a>手順 1. サーバーを作成し、サーバーに Azure AD ID を割り当てる
      ```cli
      # create server (with identity) and database
      az sql server create -n "ServerName" -g "ResourceGroupName" -l "westus" -u "cloudsa" -p "YourFavoritePassWord99@34" -I 
      az sql db create -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 
      ```

 
## <a name="step-2-grant-key-vault-permissions-to-your-server"></a>手順 2. Key Vault のアクセス許可をサーバーに付与する
      ```cli
      # create key vault, key and grant permission
      az keyvault create -n "VaultName" -g "ResourceGroupName" 
      az keyvault key create -n myKey -p software --vault-name "VaultName" 
      az keyvault set-policy -n "VaultName" --object-id "ServerIdentityObjectId" -g "ResourceGroupName" --key-permissions wrapKey unwrapKey get list 
      ```

 
## <a name="step-3-add-the-key-vault-key-to-the-server-and-set-the-tde-protector"></a>手順 3. Key Vault キーをサーバーに追加し、TDE プロテクターを設定する
  
     ```cli
     # add server key and update encryption protector
      az sql server key create -g "ResourceGroupName" -s "ServerName" -t "AzureKeyVault" -u "FullVersionedKeyUri 
      az sql server tde-key update -g "ResourceGroupName" -s "ServerName" -t AzureKeyVault -u "FullVersionedKeyUri" 
      ```
  
  > [!Note]
> Key Vault 名とキー名を組み合わせた長さの上限は 94 文字です。
> 

>[!Tip]
>Key Vault からの KeyId の例: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
>
  
## <a name="step-4-turn-on-tde"></a>手順 4. TDE を有効にする 
      ```cli
      # enable encryption
      az sql db tde create -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" --status Enabled 
      ```

データベースまたはデータ ウェアハウスで、Key Vault の暗号化キーを使用して TDE が有効になりました。

## <a name="step-5-check-the-encryption-state-and-encryption-activity"></a>手順 5. 暗号化の状態と暗号化のアクティビティを確認する

     ```cli
      # get encryption scan progress
      az sql db tde show-activity -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 

      # get whether encryption is on or off
      az sql db tde show-configuration -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 

      ```
