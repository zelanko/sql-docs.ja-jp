---
title: FTP でのスナップショットの配信 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d1a8989492c9efb670b00bda00dbfa757c549fca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62960066"
---
# <a name="deliver-a-snapshot-through-ftp"></a>FTP でのスナップショットの配信
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、FTP でスナップショットを配信する方法について説明します。  
  
##  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\ftpserver\home\snapshots など) として指定する必要があります。 詳細については、「[スナップショットフォルダーをセキュリティで保護する](../security/secure-the-snapshot-folder.md)」を参照してください。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   ファイル転送プロトコル (FTP) を使用してスナップショット ファイルを転送するには、まず、FTP サーバーを構成する必要があります。 詳細については、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) のマニュアルを参照してください。  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティを強化するため、インターネット経由の FTP スナップショット配信を使用する際には仮想プライベート ネットワーク (VPN) を実装することをお勧めします。 詳細については、「[Publish Data over the Internet Using VPN](../publish-data-over-the-internet-using-vpn.md)」 (VPN を使用したインターネット経由のデータのパブリッシュ) を参照してください。  
  
 セキュリティの推奨方法としては、FTP サーバーに対する匿名ログインを許可しないことをお勧めします。 スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\ftpserver\home\snapshots など) として指定する必要があります。 詳細については、「[スナップショットフォルダーをセキュリティで保護する](../security/secure-the-snapshot-folder.md)」を参照してください。  
  
 可能であれば、実行時に資格情報の入力を求めるメッセージを表示します。 資格情報をスクリプト ファイルに保存する場合、ファイルをセキュリティ保護する必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 FTP サーバーの構成が完了したら、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、そのサーバーのディレクトリとセキュリティの情報を指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。  
  
#### <a name="to-specify-ftp-information"></a>FTP 情報を指定するには  
  
1.  
  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの次のいずれかのページで、**[ファイル転送プロトコル (FTP) を使用したスナップショット ファイルのダウンロードをサブスクライバーに許可する]** を選択します。   
    -   
  **[FTP スナップショット]** ページ。スナップショット パブリケーション、トランザクション パブリケーション、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のバージョンを実行しているパブリッシャーのマージ パブリケーションの場合。    
    -   
  **[FTP スナップショットとインターネット]** ページ。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降を実行しているパブリッシャーからのマージ パブリケーションの場合。    
2.  
      **[FTP サーバー名]**、 **[ポート番号]**、 **[FTP ルート フォルダーからのパス]**、 **[ログイン]**、および **[パスワード]** の値を指定します。    
 たとえば、FTP サーバーのルートが \\\ftpserver\home で、スナップショットを \\\ftpserver\home\snapshots に格納する場合は、**[FTP ルート フォルダーからのパス]** には「\snapshots\ftp」と指定します (レプリケーションでは、スナップショット ファイルが作成されるときにスナップショット フォルダーのパスに "ftp" が追加されます)。    
