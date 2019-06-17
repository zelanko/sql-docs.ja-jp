---
title: Azure Key Vault (AKV) のカスタマー マネージド キーによる Transparent Data Encryption (TDE) の一般的なエラーと解決 | Microsoft Docs
description: Azure Key Vault 構成で Transparent Data Encryption (TDE) のトラブルシューティングを行います。
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
ms.openlocfilehash: 1366d0a20ed39b466d1a2f6cb3e84f0f30e17f9f
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718090"
---
# <a name="common-errors-and-resolutions-with-transparent-data-encryption-tde-with-customer-managed-keys-in-azure-key-vault-akv"></a>Azure Key Vault (AKV) のカスタマー マネージド キーによる Transparent Data Encryption (TDE) の一般的なエラーと解決

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
このトピックでは、次の問題について説明します。  
  
- 必要条件  
- 最も一般的なエラーを特定して解決する方法

## <a name="requirements"></a>必要条件
[AKV 構成でのカスタマー マネージド TDE プロテクター](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault)のトラブルシューティングを行うには、まず次の要件を確認します。
- 論理 SQL サーバーとキー コンテナーは、同じリージョンに配置する必要があります。
- Azure Active Directory (Azure Key Vault 内の APPID) によって提供される論理 SQL サーバー ID は、元のサブスクリプションのテナントに限定されます。  サーバーが別のサブスクリプションに移動されている場合、サーバー ID (APPID) を再作成する必要があります。
- キー コンテナーが稼働している必要があります。[Azure Resource Health](https://docs.microsoft.com/azure/service-health/resource-health-overview) を参照して、キー コンテナーの状態を確認し、[アクション グループ](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups)を参照して、通知にサインアップします。
- Geo-DR のシナリオでは、フェールオーバーが機能するために、両方のキー コンテナーに、同じキー マテリアルが格納されている必要があります。
- 論理サーバーには、キー コンテナーに対して認証するために、Azure Active Directory (AAD) ID (APPID) が必要です。
- APPID はキー コンテナーにアクセスでき、TDE プロテクターとして選択されているキーのラップ、ラップ解除、およびアクセス許可の取得を行う必要があります。

AKV で TDE を使用する場合に発生したほとんどの問題は、次の構成ミスのいずれかに原因があります。

### <a name="key-vault-unavailable-or-doesnt-exist"></a>キー コンテナーが使用できないか、または存在しない。
- キー コンテナーが誤って削除された
- Microsoft サービスへのアクセスを許可せずに Azure Key Vault に対してファイアウォールが構成された

### <a name="no-permissions-to-access-the-key-vault-or-key-doesnt-exist"></a>キー コンテナーへのアクセス許可がないか、またはキーが存在しない
- キーが誤って削除された
- SQL APPID が誤って削除された
- SQL が新しい APPID を必要とする別のサブスクリプションに移動された
- キーの APPID に付与されたアクセス許可が十分でない (ラップ、ラップ解除、取得)
- SQL APPID の権限が取り消された


次のセクションで、最も一般的なエラーのトラブルシューティング手順を挙げます。


## <a name="how-to-identify-and-resolve-the-most-common-errors"></a>最も一般的なエラーを特定して解決する方法

## <a name="missing-server-identity"></a>サーバー ID がない
エラー メッセージ:"401 AzureKeyVaultNoServerIdentity - サーバーでサーバー ID が正しく構成されていません。 サポートにお問い合わせください。"

検出:次のコマンドを使用して、論理 SQL サーバーに ID が割り当てられていることを確認します。

- [Azure PowerShell Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 
- [Azure CLI az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

軽減策:論理 SQL サーバーの Azure Active Directory (Azure AD) の ID (APPID) を構成します

PowerShell の場合:Set-AzureRmSqlServer コマンドに [-AssignIdentity](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0) オプションを指定して実行します 

CLI の場合:az sql server update コマンドに [-assign_identity](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update) オプションを指定して実行します 

Azure portal では、キー コンテナーを参照して [アクセス ポリシー] に移動します。  
 - [新規追加] ボタンを使用して、前の手順で作成したサーバーの APPID を追加します。 
 - 次のキー アクセス許可を割り当てます。取得、ラップ、ラップ解除 

[詳細情報](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server)

> [!IMPORTANT]
> AKV による TDE の初期構成後、論理 SQL サーバーが新しいサブスクリプションに移動された場合、AAD ID を構成する手順を繰り返して、新しい APPID を作成する必要があります。  新しい APPID がキー コンテナーに追加され、正しいアクセス許可が再割り当てされる必要があります。 
>

## <a name="missing-key-vault"></a>キー コンテナーがない
エラー メッセージ:"503 AzureKeyVaultConnectionFailed - Azure Key Vault への接続の試みが失敗したため、サーバーでの操作を完了できませんでした"

検出:キー URI とキー コンテナーを識別する方法 

手順 1:次のコマンドを使用して、特定の論理 SQL サーバーのキー URI を取得します。

-[Azure PowerShell get-azurermsqlserverkeyvaultkey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

-[Azure CLI az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

手順 2:キー URI を使用して、キー コンテナーを識別します

PowerShell:$MyServerKeyVaultKey のプロパティを検査して、キー コンテナーの詳細を取得できます

CLI:キー コンテナーの詳細について、返されるサーバー暗号化プロテクターを検査します

軽減策:キー コンテナーが使用できることを確認します
- キー コンテナーが使用でき、論理 SQL サーバーがアクセス権を持つことを確認します
- キー コンテナーがファイアウォールの背後にある場合は、Microsoft サービスのキー コンテナーへのアクセスを許可するチェック ボックスをオンにします
- キー コンテナーが誤って削除された場合は、構成を最初から実行する必要があります


## <a name="missing-key"></a>キーがない 
エラー メッセージ:"404 ServerKeyNotFound - The requested server key was not found on the current subscription." (404 ServerKeyNotFound - 要求されたサーバー キーは、現在のサブスクリプションで使用できません。)
"409 ServerKeyDoesNotExists - The server key does not exist." (409 ServerKeyDoesNotExists - サーバー キーは存在しません。)

検出:キー URI とキー コンテナーを識別する方法
- 上記の「キー コンテナーがない」セクションから、キーの一覧を返すコマンドレットを使用して、論理 SQL サーバーに追加されたキー URI を特定します。

軽減策:TDE プロテクターが AKV に存在することを確認します
- キー コンテナーを特定し、Azure portal でそれを参照します
- キー URI によって特定されたキーが存在することを確認します

## <a name="missing-permissions"></a>アクセス許可がない 
エラー メッセージ:"401 AzureKeyVaultMissingPermissions - The server is missing required permissions on the Azure Key Vault." (401 AzureKeyVaultMissingPermissions - サーバーには Azure Key Vault に必要なアクセス許可がありません。)

検出:キー URI とキー コンテナーを識別する方法
- 上記の「キー コンテナーがない」セクションのコマンドレットを使用して、論理 SQL サーバーで使用されているキー コンテナーを特定します。

軽減策:論理 SQL サーバーにキー コンテナーへのアクセス許可と、キーにアクセスするための正しいアクセス許可があることを確認します
- Azure portal で、キー コンテナーを参照し、[アクセス ポリシー] に移動して、Sql Server APPID を見つけます。  
  - APPID が存在しない場合は、[新規追加] ボタンを使用して、それを追加します。 
  - APPID が存在する場合は、次のキー アクセス許可があることを確認します。取得、ラップ、ラップ解除。
