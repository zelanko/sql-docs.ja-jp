---
title: "Azure SQL Database と Data Warehouse 用の TDE | Microsoft Docs"
description: "SQL Database と Data Warehouse 用の Transparent Data Encryption の概要。 このドキュメントでは、利点と、構成のオプション (サービス管理 TDE、Bring Your Own Key など) について説明します。"
keywords: 
services: sql-database
documentationcenter: 
author: becczhang
manager: cguyer
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: On Demand
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.openlocfilehash: ac3ea91dc2db3d1cfb22dca2fdc341650c74b95b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="transparent-data-encryption-for-azure-sql-database-and-data-warehouse"></a>Azure SQL Database と Data Warehouse 用の Transparent Data Encryption

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Transparent Data Encryption (TDE) を使用すると、データベース、関連するバックアップ、静止したトランザクション ログ ファイルのリアルタイム暗号化および暗号化解除を実行して、悪意のあるアクティビティの脅威から Azure SQL Database と Data Warehouse を保護できます。アプリケーションに変更を加える必要はありません。

TDE では、データベース暗号化キー (DEK) という対称キーを使用してデータベース全体のストレージを暗号化します。 このデータベース暗号化キーは、TDE プロテクターで保護されます。TDE プロテクターとは、サービス管理証明書 ("サービス管理 TDE") または Azure Key Vault に格納されている非対称キー ("Bring Your Own Key") です。 TDE プロテクターはサーバー レベルで設定されます。 

データベースの起動時に、DEK の暗号化は解除され、SQL エンジン プロセスでデータベース ファイルの暗号化解除と再暗号化に使用されます。 TDE では、ページ レベルでデータのリアルタイム I/O 暗号化と暗号化解除が実行されます。 各ページは、メモリに読み込まれるときに暗号化が解除され、ディスクに書き込まれる前に暗号化されます。 TDE の一般的な説明については、「[透過的なデータ暗号化 (TDE)](transparent-data-encryption.md)」を参照してください。