3.  スナップショット エージェントが、手順 2. で指定したディレクトリにスナップショット ファイルを書き込むように指定します。 たとえば、スナップショット エージェントがスナップショット ファイルを \\\ftpserver\home\snapshots\ftp に書き込むようにするには、次のいずれかの場所に \\\ftpserver\home\snapshots というパスを指定する必要があります。    
    -   このパブリケーションに関連付けられているディストリビューターの既定のスナップショットの場所。    
         既定のスナップショットの場所を指定する方法の詳細については、「[既定のスナップショットの場所の指定](../snapshot-options.md#snapshot-folder-locations)」を参照してください。    
    -   このパブリケーションの代替スナップショット フォルダーの場所。 スナップショットが圧縮されている場合、別の場所が必要です。    
         
  **[パブリケーションのプロパティ - **Publication>]** ダイアログ ボックスの [スナップショット] ページで、\<[ファイルを次のフォルダーに保存する]** ボックスにパスを入力します。   
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 FTP サーバーでスナップショット ファイルを使用するためのオプションを設定できます。この FTP 設定は、レプリケーション ストアド プロシージャを使用してプログラムから変更できます。 使用されるプロシージャは、パブリケーションの種類によって異なります。 FTP によるスナップショット配信は、プル サブスクリプションでのみ使用できます。  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションで FTP スナップショット配信を有効にするには  
  
1.  パブリッシャーのパブリケーション データベースに対して、 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。 を**@publication**指定し、 `true`に**@enabled_for_internet**値を、次のパラメーターに適切な値を指定します。    
    -   **@ftp_address**-スナップショットの配信に使用する FTP サーバーのアドレス。    
    -   Optional**@ftp_port** -FTP サーバーによって使用されるポート。    
    -   Optional**@ftp_subdirectory** -ftp ログインに割り当てられている既定の ftp ディレクトリのサブディレクトリ。 たとえば、FTP サーバールートが \ ftp_s \\ホームで、スナップショットを\\ **\snapshots\ftp**に保存する場合は、に対して**@ftp_subdirectory** [] を指定します (スナップショットファイルを作成するときに、レプリケーションによって "FTP" がスナップショットフォルダーパスに追加されます)。    
    -   Optional**@ftp_login** -FTP サーバーに接続するときに使用されるログインアカウント。    
    -   Optional**@ftp_password** -FTP ログインのパスワード。  
  
     これにより、FTP を使用するパブリケーションが作成されます。 詳しくは、「 [Create a Publication](create-a-publication.md)」をご覧ください。  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-merge-publication"></a>マージ パブリケーションで FTP スナップショット配信を有効にするには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。 を**@publication**指定し、 `true`に**@enabled_for_internet**値を指定して、次のパラメーターに適切な値を指定します。  
  
    -   **@ftp_address**-スナップショットの配信に使用する FTP サーバーのアドレス。    
    -   Optional**@ftp_port** -FTP サーバーによって使用されるポート。    
    -   Optional**@ftp_subdirectory** -ftp ログインに割り当てられている既定の ftp ディレクトリのサブディレクトリ。 たとえば、FTP サーバールートが \ ftp_s \\ホームで、スナップショットを\\ **\snapshots\ftp**に保存する場合は、に対して**@ftp_subdirectory** [] を指定します (スナップショットファイルを作成するときに、レプリケーションによって "FTP" がスナップショットフォルダーパスに追加されます)。    
    -   Optional**@ftp_login** -FTP サーバーに接続するときに使用されるログインアカウント。    
    -   Optional**@ftp_password** -FTP ログインのパスワード。  
  
     これにより、FTP を使用するパブリケーションが作成されます。 詳しくは、「 [Create a Publication](create-a-publication.md)」をご覧ください。  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication-that-uses-ftp-snapshot-delivery"></a>FTP スナップショット配信を使用するスナップショット パブリケーションまたはトランザクション パブリケーションへのプル サブスクリプションを作成するには  
  
1.  サブスクライバー側のサブスクリプション データベースに対して、 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)を実行します。 および**@publisher** **@publication**を指定します。  
  
    -   サブスクライバー側のサブスクリプション データベースに対して、 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)を実行します。 、 **@publisher** **@publisher_db**、 **@publication**を指定し[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 、サブスクライバーでディストリビューションエージェントが実行されるときに使用**@job_login**する**@job_password**Windows 資格情報をと`true`に**@use_ftp**指定し、の値をに指定します。  
  
2.  パブリッシャー側のパブリケーション データベースに対して [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を実行し、プル サブスクリプションを登録します。 詳細については、「 [プル サブスクリプションの作成](../create-a-pull-subscription.md)」をご覧ください。  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication-that-uses-ftp-snapshot-delivery"></a>FTP スナップショット配信を使用するマージ パブリケーションへのプル サブスクリプションを作成するには  
  
1.  サブスクライバー側のサブスクリプション データベースに対して、 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)を実行します。 および**@publisher** **@publication**を指定します。   
2.  サブスクライバー側のサブスクリプション データベースに対して、 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)を実行します。 、 **@publisher** **@publisher_db**、 **@publication**を指定し、サブスクライバーでディストリビューションエージェントが実行されるときに使用**@job_login**する**@job_password**Windows 資格情報をと`true`に**@use_ftp**指定し、の値をに指定します。    
3.  パブリッシャー側のパブリケーション データベースに対して [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) を実行し、プル サブスクリプションを登録します。 詳細については、「 [プル サブスクリプションの作成](../create-a-pull-subscription.md)」をご覧ください。  
  
