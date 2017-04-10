---
title: "FTP でのスナップショットの配信 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "snapshots [SQL Server replication], FTP snapshots"
  - "FTP snapshots [SQL Server replication]"
  - "スナップショット レプリケーション [SQL Server], FTP"
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# FTP でのスナップショットの配信
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、FTP でスナップショットを配信する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [前提条件](#Prerequisites)  
  
     [セキュリティ](#Security)  
  
-   **FTP でスナップショットを配信するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用している場合、必要があります、共有ディレクトリを指定汎用名前付け規則 (UNC) パスなど \\\ftpserver\home\snapshots します。 詳細については、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   ファイル転送プロトコル (FTP) を使用してスナップショット ファイルを転送するには、まず、FTP サーバーを構成する必要があります。 詳細については、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) のマニュアルを参照してください。  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティを強化するため、インターネット経由の FTP スナップショット配信を使用する際には仮想プライベート ネットワーク (VPN) を実装することをお勧めします。 詳細については、次を参照してください。 [インターネットを使用して VPN 経由でデータを発行](../../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md)します。  
  
 セキュリティの推奨方法としては、FTP サーバーに対する匿名ログインを許可しないことをお勧めします。 スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用している場合、必要があります、共有ディレクトリを指定汎用名前付け規則 (UNC) パスなど \\\ftpserver\home\snapshots します。 詳細については、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
 可能であれば、実行時に資格情報の入力を求めるメッセージを表示します。 資格情報をスクリプト ファイルに保存する場合、ファイルをセキュリティ保護する必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 FTP サーバーを構成した後でこのサーバーのディレクトリおよびセキュリティ情報を指定、 **パブリケーションのプロパティ \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
#### FTP 情報を指定するには  
  
1.   **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、 **FTP を使用してスナップショット ファイルのダウンロードをサブスクライバーに許可** から次のページのいずれか。  
  
    -    **FTP スナップショット** ] ページで、スナップショットおよびトランザクション パブリケーション、およびより前のバージョンを実行しているパブリッシャーのマージ パブリケーションの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]します。  
  
    -   **[FTP スナップショットとインターネット]** ページ。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降を実行しているパブリッシャーからのマージ パブリケーションの場合。  
  
2.  **[FTP サーバー名]**、 **[ポート番号]**、 **[FTP ルート フォルダーからのパス]**、 **[ログイン]**、および **[パスワード]**の値を指定します。  
  
     たとえば、FTP サーバーのルートが \\\ftpserver\home し、スナップショットに保存するため \\\ftpserver\home\snapshots、\snapshots\ftp プロパティの指定 **FTP ルート フォルダーからのパス** (レプリケーションは、"ftp"スナップショット フォルダーのパスにスナップショット ファイルの作成時に追加されます)。  
  
3.  スナップショット エージェントが、手順 2. で指定したディレクトリにスナップショット ファイルを書き込むように指定します。 たとえば、エージェント、スナップショットが存在する記述のスナップショット ファイルを \\\ftpserver\home\snapshots\ftp、パスを指定する必要があります \\\ftpserver\home\snapshots で 2 つの場所。  
  
    -   このパブリケーションに関連付けられているディストリビューターの既定のスナップショットの場所。  
  
         スナップショットの既定の場所を指定する方法の詳細については、次を参照してください。 [#40; (&)、スナップショットの既定の場所を指定します。SQL Server Management Studio と #41;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)します。  
  
    -   このパブリケーションの代替スナップショット フォルダーの場所。 スナップショットが圧縮されている場合、別の場所が必要です。  
  
         パスを入力、 **次のフォルダーにファイルを配置** ] テキスト ボックスの [スナップショット] ページで、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 代替スナップショット フォルダーの場所の詳細については、「 [Alternate Snapshot Folder Locations](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)」を参照してください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 FTP サーバーでスナップショット ファイルを使用するためのオプションを設定できます。この FTP 設定は、レプリケーション ストアド プロシージャを使用してプログラムから変更できます。 使用されるプロシージャは、パブリケーションの種類によって異なります。 FTP によるスナップショット配信は、プル サブスクリプションでのみ使用できます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションで FTP スナップショット配信を有効にするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)します。 指定 **@publication**, の値 **true** の **@enabled_for_internet**, と、次のパラメーターの値を適切な。  
  
    -   **@ftp_address** -スナップショットの配信に使用する FTP サーバーのアドレス。  
  
    -   (省略可能) **@ftp_port** -FTP サーバーによって使用されるポート。  
  
    -   (省略可能) **@ftp_subdirectory** -FTP ログインに割り当てられている既定の FTP ディレクトリのサブディレクトリです。 たとえば、FTP サーバーのルートが \\\ftpserver\home し、スナップショットに保存するため \\\ftpserver\home\snapshots、指定 **\snapshots\ftp** の **@ftp_subdirectory** (レプリケーションは、"ftp"スナップショット フォルダーのパスにスナップショット ファイルの作成時に追加されます)。  
  
    -   (省略可能) **@ftp_login** -ログイン アカウントが FTP サーバーに接続するときに使用します。  
  
    -   (省略可能) **@ftp_password** -FTP ログイン用のパスワード。  
  
     これにより、FTP を使用するパブリケーションが作成されます。 詳細については、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
