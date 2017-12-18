---
title: TDE - Bring Your Own Key (BYOK) - Azure SQL | Microsoft Docs
description: "SQL Database および Data Warehouse に対する Azure Key Vault での Transparent Data Encryption (TDE) の Bring Your Own Key (BYOK) サポート。 BYOK を使用した TDE の概要、利点、しくみ、考慮事項、推奨事項。"
keywords: 
services: sql-database
documentationcenter: 
author: aliceku
manager: craigg
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: Inactive
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 11/15/2017
ms.author: aliceku
ms.openlocfilehash: 5a0b56974d85f63e3382f26b1388e7d30dfbd6f8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="transparent-data-encryption-with-bring-your-own-key-support-for-azure-sql-database-and-data-warehouse"></a>Azure SQL Database および Data Warehouse 用の Bring Your Own Key サポートによる Transparent Data Encryption
[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

[Transparent Data Encryption (TDE)](transparent-data-encryption.md) のための Bring Your Own Key (BYOK) サポートを利用すると、TDE 暗号化キーを管理できるようになり、キーにアクセスできるユーザーと時期を制限することができます。 Azure のクラウド ベースの外部キー管理システムである [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault) は、TDE により BYOK のサポートが統合された最初のキー管理サービスです。 BYOK がサポートされていると、データベース暗号化キーは Key Vault に格納されている非対称キーによって保護されます。 非対称キーはサーバー レベルで設定され、そのサーバーに存在するすべてのデータベースによって継承されます。 

BYOK のサポートにより、ユーザーは、キーのローテーション、キー コンテナーのアクセス許可、キーの削除、すべての暗号化キーの監査/レポートの有効化など、キー管理タスクを制御できるようになります。 Key Vault は、キーの集中管理機能を提供し、厳重に監視されたハードウェア セキュリティ モジュール (HSM) を利用して、キー管理とデータ管理の間で役割の分離を可能にすることにより規制のコンプライアンス対応を実現します。 

TDE と BYOK には、次のような利点があります。
- TDE プロテクターの自己管理による透明性の向上ときめ細かい制御   
- Key Vault でホストすることによる TDE 暗号化キー (および、他の Azure サービスで使われている他のキーとシークレット) の集中管理
- 組織内のキー管理ロールとデータ管理ロールの分離による役割の分離のサポート
- Key Vault は Microsoft が暗号化キーを参照または抽出しないように設計されているので、クライアントからの信頼の向上 
- キー ローテーションのサポート

> [!IMPORTANT]
> サービス管理 TDE を使っているユーザーが Key Vault を使い始める場合、Key Vault にキーを切り替える処理の間、TDE は有効状態を維持します。 ダウンタイムも、データベース ファイル自体の再暗号化もありません。 サービスで管理されたキーから Key Vault のキーへの切り替えにはデータベース暗号化キーの再暗号化が必要ですが、これは高速のオンライン操作です。
>

## <a name="how-does-tde-with-byok-support-work"></a>BYOK がサポートされた TDE の動作の仕組み
 
![サーバーから Key Vault への認証](./media/transparent-data-encryption-byok-azure-sql/tde-byok-server-authentication-flow.PNG)

Key Vault のキーを使うように TDE が構成されていると、サーバーは TDE が有効な各データベースのデータベース暗号化キーを Key Vault に送信して "*ラップ キー*" を要求します。 Key Vault は暗号化されたデータベース暗号化キーを返し、それはユーザー データベースに格納されます。 

重要な点は、**いったん Key Vault に格納されたキーが Key Vault の外に出ることはない**ということです。 ハードウェア セキュリティ モジュール (HSM) によってバックアップされた Key Vault のキーが、HSM のセキュリティ境界から外に出ることはありません。 サーバーは、Key Vault 内の TDE プロテクター キー マテリアルにキー操作要求を送信することだけができます。 Key Vault 管理者は、いつでもサーバーに対する Key Vault のアクセス許可を取り消すアクセス許可があり、取り消すと、サーバーへのすべての接続が切断されます。 

## <a name="considerations"></a>考慮事項

BYOK による TDE を使うと、新しいキー管理タスクが発生するだけでなく、Key Vault 自体を使うための関連コストがかかります。 これらの考慮事項について次の 2 つのセクションで説明します。

### <a name="key-management-responsibilities"></a>キー管理の責任

アプリケーションのリソースの暗号化キー管理を引き受けることは、重要な責任です。 Key Vault を利用して BYOK による TDE を使うときは、以下のキー管理タスクが想定されます。
- **キーのローテーション**: TDE プロテクターは、社内のポリシーやコンプライアンスの要件に従って、ローテーションする必要があります。 キーのローテーションは、TDE プロテクターの Key Vault を通して行うことができます。  
- **Key Vault のアクセス許可**: Key Vault 内のアクセス許可は、Key Vault とサーバー レベルでプロビジョニングされます。 Key Vault に対するサーバーのアクセス許可は、Key Vault のアクセス ポリシーを使っていつでも取り消すことができます。
- **キーの削除**: 安全性強化とコンプライアンス要件への対応のため、Key Vault と SQL Server からキーを削除することができます。
- **すべての暗号化キーの監査/レポート**: Key Vault が提供するログは、他のセキュリティ情報ツールやイベント管理 (SIEM) ツールに簡単に取り込むことができます。 Operations Management Suite (OMS) の [Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-azure-key-vault) は、既に統合されているサービスの 1 つの例です。

### <a name="pricing-considerations"></a>料金に関する考慮事項 

BYOK サポートによる TDE は、Azure SQL Database および Data Warehouse に追加料金なしで組み込まれているセキュリティ機能です。 ただし、Key Vault 自体の使用に関連するコストがあります。 サーバーによって行われる Key Vault の操作は、コンテナーに対する通常の操作と同じように請求され、Key Vault の[料金](https://azure.microsoft.com/pricing/details/key-vault/)に従います。 サーバーは、次のイベントに対して Key Vault に要求を送信します。
- SQL インスタンスの再起動
- キーのロールオーバー
- Key Vault に対するサーバーのアクセス許可に変更があったかどうかの 6 時間ごとの確認

## <a name="important-warnings"></a>重要な警告

### <a name="loss-of-access-to-keys"></a>キーへのアクセスの喪失

サーバーが TDE プロテクターへのアクセス権を失うと (Key Vault のアクセス許可の削除またはキーの削除によって)、**サーバーにある暗号化されたデータベースへのすべての接続がブロックされ、これらのデータベースはオフラインになり、24 時間以内に削除されます**。 使うことができなくなったキーで暗号化された古いバックアップにはアクセスできなくなりました。 キーが侵害された可能性がある場合 (サービスまたはユーザーがキーに不正アクセスしたなど)、「[PowerShell を使用して Transparent Data Encryption (TDE) プロテクターを削除する](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)」のガイドラインに従ってキーを削除するのが最善の方法です。 最大 10 分間のデータが失われる可能性を防ぐため、アクティブな TDE プロテクターを削除する前に、データベースを削除する必要があります。  

### <a name="expired-keys"></a>有効期限が切れたキー

TDE プロテクターの可用性はデータベースの可用性に直接影響を与えるため、有効期限のあるキーは SQL server に追加できません。 キーがサーバーの TDE プロテクターとして既に使われていて、このキーに Azure Key Vault で有効期限が後から設定された場合、**キーの有効期限が切れると、暗号化されたデータベースは TDE プロテクターへのアクセス権を失い、24 時間以内に削除されます**。

### <a name="deleted-server-identities"></a>削除されたサーバーの ID 

Key Vault へのサーバーのアクセスは、サーバーの一意の Azure Active Directory (AAD) ID によって管理されます。 したがって、サーバーの ID が AAD から削除されると、サーバーは Key Vault にアクセスできなくなります。 その結果、**サーバーにある暗号化されたデータベースへのすべての接続がブロックされ、これらのデータベースはオフラインになり、24 時間以内に削除されます**。

## <a name="limitations"></a>制限事項

TDE に使われる Key Vault は、SQL Database サーバーまたは Data Warehouse サーバーと同じ AAD テナントに存在する必要があります。 クロステナントのキー コンテナーとサーバー相互作用はサポートされていません。 Key Vault のキーで暗号化されたリソースを、Azure サブスクリプション間で移動することはできません。 サブスクリプション間でリソースを移動すると、BYOK による TDE を可能にしている必要な Key Vault のアクセス制御が壊れます。 リソースを別のサブスクリプションに移動する必要がある場合は、TDE のモードを BYOK から[サービス管理 TDE](transparent-data-encryption-azure-sql.md) に変更します。 

SQL Database または Data Warehouse に固有の TDE プロテクターはサポートされていません。 TDE プロテクターはサーバー レベルで設定され、そのサーバーのすべてのリソースによって継承されます。 

## <a name="guidelines-for-managing-encrypted-databases"></a>暗号化されたデータベースの管理に関するガイドライン

### <a name="high-availability-and-disaster-recovery"></a>高可用性とディザスター リカバリー
  
Key Vault を使用してサーバー用の geo レプリケーションを構成する方法には、次の 2 とおりがあります。 

- **個別の Key Vault**: 各サーバーが個別の Key Vault にアクセスします (理想的には、それぞれ独自の Azure リージョン内)。 これは、暗号化されて geo レプリケートされたデータベース用の TDE プロテクターの独自のコピーが各サーバーにあるので、推奨される構成です。 いずれかのサーバーの Azure リージョンがオフラインになった場合でも、他のサーバーは geo レプリケートされたデータベースに引き続きアクセスできます。   

- **共有 Key Vault**: すべてのサーバーが同じ Key Vault を共有します。 この構成はセットアップは簡単ですが、Key Vault のある Azure リージョンがオフラインになると、すべてのサーバーが、暗号化されて geo レプリケートされたデータベースまたは独自の暗号化されたデータベースを読み取ることができなくなります。 
 
最初に、[Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) コマンドレットを使って、各サーバーの Key Vault キーを geo レプリケーション リンク内の他のサーバーに追加します。  
(Key Vault の KeyId の例: *https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h*)

   ```powershell
   <# Include the version guid in the KeyId #>
   Add-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```

>[!NOTE]
>Key Vault 名とキー名を組み合わせた文字の長さが、94 文字を超えることはできません。
>

「[概要: フェールオーバー グループとアクティブ geo レプリケーション](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)」の手順に従って、これらのサーバーでアクティブ geo レプリケーションを構成し、フェールオーバーをトリガーします。  

### <a name="backup-and-restore"></a>バックアップと復元

Key Vault のキーを使って TDE でデータベースを暗号化した後は、生成されるバックアップも同じ TDE プロテクターで暗号化されます。

Key Vault から TDE プロテクターで暗号化されたバックアップを復元するには、キー マテリアルが元のコンテナーに元のキー名でまだ存在することを確認します。 データベースの TDE プロテクターが変更されても、データベースの古いバックアップが最新の TDE プロテクターを使うように更新されることは**ありません**。 したがって、データベースのバックアップを復元できるように、TDE プロテクターのすべての古いバージョンを Key Vault に残しておくことをお勧めします。 

バックアップの復元に必要なキーが元の Key Vault に残っていない場合は、次のエラー メッセージが返されます。"Target server <Servername> does not have access to all AKV Uris created between <Timestamp #1> and <Timestamp #2>. Please retry operation after restoring all AKV Uris." (ターゲット サーバー <サーバー名> は <タイムスタンプ #1> と <タイムスタンプ #2> の間に作成されたすべての AKV URI にアクセスできません。すべての AKV URI を復元した後で操作をやり直してください。)

これを軽減するには、[Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) コマンドレットを実行して、サーバーに追加された Key Vault からキーの一覧を取得します。 すべてのバックアップを復元できるようにするには、バックアップのターゲット サーバーがこれらのキーすべてにアクセスできることを確認してください。

   ```powershell
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
SQL Database のバックアップの復旧については、「[データベースの自動バックアップを使用した Azure SQL Database の復旧](https://docs.microsoft.com/azure/sql-database/sql-database-recovery-using-backups)」を参照してください。 SQL Data Warehouse のバックアップの復旧については、「[SQL Data Warehouse の復元](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-restore-database-overview)」を参照してください。

## <a name="best-practices"></a>ベスト プラクティス

### <a name="key-management"></a>キー管理 

すばやいキー復旧を確保し、Azure 以外のデータにアクセスできるようにするには、以下のことをお勧めします。
- ローカル HSM デバイスのローカルに暗号化キーを作成します (Azure Key Vault に格納できるように、必ず非対称の RSA 2048 キーを作成してください)。
- 暗号化キー ファイル (.pfx、.byok、または .backup) を Azure Key Vault にインポートします。 想定外のキー削除からの復旧保護のために、[論理的な削除](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete)が有効な Key Vault を使用することを検討してください。
- 初めて Azure Key Vault でキーを使用する前に、Azure Key Vault キーのバックアップを作成します。 詳細については、 [Backup-AzureKeyVaultKey](https://msdn.microsoft.com/library/mt126292.aspx) コマンドを参照してください。
- キーに何らかの変更を加える場合 (ACL の追加、タグの追加、キー属性の追加など) は常に、新しい Azure Key Vault キーのバックアップを作成してください。
- キーのロールオーバーでは、古いデータベース バックアップを復元できるように、Key Vault に**以前のバージョンのキーを残しておきます**。 

運用環境のシナリオでは、最初に TDE 暗号化キーをローカルに作成し、非対称キーをインポートする方法を強くお勧めします。このようにすると、管理者はキーをキー エスクロー システムに預託できます。 Azure Key Vault で非対称キーを作成した場合、秘密キーはコンテナーの外に出ることができないため、エスクローに預託することができません。 重要なデータの保護に使用するキーはエスクローに預託してください。 非対称キーを紛失すると、データが永久的に復元不能になります。

### <a name="pre-configuration-for-replicated-databases"></a>レプリケートされるデータベースの事前構成

暗号化されたデータベースを別のサーバーにレプリケートする場合は、データベースを移動またはレプリケートする**前**に、サーバーが他のサーバーで使われている Key Vault キー マテリアルのコピーにアクセスできることを確認します。  

各サーバーが別の Key Vault (理想的にはサーバーと同じ Azure リージョン内) に格納されている、他のサーバーで使われる Key Vault キー マテリアルのコピーにアクセスできるようにすることをお勧めします。 このセットアップでは、暗号化されてレプリケートされたデータベースの TDE プロテクターの独自のコピーが各サーバーにあります。 いずれかのサーバーの Azure リージョンがオフラインになった場合でも、他のサーバーはレプリケートされたデータベースに引き続きアクセスできます。

## <a name="next-steps"></a>次の手順

- TDE の Bring Your Own Key サポートの概要については、「[PowerShell: Enable Transparent Data Encryption using your own key from Azure Key Vault](transparent-data-encryption-byok-azure-sql-configure.md)」(PowerShell: Azure Key Vault から独自のキーを使用して Transparent Data Encryption を有効にする) を参照してください。
- セキュリティ ポリシーに準拠するようにサーバーの TDE プロテクターをローテーションする方法については、「[PowerShell を使用して Transparent Data Encryption (TDE) プロテクターをローテーションする](transparent-data-encryption-byok-azure-sql-key-rotation.md)」を参照してください。
- セキュリティ インシデントが発生した場合、侵害された可能性のある TDE プロテクターを削除する方法については、「[PowerShell を使用して Transparent Data Encryption (TDE) プロテクターを削除する](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)」を参照してください。 
