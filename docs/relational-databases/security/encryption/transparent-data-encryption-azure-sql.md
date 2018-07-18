---
title: Azure SQL Database と Data Warehouse の透過的なデータ暗号化 | Microsoft Docs
description: SQL Database と Data Warehouse の透過的なデータ暗号化の概要。 このドキュメントでは、利点と、構成のオプション (サービス管理の透過的なデータ暗号化と Bring Your Own Key を含む) について説明します。
keywords: ''
author: becczhang
manager: craigg
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.date: 07/09/2018
ms.author: aliceku
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 49a3745e67a51ee8f5eb9625d518328f61593514
ms.sourcegitcommit: dcd29cd2d358bef95652db71f180d2a31ed5886b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2018
ms.locfileid: "37934854"
---
# <a name="transparent-data-encryption-for-sql-database-and-data-warehouse"></a>Azure SQL Database と Data Warehouse の透過的なデータ暗号化
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

透過的なデータ暗号化 (TDE) は、悪意のあるアクティビティの脅威から Azure SQL Database と Azure Data Warehouse を保護するのに役立ちます。 データベース、関連するバックアップ、静止したトランザクション ログ ファイルのリアルタイム暗号化および暗号化解除を実行します。アプリケーションに変更を加える必要はありません。 既定では、TDL は新しく展開されるすべての Azure SQL Database で有効です。 SQL Database で論理 **master** データベースを暗号化するために TDE を使用することはできません。  **master** データベースには、ユーザー データベースで TDE 操作を実行する必要があるオブジェクトが含まれます。

古いデータベースや Azure SQL Data Warehouse の場合、TDE を手動で有効にする必要があります。  

透過的なデータ暗号化では、データベース暗号化キーという対称キーを使用してデータベース全体のストレージを暗号化します。 このデータベース暗号化キーは、透過的なデータ暗号化プロテクターで保護されます。 プロテクターは、サービス管理証明書 (サービス管理の透過的なデータ暗号化) または Azure Key Vault に格納されている非対称キー (Bring Your Own Key) です。 透過的なデータ暗号化プロテクターはサーバー レベルで設定します。 

データベースの起動時に、暗号化されたデータベース暗号化キーは暗号化解除されてから、SQL Server データベース エンジン プロセスでデータベース ファイルの暗号化解除と再暗号化に使用されます。 透過的なデータ暗号化では、ページ レベルでデータのリアルタイム I/O 暗号化と暗号化解除が実行されます。 各ページは、メモリに読み込まれるときに暗号化が解除され、ディスクに書き込まれる前に暗号化されます。 透過的なデータ暗号化の一般的な説明については、「[透過的なデータ暗号化 (TDE)](transparent-data-encryption.md)」を参照してください。

