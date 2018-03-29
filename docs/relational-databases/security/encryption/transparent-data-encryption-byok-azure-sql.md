---
title: TDE - Bring Your Own Key (BYOK) - Azure SQL | Microsoft Docs
description: SQL Database および Data Warehouse に対する Azure Key Vault での Transparent Data Encryption (TDE) の Bring Your Own Key (BYOK) サポート。 BYOK を使用した TDE の概要、利点、しくみ、考慮事項、推奨事項。
keywords: ''
services: sql-database
documentationcenter: ''
author: aliceku
manager: craigg
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: ''
ms.component: security
ms.workload: On Demand
ms.tgt_pltfrm: ''
ms.devlang: na
ms.topic: article
ms.date: 03/16/2018
ms.author: aliceku
ms.openlocfilehash: ae89e8496ce8f2aec87d80e36ce7b48acfd6a8cf
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="transparent-data-encryption-with-bring-your-own-key-preview-support-for-azure-sql-database-and-data-warehouse"></a>Azure SQL Database および Data Warehouse 用の Bring Your Own Key (プレビュー) サポートによる Transparent Data Encryption
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

[Transparent Data Encryption (TDE)](transparent-data-encryption.md) のための Bring Your Own Key (BYOK) サポートを利用すると、TDE プロテクターと呼ばれる非対称キーを使って、データベース暗号化キー (DEK) を暗号化できます。  TDE プロテクターは、Azure のクラウドベースの外部キー管理システムである [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault) のコントロールに格納されます。 Azure Key Vault は、TDE により BYOK のサポートが統合された最初のキー管理サービスです。 TDE の DEK は、データベースのブート ページに格納され、TDE プロテクターによって暗号化および複合化されます。 TDE プロテクターは、Azure Key Vault に格納され、そのキー コンテナーの外へ移動されることはありません。 キー コンテナーへのサーバーのアクセス権が取り消された場合、データベースを複合化して、メモリに読み込むことはできません。  TDE プロテクターは、論理サーバー レベルで設定され、そのサーバーと関連付けられているすべてのデータベースによって継承されます。 

BYOK のサポートにより、ユーザーは、Azure Key Vault 機能を使用して、キーのローテーション、キー コンテナーのアクセス許可、キーの削除、すべての TDE の監査/レポートの有効化など、キー管理タスクを制御できるようになります。 Key Vault は、キーの集中管理機能を提供し、厳重に監視されたハードウェア セキュリティ モジュール (HSM) を利用して、キー管理とデータ管理の間で役割の分離を可能にすることにより規制のコンプライアンス対応を実現します。  


TDE と BYOK には、次のような利点があります。
- TDE プロテクターの自己管理による透明性の向上ときめ細かい制御   
- Key Vault でホストすることによる TDE プロテクター (および、他の Azure サービスで使われている他のキーとシークレット) の集中管理
- 組織内のキー管理とデータ管理の責任の分離による役割の分離のサポート
- Key Vault は Microsoft が暗号化キーを参照または抽出しないように設計されているので、クライアントからの信頼の向上 
- キー ローテーションのサポート

> [!IMPORTANT]
> サービス管理 TDE を使っているユーザーが Key Vault を使い始める場合、Key Vault の TDE プロテクターを切り替える処理の間、TDE は有効状態を維持します。 ダウンタイムも、データベース ファイルの再暗号化もありません。 サービスで管理されたキーから Key Vault のキーへの切り替えには、データベース暗号化キー (DEK) の再暗号化のみが必要ですが、これは高速のオンライン操作です。 
>

## <a name="how-does-tde-with-byok-support-work"></a>BYOK がサポートされた TDE の動作の仕組み
 
![サーバーから Key Vault への認証](./media/transparent-data-encryption-byok-azure-sql/tde-byok-server-authentication-flow.PNG)

最初に TDE が Key Vault から TDE プロテクターを使うように構成されていると、サーバーは TDE が有効な各データベースの DEK を Key Vault に送信して、ラップ キーを要求します。 Key Vault は暗号化されたデータベース暗号化キーを返し、それはユーザー データベースに格納されます。  