Azure 仮想マシン上で実行されている SQL Server は、Key Vault の非対称キーを使用することもできます。 構成手順は、Azure SQL Database で非対称キーを使用する場合と異なります。 詳細については、「[Azure Key Vault を使用する拡張キー管理 (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。

## <a name="service-managed-tde"></a>サービス管理 TDE

Azure の TDE の既定設定では、データベース暗号化キーは、組み込みのサーバー証明書によって保護されます。 組み込みのサーバー証明書は、各サーバーに対して一意です。 データベースが geo レプリケーション関係にある場合、プライマリおよび geo セカンダリ データベースの両方がプライマリの親サーバー キーで保護されます。 2 つのデータベースが同じサーバーに接続している場合は、同じ組み込みの証明書を共有します。 Microsoft は、少なくとも 90 日ごとにこれらの証明書を自動的に回転します。

また、geo レプリケーションと復元に必要なので、キーの移動と管理をシームレスに行います。 

> [!IMPORTANT]
> 新しく作成されたすべての SQL データベースは、既定でサービス管理 TDE を使用して暗号化されます。 2017 年 5 月より前の既存のデータベースと、復元、geo レプリケーション、およびデータベースのコピーで作成されたデータベースは、既定で暗号化されません。
>

## <a name="bring-your-own-key"></a>Bring Your Own Key

Bring Your Own Key (BYOK) サポートを利用すると、TDE 暗号化キーをユーザーが制御できるようになり、いつ誰がキーにアクセスできるかを制御できます。 Azure のクラウド ベースの外部キー管理システムである Azure Key Vault (AKV) は、BYOK のサポートのために TDE が統合された最初のキー管理サービスです。 BYOK がサポートされていると、データベース暗号化キーは AKV に格納されている非対称キーによって保護されます。 非対称キーが Key Vault を離れることはありません。サーバーが Key Vault へのアクセス許可を取得すると、サーバーから Key Vault サービス経由で基本的なキー操作要求が送信されます。 非対称キーはサーバー レベルで設定され、そのサーバーに存在するすべてのデータベースによって継承されます。 BYOK のサポートにより、ユーザーは、キーのローテーション、キー コンテナーのアクセス許可、キーの削除、すべての暗号化キーの監査/レポートの有効化など、キー管理タスクを制御できるようになります。 Key Vault は、キーの集中管理機能を提供し、厳重に監視されたハードウェア セキュリティ モジュール (HSM) を利用して、キーとデータの管理の分離を促進することにより規制のコンプライアンス対応を実現します。 Key Vault の詳細については、「[キー コンテナーのセキュリティ保護](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault)」を参照してください。

Azure SQL Database と Data Warehouse 用の BYOK がサポートされた TDE の詳細については、「[Transparent Data Encryption with Bring Your Own Key support](transparent-data-encryption-byok-azure-sql.md)」(Bring Your Own Key がサポートされた Transparent Data Encryption) を参照してください。

BYOK がサポートされた TDE を初めて使用する場合は、方法ガイド「[Turn on Transparent Data Encryption using your own key from Key Vault Using PowerShell](transparent-data-encryption-byok-azure-sql-configure.md)」(PowerShell で Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする) を参照してください。

## <a name="moving-a-tde-protected-database"></a>TDE で保護されたデータベースの移動

Azure 内での操作用にデータベースの暗号化を解除する必要はありません。 ソース データベースまたはプライマリ データベースの TDE の設定は、ターゲットに透過的に継承されます。 これには次の操作が含まれます。
- geo リストア
- セルフ サービスによる特定の時点での復元
- 削除されたデータベースの復元
- アクティブな地理的レプリケーション
- データベースのコピーの作成

TDE で保護されたデータベースをエクスポートする場合、データベースのエクスポートされるコンテンツは暗号化されません。 このエクスポートされたコンテンツは、暗号化されていない BACPAC ファイルに保存されます。 BACPAC ファイルは必ず適切に保護し、新しいデータベースのインポートが完了したら TDE を有効にしてください。

たとえば、BACPAC ファイルをオンプレミスの SQL Server からエクスポートする場合、新しいデータベースのインポートされるコンテンツは自動的に暗号化されません。 同様に、BACPAC をオンプレミスの SQL Server にエクスポートする場合も、新しいデータベースは自動的に暗号化されません。

例外は、Azure SQL Database へのエクスポートと Azure SQL Database からのエクスポートのみです。 新しいデータベースでは TDE が有効になりますが、PACPAC ファイル自体は暗号化されません。

## <a name="managing-transparent-data-encryption-in-the-azure-portal"></a>Azure Portal で Transparent Data Encryption を管理する

Azure Portal で TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。 

Transparent Data Encryption はデータベース レベルで設定されます。 データベースで TDE を有効にするには、[Azure Portal](https://portal.azure.com) にアクセスし、Azure 管理者または共同作成者アカウントでサインインします。 ユーザー データベース以下の TDE 設定を見つけます。 既定ではサービス管理 TDE が使用され、データベースを含むサーバーの TDE 証明書が自動生成されます。 

![サービス管理 TDE](./media/transparent-data-encryption-azure-sql/service-managed-tde.png)  

TDE マスター キーは *TDE プロテクター*とも呼ばれ、サーバー レベルで設定されます。 Bring Your Own Key がサポートされた TDE を使用し、Azure Key Vault のキーでデータベースを保護するには、お使いのサーバーの TDE 設定にアクセスします。 

![BYOK がサポートされた TDE](./media/transparent-data-encryption-azure-sql/tde-byok-support.png) 

## <a name="managing-transparent-data-encryption-using-powershell"></a>PowerShell を使用して Transparent Data Encryption を管理する

PowerShell で TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。 

| コマンドレット | Description |
| --- | --- |
| [Set-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) |データベースの TDE を有効または無効にします。|
| [Get-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) |データベースの TDE の状態を取得します。 |
| [Get-AzureRmSqlDatabaseTransparentDataEncryptionActivity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) |データベースの暗号化の進行状況を確認します。 |
| [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) |SQL Server に Key Vault キーを追加します。 |
| [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) |SQL Server の Key Vault キーを取得します。 |
| [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) |SQL Server の TDE プロテクターを設定します。 |
| [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) |Transparent Data Encryption (TDE) プロテクターを取得します。 |
| [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) |SQL Server から Key Vault キーを削除します。 |
|  | |

## <a name="managing-transparent-data-encryption-using-transact-sql"></a>Transact-SQL を使用して Transparent Data Encryption を管理する

管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。

| Command | Description |
| --- | --- |
| [ALTER DATABASE (Azure SQL Database)](/sql/t-sql/statements/alter-database-azure-sql-database) | SET ENCRYPTION ON/OFF を使用してデータベースの暗号化または暗号化解除を行います。 |
| [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) |データベースの暗号化の状態およびデータベースに関連付けられているデータベース暗号化キーに関する情報を返します。 |
| [sys.dm_pdw_nodes_database_encryption_keys](https://docs.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql) |各データ ウェアハウス ノードの暗号化状態と、それに関連付けられているデータベース暗号化キーに関する情報を返します。 | 
|  | |

Transact-SQL を使用する場合、TDE プロテクターを Azure Key Vault のキーに切り替えることはできません。PowerShell または Azure Portal を使用してください。

## <a name="managing-transparent-data-encryption-using-rest-api"></a>REST API を使用して Transparent Data Encryption を管理する
 
REST API で TDE を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。 

| Command | Description |
| --- | --- |
|[サーバーの作成または更新](/rest/api/sql/servers/createorupdate)|AAD ID を SQL Server に追加します (Key Vault にアクセス権を付与するために使用されます)。|
|[サーバー キーの作成または更新](/rest/api/sql/serverkeys/createorupdate)|SQL Server に Key Vault キーを追加します。|
|[サーバー キーの削除](/rest/api/sql/serverkeys/delete)|SQL Server から Key Vault キーを削除します。|
|[サーバー キーの取得](/rest/api/sql/serverkeys/get)|SQL Server から特定の Key Vault キーを取得します。|
|[サーバー キー一覧をサーバー別に取得](/rest/api/sql/serverkeys/listbyserver)|SQL Server の Key Vault キーを取得します。|
|[暗号化プロテクターの作成または更新](/rest/api/sql/encryptionprotectors/createorupdate)|SQL Server の TDE プロテクターを設定します。|
|[暗号化プロテクターの取得](/rest/api/sql/encryptionprotectors/get)|SQL Server の TDE プロテクターを取得します。|
|[暗号化プロテクター一覧をサーバー別に取得](/rest/api/sql/encryptionprotectors/listbyserver)|SQL Server の TDE プロテクターを取得します。|
|[Transparent Data Encryption 構成の作成または更新](/rest/api/sql/transparentdataencryptions/createorupdate)|データベースの TDE を有効または無効にします。|
|[Transparent Data Encryption 構成の取得](/rest/api/sql/transparentdataencryptions/get)|データベースの TDE 構成を取得します。|
|[Transparent Data Encryption 構成結果一覧の取得](/rest/api/sql/transparentdataencryptionactivities/ListByConfiguration)|データベースの暗号化結果を取得します。|

## <a name="next-steps"></a>次の手順

- TDE の一般的な説明については、「[透過的なデータ暗号化 (TDE)](transparent-data-encryption.md)」を参照してください。

- Azure SQL Database と Data Warehouse 用の BYOK がサポートされた TDE の詳細については、「[Transparent Data Encryption with Bring Your Own Key support](transparent-data-encryption-byok-azure-sql.md)」(Bring Your Own Key がサポートされた Transparent Data Encryption) を参照してください。

- BYOK がサポートされた TDE を初めて使用する場合は、方法ガイド「[Turn on Transparent Data Encryption using your own key from Key Vault Using PowerShell](transparent-data-encryption-byok-azure-sql-configure.md)」(PowerShell で Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする) を参照してください。

- Key Vault の詳細については、「[キー コンテナーのセキュリティ保護](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault)」を参照してください。
