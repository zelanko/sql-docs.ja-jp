---
title: Azure Key Vault のカスタマー マネージド キーを使った透過的なデータ暗号化に関する一般的なエラー | Microsoft Docs
description: Azure Key Vault 構成を使った透過的なデータ暗号化 (TDE) のトラブルシューティングを行います。
helpviewer_keywords:
- troublshooting, tde akv
- tde akv configuration, troubleshooting
- tde troubleshooting
author: aliceku
manager: craigg
ms.prod: sql
ms.technology: security
ms.reviewer: vanto
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f963e15d674115029fce78b98ba280fe75da2cd1
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716667"
---
# <a name="common-errors-for-transparent-data-encryption-with-customer-managed-keys-in-azure-key-vault"></a>Azure Key Vault のカスタマー マネージド キーを使った透過的なデータ暗号化に関する一般的なエラー

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
この記事では、Azure Key Vault のカスタマー マネージド キーによる透過的なデータ暗号化 (TDE) を使うための要件と、一般的なエラーを識別して解決する方法について説明します。

## <a name="requirements"></a>必要条件

Key Vault のカスタマー マネージド TDE プロテクターを使って TDE のトラブルシューティングを行うには、次の要件を満たしている必要があります。

- 論理 SQL Server インスタンスとキー コンテナーは、同じリージョンに配置する必要がある。
- Azure Active Directory (Azure AD) により提供される論理 SQL Server インスタンス ID (Azure Key Vault の AppId) は、元のサブスクリプションのテナントである必要がある。 サーバーが、作成されたのとは別のサブスクリプションに移動された場合、サーバー ID (AppId) を再作成する必要がある。
- キー コンテナーが稼働している必要がある。 キー コンテナーの状態を確認する方法については、[Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview) に関する記事をご覧ください。 通知にサインアップするには、[アクション グループ](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups)に関する記事をご覧ください。
- geo ディザスター リカバリーのシナリオでは、フェールオーバーを機能させるために、両方のキー コンテナーに同じキー マテリアルを含める必要がある。
- 論理サーバーには、キー コンテナーへの認証のための Azure AD ID (AppId) がある必要がある。
- AppId にはキー コンテナーへのアクセス権がある必要がある。また、TDE プロテクターとして選択されたキーに対する取得、ラップ、ラップ解除のアクセス許可がある必要がある。

詳細については、「[TDE と Azure Key Vault の構成に関するガイドライン](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault)」をご覧ください。

## <a name="common-misconfigurations"></a>一般的な構成ミス

Key Vault による TDE を使用しているときに発生する問題のほとんどは、次の構成ミスのいずれかが原因です。

### <a name="the-key-vault-is-unavailable-or-doesnt-exist"></a>キー コンテナーが使用できない、または存在しない

- キー コンテナーが誤って削除された。
- Azure Key Vault に対してファイアウォールが構成されたが、そこで Microsoft サービスへのアクセスが許可されていない。

### <a name="no-permissions-to-access-the-key-vault-or-the-key-doesnt-exist"></a>キー コンテナーへのアクセス許可がない、またはキーが存在しない

- キーが誤って削除された。
- 論理 SQL Server インスタンスの AppId が誤って削除された。
- 論理 SQL Server インスタンスが別のサブスクリプションに移動された。 論理サーバーが別のサブスクリプションに移動された場合、新しい AppId を作成する必要があります。
- キー用の AppId に付与されているアクセス許可が不十分 (取得、ラップ、ラップ解除が含まれていない)。
- 論理 SQL Server インスタンスの AppId に対するアクセス許可が取り消された。

## <a name="identify-and-resolve-common-errors"></a>一般的なエラーの識別と解決

このセクションでは、最も一般的なエラーに対するトラブルシューティング手順の一覧を示します。

### <a name="missing-server-identity"></a>サーバー ID がない

**エラー メッセージ**

"_401 AzureKeyVaultNoServerIdentity - サーバーでサーバー ID が正しく構成されていません。サポートにお問い合わせください。_ "

**検出**

次のコマンドレットまたはコマンドを使用して、論理 SQL Server インスタンスに ID が割り当てられていることを確認します。