>[!IMPORTANT]
>重要な点は、**いったん TDE プロテクターが Azure Key Vault に格納されると、Azure Key Vault の外に移動されることはない**ということです。 論理サーバーは、Key Vault 内の TDE プロテクター キー マテリアルにキー操作要求を送信できるだけで、**TDE プロテクターにアクセスしたり、TDE プロテクターをキャッシュしたりすることはありません**。 Key Vault 管理者は、いつでもサーバーの Key Vault のアクセス許可を取り消すアクセス許可があり、取り消すと、サーバーへのすべての接続が切断されます。 
>


## <a name="guidelines-for-configuring-tde-with-byok"></a>BYOK を使用した TDE 構成に関するガイドライン

### <a name="general-guidelines"></a>一般的なガイドライン
- Azure Key Vault と Azure SQL Database が、同じテナント内にあることを確認します。  クロステナントのキー コンテナーとサーバー相互作用は、**サポートされていません**。
- 必要なリソースに使用されるサブスクリプションを決定します。サブスクリプション間のサーバーの移動には、後で BYOK を使用して TDE の新しいセットアップを行う必要があります。
- BYOK で TDE を構成するときは、ラップ/ラップ解除操作の繰り返しによってキー コンテナーにかかる負荷を考慮することが重要です。 たとえば、論理サーバーに関連付けられているすべてのデータベースは同じ TDE プロテクターを使うため、そのサーバーでフェールオーバーが発生すると、サーバー内のデータベースと同じ数のキー操作がコンテナーに対してトリガーされます。 これまでの実績から、また[キー コンテナー サービスの制限](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-service-limits)に記されている内容から、コンテナー内の TDE プロテクターへのアクセスに対して常に高い可用性を保証するには、1 つのサブスクリプションの 1 つの Azure Key Vault に関連付けるデータベースの数を、Standard データベースで最大 500 個、Premium データベースで最大 200 個にすることをお勧めします。 
- 推奨: TDE プロテクターのコピーはオンプレミスで保持してください。  これには、ローカルに TDE プロテクターを作成するために HSM デバイスが必要で、TDE プロテクターのローカル コピーを格納するためにキー エスクロー システムが必要です。


### <a name="guidelines-for-configuring-azure-key-vault"></a>Azure Key Vault の構成に関するガイドライン

- キー (または、キー コンテナー) を誤って削除した場合に、データの損失を防ぐには、[論理削除](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete)を有効にしたキー コンテナーを使用します。  
  - 論理削除のリソースは、一定の期間保持されます。復旧や消去が行われない限り、その期間は 90 日間です。
  - **復旧**と**消去**アクションには、キー コンテナーのアクセス ポリシーに関連付けられた独自のアクセス許可があります。 
- Azure Active Directory (Azure AD) の ID を使用して、キー コンテナーへのアクセス権を論理サーバーに付与します。  ポータルの UI を使用すると、Azure AD の ID が自動的に作成され、キー コンテナーのアクセス許可がそのサーバーに付与されます。  BYOK で TDE を構成するために PowerShell を使用すると、Azure AD の ID が作成され、完了が確認されます。 PowerShell を使用するときの詳しいステップバイステップのガイダンスについては、「[BYOK での TDE の構成](transparent-data-encryption-byok-azure-sql-configure.md)」を参照してください。

  >[!NOTE]
  >Azure AD の ID **が誤って削除されたり、キー コンテナーのアクセス ポリシーを使用してサーバーのアクセス許可が取り消されたりした**場合、そのサーバーはキー コンテナーへのアクセス権を失います。
  >
  
- すべての暗号化キーの監査とレポートを有効にする: Key Vault が提供するログは、他のセキュリティ情報ツールやイベント管理 (SIEM) ツールに簡単に挿入することができます。 Operations Management Suite (OMS) の [Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-azure-key-vault) は、既に統合されているサービスの 1 つの例です。
- 暗号化されたデータベースの高可用性を確実にするには、各論理サーバーを異なるリージョンに存在する 2 つの Azure Key Vault で構成します。