Azure 仮想マシン上で実行されている SQL Server は、Key Vault の非対称キーを使用することもできます。 構成手順は、SQL Database で非対称キーを使用する場合と異なります。 詳細については、「[Azure Key Vault を使用する拡張キー管理 (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md)」を参照してください。

## <a name="service-managed-transparent-data-encryption"></a>サービス管理の透過的なデータ暗号化

Azure の透過的なデータ暗号化の既定設定では、データベース暗号化キーは、組み込みのサーバー証明書によって保護されます。 組み込みのサーバー証明書は、各サーバーに対して一意です。 データベースが geo レプリケーション関係にある場合、プライマリおよび geo セカンダリ データベースの両方がプライマリ データベースの親サーバー キーで保護されます。 2 つのデータベースが同じサーバーに接続されている場合は、同じ組み込みの証明書が共有されます。 Microsoft は、少なくとも 90 日ごとにこれらの証明書を自動的に回転します。

また、geo レプリケーションと復元で必要な場合に、キーの移動と管理をシームレスに行います。 

> [!IMPORTANT]
> 新しく作成されたすべての SQL データベースは、既定でサービス管理の透過的なデータ暗号化を使用して暗号化されます。 2017 年 5 月より前の既存のデータベースと、復元、geo レプリケーション、およびデータベースのコピーで作成されたデータベースは、既定で暗号化されません。
>

## <a name="bring-your-own-key"></a>Bring Your Own Key

Bring Your Own Key のサポートにより、ユーザーは透過的なデータ暗号化キーを制御でき、また、いつ誰がキーにアクセスできるかを制御できます。 Azure のクラウド ベースの外部キー管理システムである Key Vault は、透過的なデータ暗号化が Bring Your Own Key サポートと統合された最初のキー管理サービスです。 Bring Your Own Key がサポートされている場合、データベース暗号化キーは Key Vault に格納されている非対称キーによって保護されます。 非対称キーが Key Vault の外に出ることはありません。 サーバーに Key Vault へのアクセス許可がある場合、そのサーバーから Key Vault 経由で基本的なキー操作要求が送信されます。 非対称キーはサーバー レベルで設定し、そのサーバーに存在するすべてのデータベースによって継承されます。

Bring Your Own Key サポートにより、キー交換や Key Vault アクセス許可などのキー管理タスクを制御できるようになりました。 また、キーを削除して、すべての暗号化キーの監査/レポート作成を有効にすることもできます。 Key Vault は、キーの集中管理機能を提供し、厳重に監視されたハードウェア セキュリティ モジュールを使用します。 キーとデータの管理の分離を促進することにより、規制のコンプライアンス対応を実現します。 Key Vault の詳細については、「[キー コンテナーのセキュリティ保護](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault)」を参照してください。

SQL Database と Data Warehouse 用の Bring Your Own Key がサポートされた透過的なデータ暗号化の詳細については、「[Azure SQL Database および Data Warehouse 用の Bring Your Own Key (プレビュー) サポートによる Transparent Data Encryption](transparent-data-encryption-byok-azure-sql.md)」を参照してください。

Bring Your Own Key がサポートされた透過的なデータ暗号化の使用を開始する場合は、方法ガイドの「[PowerShell: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする (プレビュー)](transparent-data-encryption-byok-azure-sql-configure.md)」を参照してください。

## <a name="move-a-transparent-data-encryption-protected-database"></a>透過的なデータ暗号化で保護されたデータベースを移動する

Azure 内での操作用にデータベースの暗号化を解除する必要はありません。 ソース データベースまたはプライマリ データベースの透過的なデータ暗号化の設定は、ターゲットに透過的に継承されます。 含まれる操作には、次のようなものがあります。
- geo リストア。
- セルフ サービスによる特定の時点での復元。
- 削除されたデータベースの復元。
- アクティブ geo レプリケーション。
- データベースのコピーの作成。

透過的なデータ暗号化で保護されたデータベースをエクスポートするときに、データベースのエクスポートされたコンテンツは暗号化されません。 このエクスポートされたコンテンツは、暗号化されていない BACPAC ファイルに保存されます。 BACPAC ファイルは必ず適切に保護し、新しいデータベースのインポートが完了してから透過的なデータ暗号化を有効にしてください。

たとえば、BACPAC ファイルをオンプレミスの SQL Server インスタンスからエクスポートする場合、新しいデータベースのインポートされるコンテンツは自動的に暗号化されません。 同様に、BACPAC ファイルをオンプレミスの SQL Server インスタンスにエクスポートする場合も、新しいデータベースは自動的に暗号化されません。

例外は、SQL Database へのエクスポートと SQL Database からのエクスポートのみです。 透過的なデータ暗号化は新しいデータベースでは有効になりますが、それでも BACPAC ファイル自体は暗号化されません。

## <a name="manage-transparent-data-encryption-in-the-azure-portal"></a>Azure Portal で透過的なデータ暗号化を管理する

Azure Portal で透過的なデータ暗号化を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。 

透過的なデータ暗号化はデータベース レベルで設定します。 データベースで透過的なデータ暗号化を有効にするには、[Azure Portal](https://portal.azure.com) に移動し、Azure 管理者または共同作成者アカウントでサインインします。 ご利用のユーザー データベースの透過的なデータ暗号化設定を見つけます。 既定では、サービス管理の透過的なデータ暗号化が使用されます。 透過的なデータ暗号化の証明書は、データベースを含むサーバーに対して自動的に生成されます。 

![サービス管理の透過的なデータ暗号化](./media/transparent-data-encryption-azure-sql/service-managed-tde.png)  

透過的なデータ暗号化マスター キー (透過的なデータ暗号化プロテクターともいう) は、サーバー レベルで設定します。 Bring Your Own Key がサポートされた透過的なデータ暗号化を使用し、Key Vault のキーでデータベースを保護する場合は、ご利用のサーバーの透過的なデータ暗号化設定を確認してください。 

![Bring Your Own Key がサポートされた透過的なデータ暗号化](./media/transparent-data-encryption-azure-sql/tde-byok-support.png) 

## <a name="manage-transparent-data-encryption-by-using-powershell"></a>PowerShell を使用して透過的なデータ暗号化を管理する

PowerShell で透過的なデータ暗号化を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。 

| コマンドレット | [説明] |
| --- | --- |
| [Set-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) |データベースの透過的なデータ暗号化を有効または無効にします|
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) |データベースの透過的なデータ暗号化の状態を取得します |
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption-Activity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) |データベースの暗号化の進行状況を確認します |
| [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) |SQL Server インスタンスに Key Vault キーを追加します |
| [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) |SQL Server インスタンスの Key Vault キーを取得します  |
| [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) |SQL Server インスタンスに対して透過的なデータ暗号化プロテクターを設定します |
| [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) |透過的なデータ暗号化プロテクターを取得します |
| [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) |SQL Server インスタンスから Key Vault キーを削除します |
|  | |