#### マージ パブリケーションで FTP スナップショット配信を有効にするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 指定 **@publication**, の値 **true** の **@enabled_for_internet** と、次のパラメーターの値を適切な。  
  
    -   **@ftp_address** -スナップショットの配信に使用する FTP サーバーのアドレス。  
  
    -   (省略可能) **@ftp_port** -FTP サーバーによって使用されるポート。  
  
    -   (省略可能) **@ftp_subdirectory** -FTP ログインに割り当てられている既定の FTP ディレクトリのサブディレクトリです。 たとえば、FTP サーバーのルートが \\\ftpserver\home し、スナップショットに保存するため \\\ftpserver\home\snapshots、指定 **\snapshots\ftp** の **@ftp_subdirectory** (レプリケーションは、"ftp"スナップショット フォルダーのパスにスナップショット ファイルの作成時に追加されます)。  
  
    -   (省略可能) **@ftp_login** -ログイン アカウントが FTP サーバーに接続するときに使用します。  
  
    -   (省略可能) **@ftp_password** -FTP ログイン用のパスワード。  
  
     これにより、FTP を使用するパブリケーションが作成されます。 詳細については、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
#### FTP スナップショット配信を使用するスナップショット パブリケーションまたはトランザクション パブリケーションへのプル サブスクリプションを作成するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)します。 **@publisher** と **@publication**を指定します。  
  
    -   サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] のサブスクライバーでディストリビューション エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**, の値との **true** の **@use_ftp**します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) プル サブスクリプションを登録します。 詳細については、「 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
#### FTP スナップショット配信を使用するマージ パブリケーションへのプル サブスクリプションを作成するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)します。 **@publisher** と **@publication**を指定します。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、サブスクライバーでディストリビューション エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**, の値との **true** の **@use_ftp**します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) プル サブスクリプションを登録します。 詳細については、「 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションの FTP スナップショット配信の設定を変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)します。 **@property** に次のいずれかの値を指定し、この設定の新しい値を **@value**に指定します。  
  
    -   **ftp_address** -スナップショットの配信に使用する FTP サーバーのアドレス。  
  
    -   **ftp_port** -FTP サーバーによって使用されるポート。  
  
    -   **ftp_subdirectory** -FTP スナップショットに使用する既定の FTP ディレクトリのサブディレクトリです。  
  
    -   **ftp_login** -FTP サーバーへの接続に使用されるログイン。  
  
    -   **ftp_password** -FTP ログイン用のパスワード。  
  
2.  (省略可) 変更する各 FTP 設定について手順 1. を実行します。  
  
3.  (省略可能)FTP スナップショット配信を無効にするには実行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **enabled_for_internet** の **@property** の **false** の **@value**します。  
  
#### マージ パブリケーションの FTP スナップショット配信の設定を変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。 **@property** に次のいずれかの値を指定し、この設定の新しい値を **@value**に指定します。  
  
    -   **ftp_address** -スナップショットの配信に使用する FTP サーバーのアドレス。  
  
    -   **ftp_port** -FTP サーバーによって使用されるポート。  
  
    -   **ftp_subdirectory** -FTP スナップショットに使用する既定の FTP ディレクトリのサブディレクトリです。  
  
    -   **ftp_login** -FTP サーバーへの接続に使用されるログイン。  
  
    -   **ftp_password** -FTP ログイン用のパスワード。  
  
2.  (省略可) 変更する各 FTP 設定について手順 1. を実行します。  
  
3.  (省略可能)FTP スナップショット配信を無効にするには実行 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **enabled_for_internet** の **@property** の **false** の **@value**します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、サブスクライバーが FTP を使用してスナップショット データにアクセスできるマージ パブリケーションを作成します。 サブスクライバーは、FTP 共有にアクセスするときにセキュリティで保護された VPN 接続を使用する必要があります。 **sqlcmd** スクリプト変数を使用して、ログインとパスワードの値が入力されます。 詳細については、次を参照してください。 [でのスクリプト変数 sqlcmd を使用して](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)します。  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_1.sql)]  
  
 次の例では、マージ パブリケーションに対するサブスクリプションを作成します。ここでは、サブスクライバーが FTP を使用してスナップショットを取得します。 サブスクライバーは、FTP 共有にアクセスするときにセキュリティで保護された VPN 接続を使用する必要があります。 **sqlcmd** スクリプト変数を使用して、ログインとパスワードの値が入力されます。 詳細については、次を参照してください。 [でのスクリプト変数 sqlcmd を使用して](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)します。  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_2.sql)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_3.sql)]  
  
## 参照  
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [FTP によるスナップショットの転送](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  