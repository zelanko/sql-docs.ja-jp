---
title: SQL Server Backup to URL | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d3911ab34a01b2da971aa602df37c8c559ed6390
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53359294"
---
# <a name="sql-server-backup-to-url"></a>SQL Server Backup to URL
  このトピックでは、バックアップ先として Windows Azure BLOB ストレージ サービスを使用するために必要な概念、要件、およびコンポーネントについて説明します。 バックアップと復元の機能は、ディスクまたはテープを使用する場合とよく似ていますが、いくつか相違点もあります。 相違点、重要な例外、コード例についても、このトピックで説明しています。  
  
## <a name="requirements-components-and-concepts"></a>要件、コンポーネント、および概念  
 **このセクションの内容:**  
  
-   [セキュリティ](#security)  
  
-   [主なコンポーネントと概念の概要](#intorkeyconcepts)  
  
-   [Windows Azure Blob ストレージ サービス](#Blob)  
  
-   [SQL Server のコンポーネント](#sqlserver)  
  
-   [制限事項](#limitations)  
  
-   [BACKUP/RESTORE ステートメントのサポート](#Support)  
  
-   [SQL Server Management Studio でのバックアップ タスクの使用](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [メンテナンス プラン ウィザードを使用した SQL Server Backup to URL](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [SQL Server Management Studio を使用した Windows Azure ストレージからの復元](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a> セキュリティ  
 Windows Azure BLOB ストレージ サービスへのバックアップや Windows Azure BLOB ストレージ サービスからの復元を実行する場合のセキュリティに関する注意点と要件は次のとおりです。  
  
-   Windows Azure BLOB ストレージ サービスのコンテナーを作成する際は、アクセス権を **private**に設定することをお勧めします。 アクセス権を private に設定すると、Windows Azure アカウントの認証に必要な情報を指定できるユーザーまたはアカウントだけがアクセスできるようになります。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Windows Azure のアカウント名とアクセス キー認証を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報に格納する必要があります。 この情報は、バックアップ操作または復元操作の実行時に Windows Azure アカウントを認証するために使用されます。  
  
-   BACKUP コマンドまたは RESTORE コマンドの発行に使用するユーザー アカウントは、 **資格情報の変更** 権限を持つ **db_backup operator** データベース ロールに属している必要があります。  
  
###  <a name="intorkeyconcepts"></a> 主なコンポーネントと概念の概要  
 次の 2 つのセクションでは、Windows Azure BLOB ストレージ サービスと、Windows Azure BLOB ストレージ サービスへのバックアップ時や Windows Azure BLOB ストレージ サービスからの復元時に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントについて説明します。 Windows Azure BLOB ストレージ サービスへのバックアップや Windows Azure BLOB ストレージ サービスからの復元を実行するには、各コンポーネントと、コンポーネント間のやり取りを理解しておくことが重要です。  
  
 このプロセスは、Windows Azure アカウントを作成することから始まります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用して、 **Windows Azure ストレージ アカウント名**とその**アクセス キー**認証し、書き込みと blob ストレージ サービスへの読み取り値。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報はこの認証情報を格納するため、バックアップ操作または復元操作中に使用されます。 ストレージ アカウントを作成して単純な復元を実行する完全なチュートリアルについては、「 [チュートリアル: Windows Azure BLOB ストレージ サービスへの SQL Server のバックアップと復元の概要](https://go.microsoft.com/fwlink/?LinkId=271615)」を参照してください。  
  
 ![sql 資格情報をストレージ アカウントのマッピング](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "sql 資格情報をストレージ アカウントのマッピング")  
  
###  <a name="Blob"></a> Windows Azure Blob ストレージ サービス  
 **ストレージ アカウント:** ストレージ アカウントとは、すべての記憶域サービスの開始点です。 Windows Azure BLOB ストレージ サービスにアクセスするには、最初に Windows Azure ストレージ アカウントを作成してください。 Windows Azure BLOB ストレージ サービスとそのコンポーネントを認証するには、 **storage account name** プロパティとその **access key** プロパティが必要です。  
  
 **コンテナー:** コンテナーは、一連の Blob をグループ化を示し、無制限の数の Blob を格納することができます。 Windows Azure BLOB Service に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップを書き込むには、少なくともルート コンテナーを作成しておく必要があります。  
  
 **Blob:** 任意の種類とサイズのファイルです。 Windows Azure BLOB ストレージ サービスに格納できる BLOB には、ブロック BLOB とページ BLOB の 2 種類があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップでは、BLOB の種類としてページ BLOB を使用します。 Blob は、次の URL 形式を使用してアドレス指定できます: https://\<ストレージ アカウント >.blob.core.windows.net/\<コンテナー >/\<blob >  
  
 ![Azure BLOB ストレージ](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure BLOB ストレージ")  
  
 Windows Azure BLOB ストレージ サービスの詳細については、「 [.NET で Windows Azure BLOB ストレージ サービスを使用する方法](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)」を参照してください。  
  
 ページ BLOB の詳細については、「 [ブロック BLOB およびページ BLOB について](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)」を参照してください。  
  
###  <a name="sqlserver"></a> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント  
 **URL:** URL には、一意なバックアップ ファイルに統一リソース識別子 (URI) を指定します。 URL は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ ファイルの場所と名前を指定するために使用されます。 この実装で有効な URL は、Windows Azure ストレージ アカウントでページ BLOB を指す URL のみです。 URL は、コンテナーだけでなく、実際の BLOB を指している必要があります。 BLOB が存在しない場合は作成されます。 "WITH FORMAT"オプションを指定しない限り、既存の Blob が指定すると、バックアップの失敗の場合。  
  
> [!WARNING]  
>  バックアップ ファイルをコピーして Windows Azure BLOB ストレージ サービスにアップロードする場合は、ストレージ オプションとしてページ BLOB を使用してください。 ブロック BLOB からの復元はサポートされていません。 ブロック BLOB から RESTORE ステートメントを実行すると、エラーが発生して失敗します。  
  
 サンプル URL 値を次に示します: http[s]://ACCOUNTNAME.Blob.core.windows.net/\<コンテナー >/\<ファイル名.bak> です >。 HTTPS は必須ではありませんが、推奨されています。  
  
 **資格情報:** A[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資格情報が SQL Server の外部にあるリソースへの接続に必要な認証情報を格納するために使用するオブジェクト。  ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップおよび復元プロセスで資格情報を使用して、Windows Azure BLOB ストレージ サービスを認証します。 資格情報には、ストレージ アカウントの名前とその **アクセス キー** 値が格納されます。 作成した資格情報は、BACKUP/RESTORE ステートメントの実行時に WITH CREDENTIAL オプションで指定する必要があります。 詳細については、表示、コピー、またはストレージ アカウントを再生成する方法についての**アクセス キー**を参照してください[ストレージ アカウント アクセス キー](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)します。  
  
 作成する方法についてステップ バイ ステップの手順について、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資格情報を参照してください[資格情報を作成](#credential)このトピックで後述する例。  
  
 資格情報の全般的な情報については、「 [資格情報](../security/authentication-access/credentials-database-engine.md)」をご覧ください。  
  
 資格情報が使用されるその他の例については、「 [SQL Server エージェント プロキシの作成](../../ssms/agent/create-a-sql-server-agent-proxy.md)」参照してください。  
  
###  <a name="limitations"></a> 制限事項  
  
-   Premium Storage へのバックアップはサポートされていません。  
  
-   サポートされるバックアップの最大サイズは 1 TB です。  
  
-   TSQL、SMO、または PowerShell コマンドレットを使用してバックアップ ステートメントや復元ステートメントを実行できます。 現在、SQL Server Management Studio のバックアップと復元ウィザードを使用して、Windows Azure BLOB ストレージ サービスとの間でバックアップまたは復元を実行することはできません。  
  
-   論理デバイス名の作成はサポートされていません。 そのため、sp_dumpdevice または SQL Server Management Studio を使用してバックアップ デバイスとして URL を追加することはできません。  
  
-   既存のバックアップ BLOB への追加はサポートされていません。 既存の BLOB へのバックアップは WITH FORMAT オプションを使用した場合にのみ上書きできます。  
  
-   1 回のバックアップ操作で複数の BLOB にバックアップすることはサポートされていません。 たとえば、次のコードではエラーが返されます。  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'   
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,STATS = 5;  
    GO  
  
    ```  
  
-   `BACKUP` ステートメントでブロック サイズを指定することはサポートされていません。  
  
-   `MAXTRANSFERSIZE` を指定することはサポートされていません。  
  
-   バックアップセットのオプション (`RETAINDAYS` および `EXPIREDATE`) を指定することはサポートされていません。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、バックアップ デバイス名に最大 259 文字の制限があります。 BACKUP TO URL では、URL の指定に使用する必須要素に 'https://.blob.core.windows.net//.bak' の 36 文字が使用されるため、アカウント、コンテナー、および BLOB の名前は残りの 223 文字で構成します。  
  
###  <a name="Support"></a> BACKUP/RESTORE ステートメントのサポート  
  
|||||  
|-|-|-|-|  
|BACKUP/RESTORE ステートメント|サポートされている|例外|コメント|  
|BACKUP|???|BLOCKSIZE および MAXTRANSFERSIZE はサポートされていません。|WITH CREDENTIAL を指定する必要があります|  
|RESTORE|???||WITH CREDENTIAL を指定する必要があります|  
|RESTORE FILELISTONLY|???||WITH CREDENTIAL を指定する必要があります|  
|RESTORE HEADERONLY|???||WITH CREDENTIAL を指定する必要があります|  
|RESTORE LABELONLY|???||WITH CREDENTIAL を指定する必要があります|  
|RESTORE VERIFYONLY|???||WITH CREDENTIAL を指定する必要があります|  
|RESTORE REWINDONLY|???|||  
  
 BACKUP ステートメントの構文と一般的な情報については、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」をご覧ください。  
  
 RESTORE ステートメントの構文と一般的な情報については、「[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」をご覧ください。  
  
### <a name="support-for-backup-arguments"></a>BACKUP の引数のサポート  
  
|||||  
|-|-|-|-|  
|引数|Supported|例外|コメント|  
|DATABASE|???|||  
|LOG|???|||  
||  
|TO (URL)|???|ディスクまたはテープの場合とは異なり、URL では論理名の指定と作成はサポートされていません。|この引数は、バックアップ ファイルの URL パスの指定に使用されます。|  
|MIRROR TO|???|||  
|**WITH オプション:**||||  
|CREDENTIAL|???||WITH CREDENTIAL は、BACKUP TO URL オプションを使用して Windows Azure BLOB ストレージ サービスにバックアップする場合にのみ使用できます。|  
|DIFFERENTIAL|???|||  
|COPY_ONLY|???|||  
|COMPRESSION&#124;NO_COMPRESSION|???|||  
|DESCRIPTION|???|||  
|NAME|???|||  
|EXPIREDATE &#124; RETAINDAYS|???|||  
|NOINIT &#124; INIT|???||このオプションは使用しても無視されます。<br /><br /> BLOB に追加することはできません。 バックアップを上書きするには、FORMAT 引数を使用します。|  
|NOSKIP &#124; SKIP|???|||  
|NOFORMAT &#124; FORMAT|???||このオプションは使用しても無視されます。<br /><br /> WITH FORMAT を指定した場合を除き、既存の BLOB に対して実行されるバックアップは失敗します。 WITH FORMAT を指定すると、既存の BLOB が上書きされます。|  
|MEDIADESCRIPTION|???|||  
|MEDIANAME|???|||  
|BLOCKSIZE|???|||  
|BUFFERCOUNT|???|||  
|MAXTRANSFERSIZE|???|||  
|NO_CHECKSUM &#124; CHECKSUM|???|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|???|||  
|STATS|???|||  
|REWIND &#124; NOREWIND|???|||  
|UNLOAD &#124; NOUNLOAD|???|||  
|NORECOVERY &#124; STANDBY|???|||  
|NO_TRUNCATE|???|||  
  
 BACKUP の引数の詳細については、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」をご覧ください。  
  
### <a name="support-for-restore-arguments"></a>RESTORE の引数のサポート  
  
|||||  
|-|-|-|-|  
|引数|サポートされている|例外|コメント|  
|DATABASE|???|||  
|LOG|???|||  
|FROM (URL)|???||FROM URL 引数は、バックアップ ファイルの URL パスの指定に使用されます。|  
|**WITH Options:**||||  
|CREDENTIAL|???||WITH CREDENTIAL は、RESTORE FROM URL オプションを使用して Windows Azure BLOB ストレージ サービスから復元する場合にのみ使用できます。|  
|PARTIAL|???|||  
|RECOVERY &#124; NORECOVERY &#124; STANDBY|???|||  
|LOADHISTORY|???|||  
|MOVE|???|||  
|[REPLACE]|???|||  
|RESTART|???|||  
|RESTRICTED_USER|???|||  
|FILE|???|||  
|PASSWORD|???|||  
|MEDIANAME|???|||  
|MEDIAPASSWORD|???|||  
|BLOCKSIZE|???|||  
|BUFFERCOUNT|???|||  
|MAXTRANSFERSIZE|???|||  
|CHECKSUM &#124; NO_CHECKSUM|???|||  
|STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR|???|||  
|FILESTREAM|???|||  
|STATS|???|||  
|REWIND &#124; NOREWIND|???|||  
|UNLOAD &#124; NOUNLOAD|???|||  
|KEEP_REPLICATION|???|||  
|KEEP_CDC|???|||  
|ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER|???|||  
|STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK|???|||  
  
 RESTORE の引数の詳細については、「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」をご覧ください。  
  
##  <a name="BackupTaskSSMS"></a> SQL Server Management Studio でのバックアップ タスクの使用  
 SQL Server Management Studio でのバックアップ タスクが強化され、バックアップ先として URL も選択できるようになりました。また、[SQL 資格情報] など、Windows Azure ストレージへのバックアップに必要な他のサポート オブジェクトも追加されました。  
  
 次の手順では、Windows Azure ストレージへのバックアップを可能にするためにデータベースのバックアップ タスクに加えられた変更を示します。  
  
1.  SQL Server Management Studio を起動し、SQL Server インスタンスに接続します。  バックアップ、および右クリックしデータベースを選択**タスク**を選択し、**をバックアップする.**.[データベースのバックアップ] ダイアログ ボックスが開きます。  
  
2.  Windows Azure ストレージへのバックアップを作成するには、[全般] ページの **[URL]** オプションを使用します。 このオプションを選択すると、このページの他のオプションも有効になります。  
  
    1.  **ファイル名:** バックアップ ファイルの名前。  
  
    2.  **SQL 資格情報:** をクリックして、新しいものを作成できますか、既存の SQL Server 資格情報を指定するか、**作成**SQL 資格情報 の横にあります。  
  
        > [!IMPORTANT]  
        >  **[作成]** をクリックすると開くダイアログでは、サブスクリプションの管理証明書または公開プロファイルが求められます。 SQL Server では現在、公開プロファイルのバージョン 2.0 がサポートされています。 公開プロファイルのサポート対象バージョンをダウンロードするには、「 [公開プロファイルのバージョン 2.0 のダウンロード](https://go.microsoft.com/fwlink/?LinkId=396421)」をご覧ください。  
        >   
        >  管理証明書または公開プロファイルにアクセスできない場合は、Transact-SQL または SQL Server Management Studio を使用してストレージ アカウント名とアクセス キーの情報を指定し、SQL 資格情報を作成することができます。 サンプル コードを参照してください、[資格情報を作成](#credential)Transact SQL を使用して資格情報を作成します。 または SQL Server Management Studio を使用して、データベース エンジン インスタンスから、 **[セキュリティ]** を右クリックし、 **[新規作成]**、 **[資格情報]** の順にクリックします。 **[ID]** にストレージ アカウント名、 **[パスワード]** にアクセス キーを指定します。  
  
    3.  **Azure ストレージ コンテナー:** バックアップ ファイルを格納する Windows Azure ストレージ コンテナーの名前。  
  
    4.  **[URL プレフィックス]** これは、前の手順で説明したフィールドで指定された情報を使用して自動的に組み込まれています。 この値を手動で編集する場合は、前に入力した他の情報と一致することを確認してください。 たとえばストレージの URL を変更する場合は、[SQL 資格情報] も、同じストレージ アカウントに対する認証を行うように設定されていることを確認します。  
  
 バックアップ先として URL を選択すると、 **[メディア オプション]** ページの一部のオプションが無効になります。  [データベースのバックアップ] ダイアログの詳細については、次のトピックを参照してください。  
  
 [データベースのバックアップ &#40;全般ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [データベースのバックアップ &#40;メディア オプション ページ&#41;](back-up-database-media-options-page.md)  
  
 [データベースのバックアップ &#40;バックアップ オプション ページ&#41;](back-up-database-backup-options-page.md)  
  
 [資格情報の作成- Azure ストレージに対する認証](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="MaintenanceWiz"></a> メンテナンス プラン ウィザードを使用した SQL Server Backup to URL  
 前に説明したバックアップ タスクと同様、SQL Server Management Studio のメンテナンス プラン ウィザードも強化され、バックアップ先として **[URL]** も選択できるようになりました。また、[SQL 資格情報] など、Windows Azure ストレージへのバックアップに必要な他のサポート オブジェクトも追加されました。 詳細については、「 **Using Maintenance Plan Wizard** 」の「 [バックアップ タスクを定義する](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)」を参照してください。  
  
##  <a name="RestoreSSMS"></a> Windows Azure storage を使用して SQL Server Management Studio からの復元  
 データベースを復元する場合、復元元のデバイスとして **[URL]** が用意されています。 次の手順では、Windows Azure ストレージからの復元を可能にするために復元タスクに加えられた変更を示します。  
  
1.  SQL Server Management Studio の復元タスクの **[全般]** ページで **[デバイス]** を選択すると、 **[バックアップ デバイスの選択]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは、バックアップ メディアの種類として **[URL]** を選択できます。  
  
2.  **[URL]** を選択し、 **[追加]** をクリックすると、 **[Azure ストレージへの接続]** ダイアログが開きます。 Windows Azure ストレージに対する認証に使用する SQL 資格情報を指定します。  
  
3.  指定した SQL 資格情報を使用して SQL Server が Windows Azure ストレージに接続され、 **[Windows Azure でのバックアップ ファイルの検索]** ダイアログ ボックスが開きます。 このページには、ストレージに存在するバックアップ ファイルが表示されます。 復元に使用するファイルを選択して **[OK]** をクリックします。 これにより、 **[バックアップ デバイスの選択]** ダイアログ ボックスが再度表示されます。このダイアログ ボックスで **[OK]** をクリックすると、メインの **[復元]** ダイアログ ボックスに戻って復元を完了できます。  詳細については、次のトピックを参照してください。  
  
     [[データベースの復元] &#40;[全般] ページ&#41;](restore-database-general-page.md)  
  
     [[データベースの復元] &#40;[ファイル] ページ&#41;](restore-database-files-page.md)  
  
     [[データベースの復元] &#40;[オプション] ページ&#41;](restore-database-options-page.md)  
  
##  <a name="Examples"></a> コード例  
 ここでは、次の例について説明します。  
  
-   [Shared Access Signature の作成](#credential)  
  
-   [データベース全体をバックアップする](#complete)  
  
-   [データベースおよびログをバックアップする](#databaselog)  
  
-   [プライマリ ファイル グループのファイルの完全バックアップを作成します。](#filebackup)  
  
-   [プライマリ ファイル グループのファイルの差分バックアップを作成します。](#differential)  
  
-   [データベースを復元しファイルを移動する](#restoredbwithmove)  
  
-   [STOPAT を使って特定の時点の状態に復元する](#PITR)  
  
###  <a name="credential"></a> Shared Access Signature の作成  
 次の例では、Windows Azure ストレージの認証情報を格納する資格情報を作成します。  
  
1.  **tsql**  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key>' ;  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
    string secret = "<storage access key>";  
  
    // Create a Credential  
    string credentialName = "mycredential";  
    Credential credential = new Credential(server, credentialName);  
    credential.Create(identity, secret);  
    ```  
  
3.  **PowerShell**  
  
    ```  
    # create variables  
    $storageAccount = "mystorageaccount"  
    $storageKey = "<storage access key>"  
    $secureString = convertto-securestring $storageKey  -asplaintext -force  
    $credentialName = "mycredential"  
  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Create a credential  
     New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString  
  
    ```  
  
###  <a name="complete"></a> 完全なデータベースをバックアップします。  
 次の例では、AdventureWorks2012 データベースを Windows Azure BLOB ストレージ サービスにバックアップします。  
  
1.  **tsql**  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
    GO  
  
    ```  
  
1.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
    ```  
  
2.  **PowerShell**  
  
    ```  
    # create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
    # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
    CD $srvPath   
    $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On  
  
    ```  
  
###  <a name="databaselog"></a> データベースおよびログをバックアップします。  
 次の例では、AdventureWorks2012 サンプル データベースをバックアップします。このデータベースでは、既定で単純復旧モデルが使用されています。 ここではまず、ログをバックアップするため、完全復旧モデルを使用するよう AdventureWorks2012 データベースを変更します。 その後、Windows Azure BLOB にデータベースの完全バックアップを作成し、更新操作の期間後、ログをバックアップします。 この例では、日付と時刻のタイム スタンプを含むバックアップ ファイル名を作成します。  
  
1.  **tsql**  
  
    ```  
    -- To permit log backups, before the full database backup, modify the database   
    -- to use the full recovery model.  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012  
       SET RECOVERY FULL;  
    GO  
  
    -- Back up the full AdventureWorks2012 database.  
           -- First create a file name for the backup file with DateTime stamp  
  
    DECLARE @Full_Filename AS VARCHAR (300);  
    SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
    --Back up Adventureworks2012 database  
  
    BACKUP DATABASE AdventureWorks2012  
    TO URL =  @Full_Filename  
    WITH CREDENTIAL = 'mycredential';  
    ,COMPRESSION  
    GO  
    -- Back up the AdventureWorks2012 log.  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url for data backup  
    string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database to Url  
    Backup backupData = new Backup();  
    backupData.CredentialName = credentialName;  
    backupData.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
    backupData.SqlBackup(server);  
  
    // Generate Unique Url for data backup  
    string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database Log to Url  
    Backup backupLog = new Backup();  
    backupLog.CredentialName = credentialName;  
    backupLog.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
    backupLog.Action = BackupActionType.Log;  
    backupLog.SqlBackup(server);  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to theSQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the full database backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Backup Database to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
    #Create a unique file name for log backup  
  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup Log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log  
  
    ```  
  
###  <a name="filebackup"></a> プライマリ ファイル グループのファイルの完全バックアップを作成します。  
 次の例では、プライマリ ファイル グループのファイル全体のバックアップを作成します。  
  
1.  **tsql**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to the SQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the file backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
    #Backup Primary File Group to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary  
  
    ```  
  
###  <a name="differential"></a> プライマリ ファイル グループのファイルの差分バックアップを作成します。  
 次の例では、プライマリ ファイル グループのファイルの差分バックアップを作成します。  
  
1.  **tsql**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
    GO  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.Incremental = true;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Create a differential backup of the primary filegroup  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental  
  
    ```  
  
###  <a name="restoredbwithmove"></a> データベースを復元し、ファイルを移動します。  
 データベースの完全バックアップを復元し、復元したデータベースを C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data ディレクトリに移動するには、次の手順を実行します。  
  
1.  **tsql**  
  
    ```  
    -- Backup the tail of the log first  
  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
    GO  
  
    RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
    WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for tail log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance   
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)  
  
    ```  
  
###  <a name="PITR"></a> STOPAT を使って特定の時点の状態に復元する  
 次の例では、データベースを特定の時点の状態に復元し、復元操作を示します。  
  
1.  **tsql**  
  
    ```  
    RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
    WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
    GO   
  
    RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
    WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for Tail Log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.NoRecovery = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    // Restore transaction Log with stop at   
    Restore restoreLog = new Restore();  
    restoreLog.CredentialName = credentialName;  
    restoreLog.Database = dbName;  
    restoreLog.Action = RestoreActionType.Log;  
    restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restoreLog.ToPointInTime = DateTime.Now.ToString();   
    restoreLog.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Navigate to SQL Server Instance Directory  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
    # Restore Transaction log with Stop At:  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()  
  
    ```  
  
## <a name="see-also"></a>参照  
 [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [システム データベースのバックアップと復元 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [チュートリアル:SQL Server のバックアップと Windows Azure Blob ストレージ サービスへの復元](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
  
