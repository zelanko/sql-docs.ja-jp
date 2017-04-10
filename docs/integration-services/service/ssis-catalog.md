---
title: "SSIS カタログ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# SSIS カタログ
  **SSISDB** カタログは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置した [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) プロジェクトを操作するための中核となります。 たとえば、プロジェクト パラメーターとパッケージ パラメーターの設定、パッケージに合わせたランタイム値を指定するための環境の構成、パッケージの実行およびトラブルシューティング、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバー操作の管理を行います。  
  
 **SSISDB** カタログに格納されているオブジェクトには、プロジェクト、パッケージ、パラメーター、環境、および操作履歴があります。  
  
 **SSISDB** カタログに格納されているオブジェクト、設定、および業務データを検査するには、 **SSISDB** データベースのビューに対してクエリを実行します。 オブジェクトを管理するには、 **SSISDB** データベースのストアド プロシージャを呼び出すか、 **SSISDB** カタログの UI を使用します。 多くの場合、UI でもストアド プロシージャの呼び出しでも同じタスクを実行できます。  
  
 **SSISDB** データベースを保守するには、ユーザー データベースの管理に標準的なエンタープライズ ポリシーを適用することをお勧めします。 メンテナンス プランの作成については、「 [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md)」をご覧ください。  
  
 **SSISDB** カタログおよび **SSISDB** データベースは、Windows PowerShell をサポートしています。 Windows PowerShell による SQL Server の使用の詳細については、「 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)」をご覧ください。 Windows PowerShell を使用してプロジェクトの配置などのタスクを実行する方法の例については、blogs.msdn.com のブログ エントリ「 [SQL Server 2012 での SSIS と PowerShell](http://go.microsoft.com/fwlink/?LinkId=242539)」をご覧ください。  
  
 操作データの表示に関する詳細については、「 [パッケージとその他の操作を実行するモニター](../../integration-services/performance/monitor-running-packages-and-other-operations.md)」をご覧ください。  
  
 **の** SSISDB [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] カタログにアクセスするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンに接続し、オブジェクト エクスプローラーで **[Integration Services カタログ]** ノードを展開します。 **で** SSISDB [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] データベースにアクセスするには、オブジェクト エクスプローラーで [データベース] ノードを展開します。  
  
> [!NOTE] **SSISDB** データベースの名前は変更できません。  
  
> [!NOTE] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSISDB **データベースがアタッチされている** インスタンスが停止したか、応答しない場合、ISServerExec.exe プロセスは終了します。 メッセージが Windows イベント ログに書き込まれます。  
>   
>  クラスター フェールオーバーの一環として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースがフェールオーバーした場合、実行中のパッケージは再開されません。 チェックポイントを使用してパッケージを再開できます。 詳細については、「 [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md)」を参照してください。  
  
## <a name="in-this-topic"></a>このトピックの内容  
  
-   [カタログ オブジェクト識別子](../../integration-services/service/ssis-catalog.md#CatalogObjectIdentifiers)  
  
-   [カタログの構成](../../integration-services/service/ssis-catalog.md#Configuration)  
  
-   [アクセス許可](../../integration-services/service/ssis-catalog.md#Permissions)  
  
-   [フォルダー](../../integration-services/service/ssis-catalog.md#Folders)  
  
-   [プロジェクトとパッケージ](../../integration-services/service/ssis-catalog.md#ProjectsAndPackages)  
  
-   [パラメーター](../../integration-services/service/ssis-catalog.md#Parameters)  
  
-   [サーバー環境、サーバー変数、およびサーバー環境参照](../../integration-services/service/ssis-catalog.md#ServerEnvironments)  
  
-   [実行と検証](../../integration-services/service/ssis-catalog.md#Executions)  
  
-   [AlwaysOn のサポート](../../integration-services/service/ssis-catalog.md#AlwaysOn)  
  
-   [関連タスク](../../integration-services/service/ssis-catalog.md#RelatedTasks)  
  
-   [関連コンテンツ](../../integration-services/service/ssis-catalog.md#RelatedContent)  
  
##  <a name="a-namecatalogobjectidentifiersa-catalog-object-identifiers"></a><a name="CatalogObjectIdentifiers"></a> カタログ オブジェクト識別子  
 カタログに新しいオブジェクトを作成するときは、オブジェクトに名前を割り当てる必要があります。 オブジェクト名が識別子となります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、識別子に使用できる文字のルールが定義されています。 次のオブジェクトの名前は、識別子のルールに従っている必要があります。  
  
-   フォルダー  
  
-   プロジェクト  
  
-   環境  
  
-   パラメーター  
  
-   環境変数  
  
###  <a name="a-namefoldera-folder-project-environment"></a><a name="Folder"></a> フォルダー、プロジェクト、環境  
 フォルダー、プロジェクト、または環境の名前を変更するときは、次のルールを考慮します。  
  
-   無効な文字には、ASCII/Unicode 文字 1 ～ 31、引用符 (")、小なり (\<)、大なり (>)、パイプ (|)、バックスペース (\b)、null (\0)、タブ (\t) などがあります。  
  
-   名前の先頭または末尾にスペースを含めることはできません。  
  
-   名前を @ で始めることはできませんが、先頭以外では @. を使用できます。  
  
-   名前の長さは 1 ～ 128 文字にする必要があります。  
  
###  <a name="a-nameparametera-parameter"></a><a name="Parameter"></a> パラメーター  
 パラメーターに名前を付けるときは、次のルールを考慮します。  
  
-   名前の最初の文字は、Unicode Standard 2.0 に定義されている文字か、アンダースコア (_) である必要があります。  
  
-   2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (_) を使用できます。  
  
###  <a name="a-nameenvironmentvariablea-environment-variable"></a><a name="EnvironmentVariable"></a> 環境変数  
 環境変数に名前を付けるときは、次のルールを考慮します。  
  
-   無効な文字には、ASCII/Unicode 文字 1 ～ 31、引用符 (")、小なり (\<)、大なり (>)、パイプ (|)、バックスペース (\b)、null (\0)、タブ (\t) などがあります。  
  
-   名前の先頭または末尾にスペースを含めることはできません。  
  
-   名前を @ で始めることはできませんが、先頭以外では @. を使用できます。  
  
-   名前の長さは 1 ～ 128 文字にする必要があります。  
  
-   名前の最初の文字は、Unicode Standard 2.0 に定義されている文字か、アンダースコア (_) である必要があります。  
  
-   2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (_) を使用できます。  
  
##  <a name="a-nameconfigurationa-catalog-configuration"></a><a name="Configuration"></a> カタログの構成  
 カタログ プロパティを調整することによって、カタログの動作を微調整します。 カタログ プロパティは、機微なデータを暗号化する方法と、操作およびプロジェクトのバージョン管理データを保持する方法を定義します。 カタログ プロパティを設定するには、**[カタログのプロパティ]** ダイアログ ボックスを使用するか、[catalog.configure_catalog (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md) ストアド プロシージャを呼び出します。 プロパティを表示するには、ダイアログ ボックスまたはクエリ [catalog.catalog_properties (SSISDB Database)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) を使用します。 ダイアログ ボックスには、オブジェクト エクスプローラーで **SSISDB** を右クリックしてアクセスできます。  
  
###  <a name="a-namecleanupa-operations-and-project-version-cleanup"></a><a name="Cleanup"></a> 操作とプロジェクト バージョンのクリーンアップ  
 カタログの多くの操作の状態データは、内部データベース テーブルに格納されます。 たとえば、カタログではパッケージの実行とプロジェクトの配置の状態が追跡されます。 操作データのサイズを維持するには、 **の** SSIS サーバー メンテナンス ジョブ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して古いデータを削除します。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインストール時に作成されます。  
  
 同じ名前の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトをカタログの同じフォルダーに配置することで、このプロジェクトを更新または再配置できます。 既定では、プロジェクトを再配置するたびに、 **SSISDB** カタログには以前のバージョンのプロジェクトが保持されます。 操作データのサイズを維持するには、 **SSIS サーバー メンテナンス ジョブ** を使用して古いバージョンのプロジェクトを削除します。  
 
**SSIS サーバー メンテナンス ジョブ**を実行するために、SSIS で SQL Server ログイン **##MS_SSISServerCleanupJobLogin##** が作成されます。 このログインは SSIS による内部使用専用です。
  
 次の **SSISDB** カタログ プロパティで、この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの動作を定義します。 **[カタログ プロパティ]** ダイアログ ボックスを利用するか、[catalog.catalog_properties (SSISDB データベース)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) と [catalog.configure_catalog (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md) を利用し、プロパティを表示し、変更できます。  
  
 **ログを定期的に消去する**  
 このプロパティが **True**に設定されている場合は、操作のクリーンアップのジョブ ステップが実行されます。  
  
 **保有期間 (日)**  
 操作データの最大保有期間を日数で定義します。 この期間を経過したデータは削除されます。  
  
 最小値は 1 日です。 最大値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **int** データ型の最大値によってのみ制限されます。 このデータ型に関する詳細については、「[int、bigint、smallint、および tinyint (Transact-SQL)](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)」を参照してください。  
  
 **古いバージョンを定期的に削除する**  
 このプロパティが **True**に設定されている場合は、プロジェクト バージョンのクリーンアップのジョブ ステップが実行されます。  
  
 **プロジェクトごとのバージョンの最大数**  
 カタログに格納されるプロジェクトのバージョンの数を定義します。 この数を超える古いバージョンのプロジェクトは削除されます。  
  
###  <a name="a-nameencryptiona-encryption-algorithm"></a><a name="Encryption"></a> 暗号化アルゴリズム  
 **[暗号化アルゴリズム]** プロパティでは、秘密性の高いパラメーター値を暗号化するために使用される暗号化の種類を指定します。 次の暗号化の種類から選択できます。  
  
-   AES_256 (既定値)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]サーバーに配置する場合、カタログは自動的にパッケージのデータと重要な値を暗号化します。 また、ユーザーがデータを取得するときには、自動的に暗号化を解除します。 SSISDB カタログは、 **ServerStorage** 保護レベルを使用します。 詳しくは、「 [Access Control for Sensitive Data in Packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)」をご覧ください。  
  
 暗号化アルゴリズムの変更は、時間のかかる操作です。 最初に、サーバーで以前に指定したアルゴリズムを使用して、すべての構成値の暗号化を解除する必要があります。 次に、新しいアルゴリズムを使用して、その値を再暗号化する必要があります。 この間、サーバーで他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 操作を実行できません。 そのため、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 操作を途切れることなく続行できるように、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]では、暗号化アルゴリズムが読み取り専用の値になっています。  
  
 **[暗号化アルゴリズム]** プロパティの設定を変更するには、 **SSISDB** データベースをシングル ユーザー モードに設定し、catalog.configure_catalog ストアド プロシージャを呼び出します。 *property_name* 引数の ENCRYPTION_ALGORITHM を使用します。 プロパティの値の詳細については、「[catalog.catalog_properties (SSISDB データベース)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)」を参照してください。 ストアド プロシージャの詳細については、「[catalog.configure_catalog (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md)」を参照してください。  
  
 シングル ユーザー モードの詳細については、「[データベースをシングル ユーザー モードに設定する](../../relational-databases/databases/set-a-database-to-single-user-mode.md)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の暗号化と暗号化アルゴリズムの詳細については、「 [SQL Server の暗号化](../../relational-databases/security/encryption/sql-server-encryption.md)」のトピックを参照してください。  
  
 暗号化にはデータベース マスター キーが使用されます。 このキーは、カタログの作成時に作成されます。 詳細については、「 [SSIS カタログの作成](../../integration-services/service/create-the-ssis-catalog.md)」を参照してください。  
  
 次の表では、 **[カタログのプロパティ]** ダイアログ ボックスに示されるプロパティ名と、データベース ビュー内の対応するプロパティについて説明します。  
  
|プロパティ名 (**[カタログのプロパティ]** ダイアログ ボックス)|プロパティ名 (データベース ビュー)|  
|---------------------------------------------------------|-------------------------------------|  
|暗号化アルゴリズムの名前|ENCRYPTION_ALGORITHM|  
|ログを定期的に消去する|OPERATION_CLEANUP_ENABLED|  
|保有期間 (日)|RETENTION_WINDOW|  
|古いバージョンを定期的に削除する|VERSION_CLEANUP_ENABLED|  
|プロジェクトごとのバージョンの最大数|MAX_PROJECT_VERSIONS|  
|サーバー全体の既定のログ記録レベル|SERVER_LOGGING_LEVEL|  
  
##  <a name="a-namepermissionsa-permissions"></a><a name="Permissions"></a> アクセス許可  
 プロジェクト、環境、およびパッケージは、セキュリティ保護可能なオブジェクトであるフォルダーに格納されます。 MANAGE_OBJECT_PERMISSIONS 権限などのフォルダーに対する権限を許可することができます。 MANAGE_OBJECT_PERMISSIONS を許可すると、ユーザーに ssis_admin ロールのメンバーシップを許可しなくても、フォルダー内容の管理をユーザーに委任できます。 プロジェクト、環境、および操作に権限を付与することもできます。 操作には、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]の初期化、プロジェクトの配置、実行の作成および開始、プロジェクトおよびパッケージの検証、 **SSISDB** カタログの構成などがあります。  
  
 データベース ロールの詳細については、「 [データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)」を参照してください。  
  
 SSISDB カタログでは、DDL トリガーの ddl_cleanup_object_permissions を使用して、SSIS のセキュリティ保護可能なリソースの権限情報の整合性を保ちます。 このトリガーは、データベース ユーザー、データベース ロール、データベース アプリケーション ロールなどのデータベース プリンシパルが SSISDB データベースから削除されたときに起動します。  
  
 このプリンシパルによって他のプリンシパルに権限が許可または拒否されている場合は、プリンシパルを削除する前に、権限の許可者が付与した権限を取り消してください。 取り消していない場合は、プリンシパルの削除が試行されるとエラー メッセージが返されます。 トリガーでは、データベース プリンシパルが権限付与対象ユーザーであるすべての権限レコードが削除されます。  
  
 トリガーは無効にしないことをお勧めします。これは、データベース プリンシパルが **SSISDB** データベースから削除された後に孤立した権限レコードが存在しないようにするためです。  
  
### <a name="managing-permissions"></a>権限の管理  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] UI、ストアド プロシージャ、 <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間を利用し、権限を管理できます。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の UI を使って権限を管理するには、次のダイアログ ボックスを使用します。  
  
-   フォルダーを使用して、 **権限** のページ、 [Folder Properties Dialog Box](../../integration-services/service/folder-properties-dialog-box.md)します。  
  
-   プロジェクトの場合は、 **権限** の [Project Properties Dialog Box](../../integration-services/service/project-properties-dialog-box.md)します。  
  
-   環境では、使用、 **権限** ページで、 [NIB: [環境のプロパティ] ダイアログ ボックスに関する記事](assetId:///6a91a8d4-0006-4cfd-9759-3e4295ae452b)します。  
  
 Transact-SQL を利用して権限を管理するには、[catalog.grant_permission (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)、[catalog.deny_permission (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md)、[catalog.revoke_permission (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md) を呼び出します。 すべてのオブジェクトの現在のプリンシパルで有効な権限を表示するには、[catalog.effective_object_permissions (SSISDB データベース)](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md) にクエリを実行します。 このトピックでは、さまざまな種類の権限について説明します。 ユーザーに明示的に割り当てられている権限を表示するには、[catalog.explicit_object_permissions (SSISDB データベース)](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md) にクエリを実行します。  
  
##  <a name="a-namefoldersa-folders"></a><a name="Folders"></a> フォルダー  
 フォルダーには、 **SSISDB** カタログ内の 1 つ以上のプロジェクトおよび環境が含まれます。 [catalog.folders (SSISDB データベース)](../../integration-services/system-views/catalog-folders-ssisdb-database.md) ビューを使用して、カタログのフォルダーに関する情報にアクセスできます。 次のストアド プロシージャを使用して、フォルダーを管理することができます。  
  
-   [catalog.create_folder &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
  
-   [catalog.delete_folder &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
  
-   [catalog.rename_folder &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
  
-   [catalog.set_folder_description &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
  
##  <a name="a-nameprojectsandpackagesa-projects-and-packages"></a><a name="ProjectsAndPackages"></a> プロジェクトとパッケージ  
 各プロジェクトには、複数のパッケージを含めることができます。 プロジェクトとパッケージの両方に、パラメーターおよび環境への参照を含めることができます。 [Configure Dialog Box](../../integration-services/service/configure-dialog-box.md)を使用して、パラメーターおよび環境への参照にアクセスできます。  
  
 次のストアド プロシージャを呼び出して、他のプロジェクト タスクを実行することができます。  
  
-   [catalog.delete_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
  
-   [catalog.deploy_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
  
-   [catalog.get_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
  
-   [catalog.move_project &#40;&#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-move-project-ssisdb-database.md)  
  
-   [catalog.restore_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
  
 次のビューには、パッケージ、プロジェクト、およびプロジェクトのバージョンに関する詳細が表示されます。  
  
-   [catalog.projects &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
  
-   [catalog.packages &#40;SSISDB データ&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
  
-   [catalog.object_versions &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
  
##  <a name="a-nameparametersa-parameters"></a><a name="Parameters"></a> パラメーター  
 パラメーターを使用して、パッケージの実行時にパッケージ プロパティに値を割り当てます。 パッケージまたはプロジェクト パラメーターの値を設定したり、値を消去したりするには、[catalog.set_object_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md) と [catalog.clear_object_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md) を呼び出します。 実行のインスタンスのパラメーターの値を設定するには、[catalog.set_execution_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md) を呼び出します。 [catalog.get_parameter_values (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md) を呼び出すことで既定のパラメーター値を取得できます。  
  
 次のビューには、すべてのパッケージとプロジェクトのパラメーター、および実行のインスタンスに使用されるパラメーター値が表示されます。  
  
-   [catalog.object_parameters &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
  
-   [catalog.execution_parameter_values &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
  
##  <a name="a-nameserverenvironmentsa-server-environments-server-variables-and-server-environment-references"></a><a name="ServerEnvironments"></a> サーバー環境、サーバー変数、およびサーバー環境参照  
 サーバー環境にはサーバー変数が含まれます。 変数値は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーでパッケージを実行または検証するときに使用できます。  
  
 次のストアド プロシージャを使用すると、環境と変数の他の多くの管理タスクを実行することができます。  
  
-   [catalog.create_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
  
-   [catalog.delete_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
  
-   [catalog.move_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
  
-   [catalog.rename_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
  
-   [catalog.set_environment_property &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
  
-   [catalog.create_environment_variable &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
  
-   [catalog.delete_environment_variable &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_property &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_value &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
  
 [catalog.set_environment_variable_protection (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md) ストアド プロシージャを呼び出すことで、変数のセンシティビティ ビットを設定できます。  
  
 サーバー変数の値を使用するには、プロジェクトとサーバー環境間の参照を指定します。 次のストアド プロシージャを使用して、参照を作成したり削除したりすることができます。 環境をプロジェクトと同じフォルダーに配置できるか、または別のフォルダーに配置できるかを示すこともできます。  
  
-   [catalog.create_environment_reference &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
  
-   [catalog.delete_environment_reference &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
  
-   [catalog.set_environment_reference_type &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
  
 環境と変数の詳細については、次のビューに対してクエリを実行します。  
  
-   [catalog.environments &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
  
-   [catalog.environment_variables &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
  
-   [catalog.environment_references &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
  
##  <a name="a-nameexecutionsa-executions-and-validations"></a><a name="Executions"></a> 実行と検証  
 実行はパッケージ実行のインスタンスです。 実行を作成し、開始するには、[catalog.create_execution (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md) と [catalog.start_execution (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md) を呼び出します。 実行またはパッケージ/プロジェクト検証を停止するには、[catalog.stop_operation (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md) を呼び出します。  
  
 実行中のパッケージを一時停止してダンプ ファイルを作成するには、catalog.create_execution_dump ストアド プロシージャを呼び出します。 ダンプ ファイルは、実行に関する問題のトラブルシューティングに役立つ、パッケージの実行に関する情報を提供します。 ダンプ ファイルの生成および構成の詳細については、「 [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)」をご覧ください。  
  
 実行、検証、操作中にログに記録されたメッセージ、およびエラーに関するコンテキスト情報の詳細については、次のビューに対してクエリを実行します。  
  
-   [catalog.executions &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
  
-   [catalog.operations &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
  
-   [catalog.operation_messages &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
  
-   [catalog.extended_operation_info &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
  
-   [catalog.event_messages](../../integration-services/system-views/catalog-event-messages.md)  
  
-   [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
 [catalog.validate_project (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md) および [catalog.validate_package (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md) ストアド プロシージャを呼び出すことで、プロジェクトとパッケージを検証できます。 [catalog.validations (SSISDB データベース)](../../integration-services/system-views/catalog-validations-ssisdb-database.md) ビューには、検証で考慮されるサーバー環境参照、検証が依存関係の検証であるか完全検証であるか、32 ビット ランタイムと 64 ビット ランタイムのどちらをパッケージの実行に使用するかなどの、検証に関する詳細が表示されます。  
  
##  <a name="a-namealwaysona-alwayson-support"></a><a name="AlwaysOn"></a> AlwaysOn のサポート  
 AlwaysOn 可用性グループ機能は、データベース ミラーリングに代わる、高可用性と災害復旧のためのエンタープライズ レベルのソリューションです。 可用性グループは、可用性データベースとして知られる、ひとまとまりでフェールオーバーされる別々のユーザー データベース セットのためのフェールオーバー環境をサポートします。 詳細については、「 [AlwaysOn 可用性グループ (SQL Server)](https://msdn.microsoft.com/library/hh510230.aspx)」を参照してください。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、一元化された SSIS カタログ (つまり SSISDB ユーザー データベース) を簡単に配置できる新しい機能が SQL Server Integration Services (SSIS) に導入されています。 SSISDB データベースとそのコンテンツ (プロジェクト、パッケージ、実行ログなど) の高可用性を実現するには、(他のユーザー データベースと同様に) SSISDB データベースを AlwaysOn 可用性グループに追加できます。 フェールオーバーが発生すると、セカンダリ ノードのいずれかが自動的に新しいプライマリ ノードになります。  
  
 AlwaysOn 機能の詳細と SSISDB に対して有効にするための手順については、「[Always On for SSIS Catalog (SSISDB データベース)](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md)」を参照してください。  
  
##  <a name="a-namerelatedtasksa-related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [SSIS カタログの作成](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [SSIS カタログのバックアップ、復元、および移動](../../integration-services/service/backup-restore-and-move-the-ssis-catalog.md)  
  
##  <a name="a-namerelatedcontenta-related-content"></a><a name="RelatedContent"></a> 関連コンテンツ  
  
-   blogs.msdn.com のブログ「 [SQL Server 2012 での SSIS と PowerShell](http://go.microsoft.com/fwlink/?LinkId=242539)」  
  
-   blogs.msdn.com のブログ エントリ「 [SSIS カタログのアクセス制御のヒント](http://go.microsoft.com/fwlink/?LinkId=246669)」  
  
-   blogs.msdn.com のブログ エントリ「 [SSIS カタログ マネージ オブジェクト モデルの概要](http://go.microsoft.com/fwlink/?LinkId=254267)」  
  
  