- Azure PowerShell:[Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 

- Azure CLI: [az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

**軽減策**

次のコマンドレットまたはコマンドを使用して、論理 SQL Server インスタンス用の Azure AD ID (AppId) を構成します。

- Azure PowerShell:`-AssignIdentity` オプションを指定した [Set-AzureRmSqlServer](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0)。

- Azure CLI: `--assign_identity` オプションを指定した [az sql server update](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update)。

Azure portal では、キー コンテナーに移動してから、 **[アクセス ポリシー]** に移動します。 次の手順を完了します。 

 1. **[新規追加]** ボタンを使用して、前の手順で作成したサーバーの AppId を追加します。 
 1. 次のキー アクセス許可を割り当てます。取得、ラップ、ラップ解除 

詳細については、「[サーバーに Azure AD ID を割り当てる](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server)」をご覧ください。

> [!IMPORTANT]
> Key Vault による TDE の初期構成後に論理 SQL Server インスタンスが新しいサブスクリプションに移動された場合、Azure AD ID を構成する手順を繰り返して、新しい AppId を作成します。 その後、その AppId をキー コンテナーに追加し、キーに適切なアクセス許可を割り当てます。 
>

### <a name="missing-key-vault"></a>キー コンテナーがない

**エラー メッセージ**

"_503 AzureKeyVaultConnectionFailed - Azure Key Vault への接続の試みが失敗したため、サーバーでの操作を完了できませんでした_"

**検出**

キー URI とキー コンテナーを識別するには:

1. 次のコマンドレットまたはコマンドを使用して、特定の論理 SQL Server インスタンスのキー URI を取得します。

    - Azure PowerShell:[Get-AzureRmSqlServerKeyVaultKey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

    - Azure CLI: [az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

1. キー URI を使用して、キー コンテナーを識別します。

    - Azure PowerShell:$MyServerKeyVaultKey 変数のプロパティを検査して、キー コンテナーの詳細を取得できます。

    - Azure CLI:キー コンテナーの詳細について、返されるサーバー暗号化プロテクターを検査します。

**軽減策**

キー コンテナーを使用できることを確認します。

- キー コンテナーを使用でき、論理 SQL Server インスタンスにアクセス権があることを確認します。
- キー コンテナーがファイアウォールの背後にある場合は、Microsoft サービスによるキー コンテナーへのアクセスを許可するチェック ボックスがオンになっていることを確認します。
- キー コンテナーが誤って削除された場合は、最初から構成を完了する必要があります。


### <a name="missing-key"></a>キーがない

**エラー メッセージ**

"_404 ServerKeyNotFound - The requested server key was not found on the current subscription._ " (404 ServerKeyNotFound - 要求されたサーバー キーは、現在のサブスクリプションで使用できません。) 

"_409 ServerKeyDoesNotExists - The server key does not exist._ " (409 ServerKeyDoesNotExists - サーバー キーは存在しません。)

**検出**

キー URI とキー コンテナーを識別するには:

- 「[キー コンテナーがない](#missing-key-vault)」のコマンドレットまたはコマンドを使用して、論理 SQL Server インスタンスに追加されたキー URI を識別します。 コマンドを実行すると、キーの一覧が返されます。

**軽減策**

TDE プロテクターが Key Vault に存在することを確認します。

1. キー コンテナーを識別した後、Azure portal でそのキー コンテナーに移動します。
1. キー URI によって識別されたキーが存在することを確認します。

### <a name="missing-permissions"></a>アクセス許可がない

**エラー メッセージ**

"_401 AzureKeyVaultMissingPermissions - The server is missing required permissions on the Azure Key Vault._ " (401 AzureKeyVaultMissingPermissions - サーバーには Azure Key Vault に必要なアクセス許可がありません。)

**検出**

キー URI とキー コンテナーを識別するには: 

- 「[キー コンテナーがない](#missing-key-vault)」のコマンドレットまたはコマンドを使用して、論理 SQL Server インスタンスによって使用されるキー コンテナーを識別します。

**軽減策**

論理 SQL Server インスタンスにキー コンテナーへのアクセス許可と、キーにアクセスするための適切なアクセス許可があることを確認します。

- Azure portal で、キー コンテナー > **[アクセス ポリシー]** の順に移動します。 論理 SQL Server インスタンスの AppId を探します。  
- AppId が存在する場合は、その AppId に次のキー アクセス許可があることを確認します。取得、ラップ、ラップ解除。
- AppId が存在しない場合は、 **[新規追加]** ボタンを使用して、それを追加します。 

## <a name="next-steps"></a>次の手順

- 「[TDE と Azure Key Vault の構成に関するガイドライン](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault)」を確認する。
- [Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview) について学習する。
- [サーバーに Azure AD ID を割り当てる](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server)方法を再確認する。