## <a name="manage-transparent-data-encryption-by-using-transact-sql"></a>Transact-SQL を使用して透過的なデータ暗号化を管理する

管理者またはマスター データベースの **dbmanager** ロールのメンバーとしてログインし、データベースに接続します。

| コマンド | [説明] |
| --- | --- |
| [ALTER DATABASE (Azure SQL Database)](/sql/t-sql/statements/alter-database-azure-sql-database) | SET ENCRYPTION ON/OFF でデータベースを暗号化または暗号化解除します |
| [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) |データベースの暗号化の状態と、関連付けられているデータベース暗号化キーに関する情報を返します |
| [sys.dm_pdw_nodes_database_encryption_keys](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql) |各データ ウェアハウス ノードの暗号化状態と、関連付けられているデータベース暗号化キーに関する情報を返します | 
|  | |

Transact-SQL を使用して、Key Vault のキーに透過的なデータ暗号化プロテクターを切り替えることはできません。 PowerShell または Azure Portal を使用してください。

## <a name="manage-transparent-data-encryption-by-using-the-rest-api"></a>REST API を使用して透過的なデータ暗号化を管理する
 
REST API で透過的なデータ暗号化を構成するには、Azure の所有者、共同作成者、または SQL セキュリティ マネージャーとして接続する必要があります。 

| コマンド | [説明] |
| --- | --- |
|[サーバーの作成または更新](/rest/api/sql/servers/createorupdate)|SQL Server インスタンスに Azure Active Directory ID を追加します (Key Vault へのアクセスを許可するために使用)|
|[サーバー キーの作成または更新](/rest/api/sql/serverkeys/createorupdate)|SQL Server インスタンスに Key Vault キーを追加します|
|[サーバー キーの削除](/rest/api/sql/serverkeys/delete)|SQL Server インスタンスから Key Vault キーを削除します|
|[サーバー キーの取得](/rest/api/sql/serverkeys/get)|SQL Server インスタンスから特定の Key Vault キーを取得します|
|[サーバー キー一覧をサーバー別に取得](/rest/api/sql/serverkeys/listbyserver)|SQL Server インスタンスの Key Vault キーを取得します |
|[暗号化プロテクターの作成または更新](/rest/api/sql/encryptionprotectors/createorupdate)|SQL Server インスタンスに対して透過的なデータ暗号化プロテクターを設定します|
|[暗号化プロテクターの取得](/rest/api/sql/encryptionprotectors/get)|SQL Server インスタンスの透過的なデータ暗号化プロテクターを取得します|
|[暗号化プロテクター一覧をサーバー別に取得](/rest/api/sql/encryptionprotectors/listbyserver)|SQL Server インスタンスの透過的なデータ暗号化プロテクターを取得します |
|[Transparent Data Encryption 構成の作成または更新](/rest/api/sql/transparentdataencryptions/createorupdate)|データベースの透過的なデータ暗号化を有効または無効にします|
|[Transparent Data Encryption 構成の取得](/rest/api/sql/transparentdataencryptions/get)|データベースの透過的なデータ暗号化構成を取得します|
|[Transparent Data Encryption 構成結果一覧の取得](/rest/api/sql/transparentdataencryptionactivities/ListByConfiguration)|データベースの暗号化結果を取得します|

## <a name="next-steps"></a>次の手順

- 透過的なデータ暗号化の一般的な説明については、「[透過的なデータ暗号化 (TDE)](transparent-data-encryption.md)」を参照してください。
- SQL Database と Data Warehouse 用の Bring Your Own Key がサポートされた透過的なデータ暗号化の詳細については、「[Azure SQL Database および Data Warehouse 用の Bring Your Own Key (プレビュー) サポートによる Transparent Data Encryption](transparent-data-encryption-byok-azure-sql.md)」を参照してください。
- Bring Your Own Key がサポートされた透過的なデータ暗号化の使用を開始する場合は、方法ガイドの「[PowerShell: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする (プレビュー)](transparent-data-encryption-byok-azure-sql-configure.md)」を参照してください。
- Key Vault の詳細については、「[キー コンテナーのセキュリティ保護](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault)」を参照してください。
