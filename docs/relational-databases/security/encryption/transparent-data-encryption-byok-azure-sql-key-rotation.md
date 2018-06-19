---
title: PowerShell - TDE プロテクターをローテーションする - Azure SQL | Microsoft Docs
description: Azure SQL Server の Transparent Data Encryption (TDE) プロテクターをローテーションする方法について説明します。
keywords: ''
services: sql-database
documentationcenter: ''
author: becczhang
manager: jhubbard
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: ''
ms.tgt_pltfrm: ''
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: ryzhang26
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 45dc9d4d9f4681fde06f75e8fa666c6584bcf863
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696743"
---
# <a name="rotate-the-transparent-data-encryption-tde-protector-using-powershell"></a>PowerShell を使用して Transparent Data Encryption (TDE) プロテクターをローテーションする 
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

この操作方法ガイドでは、Azure Key Vault から TDE プロテクターを使用して、Azure SQL Server のキーをローテーションする方法について説明します。 Azure SQL Server の TDE プロテクターのローテーションとは、サーバー上のデータベースを保護する新しい非対称キーに切り替えることを示します。 キーのローテーションはオンライン操作であり、完了までにかかる時間はわずか数秒です。これは、データベース全体ではなく、データベースのデータ暗号化キーの暗号化解除と再暗号化を行うだけだからです。

このガイドでは、サーバー上の TDE プロテクターをローテーションする 2 つのオプションについて説明します。

> [!NOTE]
> キーのローテーションの前に、一時停止した SQL Data Warehouse を再開する必要があります。
>

> [!IMPORTANT]
> ロールオーバー後に、以前のバージョンのキーは**削除しないでください**。  キーがロールオーバーされても、古いデータベースのバックアップなど、一部のデータは前のキーで暗号化されたままです。 
>

## <a name="prerequisites"></a>Prerequisites

- この操作方法ガイドでは、Azure SQL Database または Data Warehouse 用 TDE プロテクターとして Azure Key Vault のキーを既に使っているものとします。 「[Transparent Data Encryption with Bring Your Own Key support for Azure SQL Database and Data Warehouse](transparent-data-encryption-byok-azure-sql.md)」(Azure SQL Database および Data Warehouse 用の Bring Your Own Key サポートによる Transparent Data Encryption) を参照してください。
- Azure PowerShell バージョン 3.7.0 以降をインストールして実行しておく必要があります。 
- [推奨されますが、省略可能] まずハードウェア セキュリティ モジュール (HSM) またはローカル キー ストアに TDE プロテクターのキー マテリアルを作成し、キー マテリアルを Azure Key Vault にインポートします。 詳細については、[ハードウェア セキュリティ モジュール (HSM) と Key Vault の使用手順](https://docs.microsoft.com/azure/key-vault/key-vault-get-started)に関するページを参照してください。

## <a name="option-1-auto-rotation"></a>オプション 1: 自動ローテーション

同じキー名と Key Vault で、Key Vault の既存 TDE プロテクター キーの新しいバージョンを生成します。 Azure SQL サービスは、24 時間以内にこの新しいバージョンを使い始めます。 

[Add-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/add-azurekeyvaultkey) コマンドレットを使用して新しいバージョンの TDE プロテクターを作成するには:

   ```powershell
   Add-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -Destination <HardwareOrSoftware>
   ```

## <a name="option-2-manual-rotation"></a>オプション 2: 手動のローテーション

このオプションは、[Add-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/add-azurekeyvaultkey)、[Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey)、[Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使用して、完全に新しいキーを追加します。このキーは、新しいキー名以下、または別の Key Vault 以下にある可能性があります。 

>[!NOTE]
>Key Vault 名とキー名を組み合わせた長さの上限は 94 文字です。
>

   ```powershell
   # Add a new key to Key Vault
   Add-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -Destination <HardwareOrSoftware>

   # Add the new key from Key Vault to the server
   Add-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>   
  
   <# Set the key as the TDE protector for all resources 
   under the server #>
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
  
## <a name="other-useful-powershell-cmdlets"></a>その他の便利な PowerShell コマンドレット

- TDE プロテクターを Microsoft 管理から BYOK モードに切り替えるには、[Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使用します。

   ```powershell
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```

- TDE プロテクターを BYOK モードから Microsoft 管理に切り替えるには、[Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使用します。

   ```powershell
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type ServiceManaged `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName> 
   ``` 

## <a name="next-steps"></a>次の手順

- セキュリティ リスクが発生した場合、侵害された可能性のある TDE プロテクターを削除する方法については、「[Remove a Transparent Data Encryption (TDE) protector using PowerShell](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)」(PowerShell を使用して Transparent Data Encryption (TDE) プロテクターを削除する) を参照してください。 

- TDE の Bring Your Own Key サポートの概要については、「[PowerShell: Enable Transparent Data Encryption using your own key from Azure Key Vault](transparent-data-encryption-byok-azure-sql-configure.md)」(PowerShell: Azure Key Vault から自分のキーを使用して Transparent Data Encryption を有効にする) を参照してください。
