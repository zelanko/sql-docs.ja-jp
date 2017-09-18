---
title: "PowerShell - TDE プロテクターを削除する - Azure SQL | Microsoft Docs"
description: "BYOK (Bring Your Own Key) をサポートする TDE を使用する Azure SQL Database または Data Warehouse 用の TDE プロテクターが侵害された可能性がある場合の対処方法を説明します。"
keywords: 
services: sql-database
documentationcenter: 
author: becczhang
manager: jhubbard
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: 
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.translationtype: HT
ms.sourcegitcommit: 46b16dcf147dbd863eec0330e87511b4ced6c4ce
ms.openlocfilehash: 861a24ef2f0bc26adece27b2612d4bf2d4640a63
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---


# <a name="remove-a-transparent-data-encryption-tde-protector-using-powershell"></a>PowerShell を使用して Transparent Data Encryption (TDE) プロテクターを削除する

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

## <a name="prerequisites"></a>前提条件
- Azure サブスクリプションを所有し、そのサブスクリプションの管理者である必要があります。
- Azure PowerShell バージョン 4.2.0 以降をインストールして実行しておく必要があります。 
- この操作方法ガイドでは、Azure SQL Database または Data Warehouse 用 TDE プロテクターとして Azure Key Vault のキーを既に使っているものとします。 詳細については、「[Transparent Data Encryption with BYOK Support](transparent-data-encryption-byok-azure-sql.md)」(Bring Your Own Key サポートによる Transparent Data Encryption) を参照してください。

## <a name="overview"></a>概要
この操作方法ガイドでは、BYOK (Bring Your Own Key) をサポートする TDE を使用する Azure SQL Database または Data Warehouse 用の TDE プロテクターが侵害された可能性がある場合の対処方法を説明します。 TDE の BYOK サポートの詳細については、[概要に関するページ](transparent-data-encryption-byok-azure-sql.md)を参照してください。 

以下の手順は、極めて普通ではない状況またはテスト環境においてのみ行う必要があります。 アクティブに使われている TDE プロテクターを Azure Key Vault から削除すると**データが失われる**可能性があるので、この操作方法ガイドを慎重に確認してください。 

サービスまたはユーザーがキーに不正アクセスしたなど、キーが侵害された疑いがある場合は、キーを削除するのが最善の対処です。

Key Vault の TDE プロテクターを削除すると、**サーバーにある暗号化されたデータベースへのすべての接続がブロックされ、これらのデータベースはオフラインになり、24 時間以内に削除される**ことに注意してください。 侵害されたキーで暗号化された古いバックアップにはアクセスできなくなります。

この操作方法ガイドでは、インシデント対応後の望ましい結果に応じて、2 つの方法を説明します。
- Azure SQL Database/Data Warehouse を**アクセス可能**のままにする場合
- Azure SQL Database/Data Warehouse を**アクセス不可能**にする場合

## <a name="to-keep-the-encrypted-resources-accessible"></a>暗号化されたリソースをアクセス可能のままにするには
1. [Key Vault に新しいキー](https://docs.microsoft.com/powershell/module/azurerm.keyvault/add-azurekeyvaultkey?view=azurermps-4.1.0)を作成します。 アクセス制御はコンテナー レベルでプロビジョニングされるため、この新しいキーは侵害された可能性のある TDE プロテクターとは別のキー コンテナーに作成する必要があります。 
2. [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) および [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使ってサーバーに新しいキーを追加し、サーバーの新しい TDE プロテクターとして更新します。

   ```powershell
   # Add the key from Key Vault to the server  
   Add-AzureRmSqlServerKeyVaultKey `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -KeyId <KeyVaultKeyId>
   
   # Set the key as the TDE protector for all resources under the server
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -Type AzureKeyVault -KeyId <KeyVaultKeyId> 
   ```

3. [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) コマンドレットを使って、サーバーとレプリカが新しい TDE に更新されたことを確認します。 

   >[!NOTE]
   > サーバーに存在するすべてのデータベースとセカンダリ データベースに新しい TDE プロテクターが反映されるまでに、数分かかる場合があります。
   >

   ```powershell
   Get-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>
   ```

4. Key Vault の[新しいキーのバックアップ](/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey)を作成します。

   ```powershell
   <# -OutputFile parameter is optional; 
   if removed, a file name is automatically generated. #>
   Backup-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -OutputFile <DesiredBackupFilePath>
   ```
 
5. [Remove-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/remove-azurekeyvaultkey) コマンドレットを使って、Key Vault から侵害されたキーを削除します。 

   ```powershell
   Remove-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName>
   ```
 
6. 後で Key Vault にキーを復元するには、[Restore-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/restore-azurekeyvaultkey) コマンドレットを使います。
   ```powershell
   Restore-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -InputFile <BackupFilePath>
   ```
 
## <a name="to-make-the-encrypted-resources-inaccessible"></a>暗号化されたリソースをアクセス不可能にするには
1. 侵害された可能性のあるキーによって暗号化されているデータベースを削除します。
データベースとログ ファイルは自動的にバックアップされるため、(キーを提供する限り) 任意の時点でデータベースのポイントインタイム リストアを実行できます。 最新のトランザクションの最大 10 分間のデータが失われる可能性を防ぐため、アクティブな TDE プロテクターを削除する前に、データベースを削除する必要があります。 
2. Key Vault の TDE プロテクターのキー マテリアルをバックアップします。
3. 侵害された可能性のあるキーを Key Vault から削除します。

## <a name="next-steps"></a>次の手順

- セキュリティ要件に準拠するようにサーバーの TDE プロテクターをローテーションする方法については、「[Rotate the Transparent Data Encryption protector Using PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md)」(PowerShell を使用して Transparent Data Encryption プロテクターをローテーションする) を参照してください

- TDE の Bring Your Own Key サポートの概要については、「[PowerShell: Enable Transparent Data Encryption using your own key from Azure Key Vault](transparent-data-encryption-byok-azure-sql-configure.md)」(PowerShell: Azure Key Vault から独自のキーを使用して Transparent Data Encryption を有効にする) を参照してください。