#### <a name="to-change-one-or-more-ftp-snapshot-delivery-settings-for-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションの FTP スナップショット配信の設定を変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。 に**@property**次のいずれかの値を指定し、に**@value**この設定の新しい値を指定します。    
    -   `ftp_address`-スナップショットの配信に使用する FTP サーバーのアドレス。    
    -   
  `ftp_port` - FTP サーバーで使用されるポート。    
    -   
  `ftp_subdirectory` - FTP スナップショットに使用する既定の FTP ディレクトリのサブディレクトリ。    
    -   
  `ftp_login` - FTP サーバーへの接続に使用されるログイン。    
    -   
  `ftp_password` - FTP ログイン用のパスワード。  
  
2.  (省略可) 変更する各 FTP 設定について手順 1. を実行します。    
3.  (省略可) FTP スナップショット配信を無効にするには、パブリッシャー側のパブリケーション データベースに対して [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) を実行します。 `enabled_for_internet`に**@property**を指定し、 `false`に**@value**値を指定します。  
  
#### <a name="to-change-ftp-snapshot-delivery-settings-for-a-merge-publication"></a>マージ パブリケーションの FTP スナップショット配信の設定を変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。 に**@property**次のいずれかの値を指定し、に**@value**この設定の新しい値を指定します。  
  
    -   `ftp_address`-スナップショットの配信に使用する FTP サーバーのアドレス。    
    -   
  `ftp_port` - FTP サーバーで使用されるポート。    
    -   
  `ftp_subdirectory` - FTP スナップショットに使用する既定の FTP ディレクトリのサブディレクトリ。   
    -   
  `ftp_login` - FTP サーバーへの接続に使用されるログイン。    
    -   
  `ftp_password` - FTP ログイン用のパスワード。    
2.  (省略可) 変更する各 FTP 設定について手順 1. を実行します。    
3.  (省略可) FTP スナップショット配信を無効にするには、パブリッシャー側のパブリケーション データベースに対して [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) を実行します。 `enabled_for_internet`に**@property**を指定し、 `false`に**@value**値を指定します。  
  
###  <a name="TsqlExample"></a>例 (Transact-sql)  
 次の例では、サブスクライバーが FTP を使用してスナップショット データにアクセスできるマージ パブリケーションを作成します。 サブスクライバーは、FTP 共有にアクセスするときにセキュリティで保護された VPN 接続を使用する必要があります。 **sqlcmd**スクリプト変数は、ログインとパスワードの値を指定するために使用されます。 詳細については、「[Use sqlcmd with Scripting Variables](../../scripting/sqlcmd-use-with-scripting-variables.md)」(sqlcmd でのスクリプト変数の使用) をご覧ください。  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubftp.sql#sp_createmergepub_ftp)]  
  
 次の例では、マージ パブリケーションに対するサブスクリプションを作成します。ここでは、サブスクライバーが FTP を使用してスナップショットを取得します。 サブスクライバーは、FTP 共有にアクセスするときにセキュリティで保護された VPN 接続を使用する必要があります。 **sqlcmd**スクリプト変数は、ログインとパスワードの値を指定するために使用されます。 詳細については、「[Use sqlcmd with Scripting Variables](../../scripting/sqlcmd-use-with-scripting-variables.md)」(sqlcmd でのスクリプト変数の使用) をご覧ください。  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsub_ftp)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsubagent_ftp)]  
  
## <a name="see-also"></a>参照  
 [レプリケーションシステムストアドプロシージャの概念](../concepts/replication-system-stored-procedures-concepts.md)   
 [FTP 経由でスナップショットを転送する](../transfer-snapshots-through-ftp.md)   
 [パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../initialize-a-subscription-with-a-snapshot.md)  
  
  