### <a name="guidelines-for-configuring-the-tde-protector-asymmetric-key-stored-in-azure-key-vault"></a>Azure Key Vault に格納された TDE プロテクター (非対称キー) の構成に関するガイドライン

- ローカル HSM デバイスのローカルに暗号化キーを作成します Azure Key Vault に格納できるように、非対称の RSA 2048 キーであることを確認してください。
- キー エスクロー システムのキーをエスクローします。  
- 暗号化キー ファイル (.pfx、.byok、または .backup) を Azure Key Vault にインポートします。 
    

>[!NOTE] 
    >テスト目的で、Azure Key Vault を使ってキーを作成できます。ただし、秘密キーはキー コンテナーの外へ移動できないため、このキーをエスクローすることはできません。  キーを損失すると (キー コンテナーでの誤削除、有効期限切れなど)、永続的にデータが失われるので、実稼働データの暗号化に使用するキーを常にバックアップしエスクローします。
    >
    
- 有効期限なしのキーを使用する (また、既に使用されているキーに有効期限を設定しない): **キーの有効期限が切れると、暗号化されたデータベースは、TDE プロテクターへのアクセス権を失い、24 時間以内に削除されます**。
- キーが有効であり、*get*、*wrap key*、および *unwrap key* 操作を実行するアクセス許可があることを確認します。
- 初めて Azure Key Vault でキーを使用する前に、Azure Key Vault キーのバックアップを作成します。 詳細については、 [Backup-AzureKeyVaultKey](https://docs.microsoft.com/en-us/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey?view=azurermps-5.1.1) コマンドを参照してください。
- キーに何らかの変更を加える場合 (ACL の追加、タグの追加、キー属性の追加など) は常に、新しいバックアップを作成します。
- 古いデータベース バックアップを復元できるように、キーをローテーションするときは、キー コンテナーに**以前のバージョンのキーを残しておきます**。 データベースの TDE プロテクターが変更されても、データベースの以前のバックアップが最新の TDE プロテクターを使うように**更新されることはありません**。  バックアップごとに、復元時に作成された TDE プロテクターが必要です。 キー ローテーションは、「[PowerShell を使用して Transparent Data Encryption (TDE) プロテクターをローテーションする](transparent-data-encryption-byok-azure-sql-key-rotation.md)」の手順に従って実行できます。
- サービス管理キーに戻した後、Azure Key Vault に以前に使用したキーをすべて保持します。  これにより、Azure Key Vault に格納された TDE プロテクターを使って、データベースのバックアップを復元できます。  Azure Key Vault で作成された TDE プロテクターは、すべての格納されたバックアップが、サービス管理キーで作成されるまで保持する必要があります。  
- [Backup-AzureKeyVaultKey](https://docs.microsoft.com/en-us/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey?view=azurermps-5.1.1) を使用して、これらのキーの回復可能なバックアップ コピーを作成します。
- データを損失する危険を伴わずに、セキュリティ上の問題が発生したときに侵害された可能性のあるキーを削除するには、[侵害された可能性があるキーの削除](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)に関するページの手順に従ってください。


## <a name="high-availability-geo-replication-and-backup--restore"></a>高可用性、geo レプリケーション、バックアップ/復元

### <a name="high-availability-and-disaster-recovery"></a>高可用性とディザスター リカバリー

Azure Key Vault で高可用性を構成する方法は、使用しているデータベースと論理サーバーの構成によって異なります。2 つの個別のケースで推奨される構成は、次のとおりです。  最初のケースは、geo 冗長を構成していないスタンドアロンのデータベースまたは論理サーバーの場合です。  2 つ目のケースは、フェールオーバー グループまたは geo 冗長を構成したデータベースまたは論理サーバーです。このケースでは、geo フェールオーバーが機能するように、各 geo 冗長のコピーには、フェールオーバー グループ内のローカルの Azure Key Vault が含まれる必要があります。 最初のケースで、geo 冗長を構成していないデータベースおよび論理サーバーの高可用性が必要な場合は、同じキー マテリアルを含む 2 つの別のリージョン内の 2 つの異なるキー コンテナーを使用するように、サーバーを構成することを強くお勧めします。  これは、論理サーバーとして同じサーバーに併置されたプライマリ Key Vault を使用する TDE プロテクターを作成し、異なる Azure リージョンのキー コンテナーにキーを複製すると実現できます。これにより、データベースの稼働中にプライマリ キー コンテナーが停止した場合、サーバーは第 2 キー コンテナーへのアクセス権を持つことができます。 Backup-AzureKeyVaultKey コマンドレットを使用して、プライマリ キー コンテナーから暗号化された形式のキーを取得し、Restore-AzureKeyVaultKey コマンドレットを使用して、第 2 リージョンのキー コンテナーを指定します。


![1 つのサーバーの高可用性および geo-DR なし](./media/transparent-data-encryption-byok-azure-sql/SingleServer_HA_Config.PNG)

2 つ目のケースでは、Azure Key Vault 内の TDE プロテクターの高可用性を維持するために、既存の SQL Database フェールオーバー グループまたはデータベースのアクティブ geo レプリケーションのコピーに基づいて、冗長な Azure Key Vault を構成する必要があります。  geo レプリケーションされたサーバーごとに、個別のキー コンテナーが必要で、同じ Azure リージョンにそのサーバーとして併置するのが理想的です。 プライマリ データベースは、1 つのリージョンの停止のためにアクセス不可になり、フェールオーバーがトリガーされた場合は、セカンダリ データベースが、セカンダリ キー コンテナーを使用して引き継ぐことができます。  

![グループと geo-DR のフェールオーバー](./media/transparent-data-encryption-byok-azure-sql/Geo_DR_Config.PNG)

フェールオーバー中に Azure Key Vault 内の TDE プロテクターに継続的にアクセスできるようにするには、データベースをセカンダリ サーバーに複製またはフェールオーバーする前に、これを構成する必要があります。 プライマリ サーバーとセカンダリ サーバーの両方で、その他すべての Azure Key Vault に TDE プロテクターのコピーを格納する必要があります。つまり、この例では、同じキーが両方のキー コンテナーに格納されるということです。

geo-DR のシナリオでの冗長性のためにはセカンダリ キー コンテナーを備えたセカンダリ データベースが必要であり、最大で 4 つのセカンダリがサポートされます。  チェーンつまりセカンダリに対するセカンダリの作成はサポートされていません。  初期セットアップ時に、サービスは、プライマリ キー コンテナーとセカンダリ キー コンテナーの両方に対してアクセス許可が正しく設定されていることを確認します。  これらのアクセス許可を維持し、適用されていることを定期的にテストすることが重要です。

>[!NOTE]
>プライマリとセカンダリのサーバーにサーバー ID を割り当てるときは、最初にセカンダリ サーバーに ID を割り当てる必要があります。
>

キー コンテナーの既存のキーを別のキー コンテナーに追加するには、[Add-AzureRmSqlServerKeyVaultKey](https://docs.microsoft.com/en-us/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) コマンドレットを使用します。

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

これを軽減するには、[Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) コマンドレットを実行して、サーバーに追加された Key Vault からキーの一覧を取得します (ユーザーによって削除された場合を除く)。 すべてのバックアップを復元できるようにするには、バックアップの対象サーバーがこれらのキーすべてにアクセスできることを確認します。

   ```powershell
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
SQL Database のバックアップの復旧については、「[データベースの自動バックアップを使用した Azure SQL Database の復旧](https://docs.microsoft.com/azure/sql-database/sql-database-recovery-using-backups)」を参照してください。 SQL Data Warehouse のバックアップの復旧については、「[SQL Data Warehouse の復元](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-restore-database-overview)」を参照してください。


バックアップ ログ ファイルに関するその他の考慮事項: TDE プロテクターがローテーションされて、データベースが新しい TDE プロテクターを使うようになっている場合でも、バックアップ ログ ファイルは元の TDE 暗号化機能で暗号化されたままです。  復元時に、データベースを復元するには両方のキーが必要になります。  途中でデータベースがサービス管理 TDE を使うように変更された場合でも、ログ ファイルが Azure Key Vault に格納されている TDE プロテクターを使っている場合は、復元時にこのキーが必要になります。


