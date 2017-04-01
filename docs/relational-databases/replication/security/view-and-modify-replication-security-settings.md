---
title: "レプリケーションのセキュリティ設定の表示および変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying replication security settings"
  - "replication [SQL Server], security"
  - "security [SQL Server replication], viewing settings"
  - "viewing replication security settings"
  - "セキュリティ [SQL Server レプリケーション], 設定の変更"
ms.assetid: 67d79532-1482-4de1-ac9f-4a23d162c85e
caps.latest.revision: 47
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 47
---
# レプリケーションのセキュリティ設定の表示および変更
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、レプリケーションのセキュリティ設定を表示および変更する方法について説明します。 たとえば、ログ リーダー エージェントからパブリッシャーへの接続を SQL Server 認証から Windows 統合認証に変更したい場合や、Windows アカウントのパスワードを変更したときにエージェント ジョブの実行に使用する資格情報を変更したい場合があります。 各エージェントで必要な権限については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **レプリケーションのセキュリティ設定を表示および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
-   **補足情報:**  [レプリケーションのセキュリティ設定を変更した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   使用するストアド プロシージャは、エージェントの種類およびサーバー接続の種類によって異なります。  
  
-   使用する RMO のクラスとプロパティは、エージェントの種類およびサーバー接続の種類によって異なります。  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティ上の理由から、レプリケーション ストアド プロシージャによって返される結果セットでは、パスワードの実際の値はマスクされます。  
  
####  <a name="Permissions"></a> アクセス許可  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 次のダイアログ ボックスでセキュリティ設定を表示および変更します。  
  
1.  **[レプリケーション パスワードの更新]** ダイアログ ボックス。このダイアログ ボックスは、 **の** [レプリケーション] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]フォルダーから利用できます。 レプリケーション トポロジのサーバーで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントまたは Windows アカウントのパスワードを変更する場合は、そのアカウントを使用する各エージェントのパスワードを更新するよりも、このダイアログ ボックスを使用してください。 複数のサーバー上のエージェントが同じアカウントを使用している場合は、それぞれのサーバーに接続してパスワードを変更する必要があります。 パスワードは、レプリケーションで使用されるすべての場所で更新されます。 パスワードは、リンク サーバーなど、その他の場所では更新されません。  
  
2.   **エージェントのセキュリティ** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
3.   **サブスクリプションのプロパティ - \< サブスクリプション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
4.   **ディストリビューターのプロパティ - \< ディストリビューター>** と **ディストリビューション データベースのプロパティ - \< Database>** ダイアログ ボックス。 これらのダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Distributor and Publisher Properties](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
5.   **パブリッシャーのプロパティ - \< Publisher>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Distributor and Publisher Properties](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
#### 1 つ以上のエージェントによって使用されるアカウントのパスワードを変更するには  
  
1.  アカウントが SQL Server アカウントの場合、このダイアログ ボックスによって SQL Server アカウントのパスワードも変更されます。 アカウントが Windows アカウントの場合は、最初に Windows でパスワードを変更します。 詳細については、Windows のマニュアルを参照してください。  
  
    > [!NOTE]  
    >  レプリケーション パスワードを変更したら、そのパスワードを使用する各エージェントを停止して再起動し、エージェントに対して変更を反映させる必要があります。  
  
2.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]でサーバーに接続して、サーバー ノードを展開します。  
  
3.  右クリックし、 **レプリケーション** フォルダー、およびクリック **レプリケーション パスワードの更新**します。  
  
4.  **[レプリケーション パスワードの更新]** ダイアログ ボックスで、アカウントと新しいパスワードを指定します。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### スナップショット エージェントのセキュリティ設定を変更するには  
  
1.   **エージェントのセキュリティ** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、をクリックして、 **セキュリティ設定** ボックスの横に、 **スナップショット エージェント** テキスト ボックスです。  
  
2.  **[スナップショット エージェントのセキュリティ]** ダイアログ ボックスで、エージェントを実行するアカウントを指定します。  
  
    -   **[プロセス アカウント]** テキスト ボックスに新しい Windows アカウントを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
3.  エージェントがディストリビューターからパブリッシャーに接続するときのコンテキストを指定します。 **[次の SQL Server ログインを使用する]**を選択する場合は、ログインも指定する必要があります。  
  
    -   **[ログイン]** テキスト ボックスにログインを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
    > [!NOTE]  
    >  接続コンテキストがで指定されたパブリッシャーが Oracle パブリッシャーの場合、 **ディストリビューターのプロパティ - \< ディストリビューター>**] ダイアログ ボックス。 コンテキストを変更する手順については、以下を参照してください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### ログ リーダー エージェントのセキュリティ設定を変更するには  
  
1.   **エージェントのセキュリティ** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、をクリックして、 **セキュリティ設定** ボックスの横に、 **ログ リーダー エージェント** テキスト ボックスです。  
  
2.  **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスで、エージェントを実行するアカウントを指定します。  
  
    -   **[プロセス アカウント]** テキスト ボックスに新しい Windows アカウントを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
3.  エージェントがディストリビューターからパブリッシャーに接続するときのコンテキストを指定します。 **[次の SQL Server ログインを使用する]**を選択する場合は、ログインも指定する必要があります。  
  
    -   **[ログイン]** テキスト ボックスにログインを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
    > [!NOTE]  
    >  接続コンテキストがで指定されたパブリッシャーが Oracle パブリッシャーの場合、 **ディストリビューターのプロパティ - \< ディストリビューター>**] ダイアログ ボックス。 次の手順を使用して、コンテキストを変更します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  ログ リーダー エージェントは、パブリッシュされているデータベースごとに 1 つ存在します。 1 つのパブリケーションでエージェントのセキュリティ設定を変更すると、パブリケーション データベースのすべてのパブリケーションの設定に影響が及びます。  
  
#### Oracle パブリケーションのスナップショット エージェントおよびログ リーダー エージェントがパブリッシャーに接続するときのコンテキストを変更するには  
  
1.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックスで、[プロパティ] ボタンをクリックして (**...**) パブリッシャーの横にあります。  
  
2.  **[パブリッシャーへのエージェント接続]** セクションで、構成したレプリケーション管理ユーザー スキーマによって使用されるログインとパスワードを指定します。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### プッシュ サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.   **サブスクリプションのプロパティ - \< サブスクリプション>** ダイアログ ボックスで、パブリッシャーでは、次の変更を加えることができます。  
  
    -   ディストリビューション エージェントが実行されがディストリビューターに接続するアカウントを変更する] をクリックして、 **エージェント プロセス アカウント** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
    -   ディストリビューション エージェントがサブスクライバーに接続するためのコンテキストを変更するにはクリックして、 **サブスクライバー接続** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
         キュー更新サブスクリプションを使用する場合、ここで指定したコンテキストは、サブスクライバーに接続するためにキュー リーダー エージェントでも使用されます。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### プル サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.   **サブスクリプションのプロパティ - \< サブスクリプション>** ダイアログ ボックスで、サブスクライバーでは、次の変更を加えることができます。  
  
    -   ディストリビューション エージェントが実行されがサブスクライバーに接続するアカウントを変更する] をクリックして、 **エージェント プロセス アカウント** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
         キュー更新サブスクリプションを使用する場合、ここで指定したコンテキストは、サブスクライバーに接続するためにキュー リーダー エージェントでも使用されます。  
  
    -   ディストリビューション エージェントがディストリビューターに接続するためのコンテキストを変更するにはクリックして、 **ディストリビューター接続** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### プッシュ サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.   **サブスクリプションのプロパティ - \< サブスクリプション>** ダイアログ ボックスで、パブリッシャーでは、次の変更を加えることができます。  
  
    -   されるマージ エージェントが実行されがパブリッシャーとディストリビューターに接続するアカウントを変更する] をクリックして、 **エージェント プロセス アカウント** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[マージ エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
    -   マージ エージェントがサブスクライバーに接続するためのコンテキストを変更するにはクリックして、 **サブスクライバー接続** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### プル サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.   **サブスクリプションのプロパティ - \< サブスクリプション>** ダイアログ ボックスで、サブスクライバーでは、次の変更を加えることができます。  
  
    -   されるマージ エージェントが実行されがサブスクライバーに接続するアカウントを変更する] をクリックして、 **エージェント プロセス アカウント** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[マージ エージェント セキュリティ]** ダイアログ ボックスで、アカウントとパスワードを指定します。  
  
    -   マージ エージェントがパブリッシャーとディストリビューターに接続するためのコンテキストを変更するにはクリックして、 **パブリッシャー接続** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。 **[接続情報の入力]** ダイアログ ボックスでコンテキストを指定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### キュー リーダー エージェントを実行するアカウントを変更するには  
  
1.   **全般** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックスで、[プロパティ] をクリックして (**...**) ディストリビューション データベースの横にあるボタンをクリックします。  
  
2.   **ディストリビューション データベースのプロパティ - \< データベース>** ダイアログ ボックスで、をクリックして、 **セキュリティ設定** ボックスの横に、 **エージェント プロセス アカウント** テキスト ボックスです。  
  
3.  **[キュー リーダー エージェントのセキュリティ]** ダイアログ ボックスで、エージェントを実行してディストリビューターへ接続するアカウントを指定します。  
  
    -   **[プロセス アカウント]** テキスト ボックスに新しい Windows アカウントを入力します。  
  
    -   **[パスワード]** テキスト ボックスと **[パスワードの確認入力]** テキスト ボックスに、新しい複雑なパスワードを入力します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 エージェントのセキュリティ設定を変更すると、このディストリビューション データベースを使用するすべてのパブリッシャーのすべてのパブリケーションの設定に影響が及びます。  
  
#### キュー リーダー エージェントがパブリッシャーに接続するときのコンテキストを変更するには  
  
1.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックスで、[プロパティ] ボタンをクリックして (**...**) パブリッシャーの横にあります。  
  
2.  **[パブリッシャーへのエージェント接続]** セクションで、 **[エージェント接続モード]** オプションの **[エージェント プロセス アカウントを借用する]** または **[SQL Server 認証]** の値を指定します。 **[SQL Server 認証]**を指定する場合は、 **[ログイン]** および **[パスワード]**の値も入力します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 エージェントのセキュリティ設定を変更すると、このディストリビューション データベースを使用するすべてのパブリッシャーのすべてのパブリケーションの設定に影響が及びます。  
  
#### キュー リーダー エージェントがサブスクライバーに接続するときのコンテキストを変更するには  
  
-   キュー リーダー エージェントは、ディストリビューション エージェントと同じ接続コンテキストをサブスクリプションに使用します。 詳細については、ディストリビューション エージェントに関する上記の手順を参照してください。  
  
#### 即時更新プル サブスクリプションのセキュリティ設定を変更するには  
  
1.   **サブスクリプションのプロパティ - \< サブスクリプション>** ] ダイアログ ボックス サブスクライバーで、をクリックして、 **パブリッシャー接続** 行を [プロパティ] をクリックして (**...**) 行にボタンをクリックします。  
  
2.  **[接続情報の入力]** ダイアログ ボックスで、次のオプションのいずれかを選択します。  
  
    -   **[リンク サーバーまたはリモート サーバーからのログインを使用します]**。 リモート サーバーまたは、サブスクライバーとパブリッシャーを使用して、間にリンク サーバー定義している場合は、このオプションを選択 [sp_addserver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), 、[sp_addlinkedserver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), 、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], 、または別の方法です。  
  
    -   **[次のログインとパスワードによる SQL Server 認証を使用する]**。 サブスクライバーとパブリッシャーの間でリモート サーバーまたはリンク サーバーを定義していない場合は、このオプションを選択します。 レプリケーションによってリンク サーバーが作成されます。 指定するアカウントは、パブリッシャーに既に存在している必要があります。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  この手順により、サブスクライバーで変更が行われたときに、レプリケーション トリガーがサブスクライバーからパブリッシャーに接続するために使用する方法が変更されます。 ディストリビューション エージェントに関連付けられている設定を即時更新サブスクリプション用に変更することもできます。 詳細については、このトピックで既に説明した手順を参照してください。  
>   
>  この手順は、プル サブスクリプションにのみ当てはまります。 プッシュ サブスクリプションの場合、ストアド プロシージャを使用して [sp_link_publication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)します。  
  
#### パブリッシャーからディストリビューターへの管理接続に使用されているパスワードを変更するには  
  
1.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックスで強力なパスワードを入力、 **パスワード** と **パスワードの確認** テキスト ボックスです。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.   **全般的な** のページ、 **パブリッシャーのプロパティ - \< Publisher>** ] ダイアログ ボックスに強力なパスワードを入力、 **パスワード** と **パスワードの確認** テキスト ボックスです。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
> [!IMPORTANT]  
>  可能な限り、次のすべての手順で、実行時にセキュリティ資格情報を入力するように求めるメッセージをユーザーに表示します。 スクリプト ファイルに資格情報を格納する場合は、不正アクセスを防ぐために、そのファイルをセキュリティで保護する必要があります。  
  
#### レプリケーション サーバーに格納されたパスワードのインスタンスをすべて変更するには  
  
1.  Master データベースのレプリケーション トポロジ内のサーバーで実行 [sp_changereplicationserverpasswords](../../../relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql.md)します。 指定の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows アカウントまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインのパスワードを変更する **@login** し、アカウントまたはログインのための新しいパスワード **@password**します。 これにより、トポロジ内の他のサーバーに接続すると、サーバーのすべてのエージェントで使用されるパスワードの各インスタンスが変更されます。  
  
    > [!NOTE]  
    >  変更だけ、ログインおよびディストリビューターまたはサブスクライバー) など、トポロジ内の特定のサーバーに接続するためのパスワードを指定してこのサーバーの名前を **@server**します。  
  
2.  パスワードの更新が必要なレプリケーション トポロジ内の各サーバーで手順 1. を繰り返します。  
  
    > [!NOTE]  
    >  レプリケーション パスワードを変更したら、そのパスワードを使用する各エージェントを停止して再起動し、エージェントに対して変更を反映させる必要があります。  
  
#### スナップショット エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーで実行 [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), を指定して **@publication**します。 これにより、スナップショット エージェントの現在のセキュリティ設定が返されます。  
  
2.  パブリッシャーで実行 [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), を指定して **@publication** と 1 つ以上の次のセキュリティ設定を変更します。  
  
    -   Windows アカウントを変更する、エージェントを実行するか、このアカウントのパスワードだけ指定 **@job_login** と **@job_password**します。  
  
    -   パブリッシャーに接続するときに使用するセキュリティ モードを変更するには、値を指定 **1** または **0** の **@publisher_security_mode**します。  
  
    -   パブリッシャーに接続するときに使用するセキュリティ モードを変更するときに **1** に **0** または変更する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは、この接続に使用される、指定 **@publisher_login** と **@publisher_password**します。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
#### ログ リーダー エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーで実行 [sp_helplogreader_agent](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md), を指定して **@publisher**します。 これにより、ログ リーダー エージェントの現在のセキュリティ設定が返されます。  
  
2.  パブリッシャーで実行 [sp_changelogreader_agent](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md), を指定して **@publication** と 1 つ以上の次のセキュリティ設定を変更します。  
  
    -   Windows アカウントを変更する、エージェントを実行するか、このアカウントのパスワードだけ指定 **@job_login** と **@job_password**します。  
  
    -   パブリッシャーに接続するときに使用するセキュリティ モードを変更するには、値を指定 **1** または **0** の **@publisher_security_mode**します。  
  
    -   パブリッシャーに接続するときに使用するセキュリティ モードを変更するときに **1** に **0** または変更する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは、この接続に使用される、指定 **@publisher_login** と **@publisher_password**します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
#### プッシュ サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpsubscription](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md), を指定して **@publication** と **@subscriber**します。 これにより、ディストリビューターで実行されるディストリビューション エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changesubscription](../../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md), を指定して、 **@publication**, 、**@subscriber**, 、**@subscriber_db**, 、の値 **すべて** の **@article**, 、セキュリティ プロパティの名前 **@property**, 、およびプロパティの新しい値 **@value**します。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   このアカウントのパスワードを Windows アカウントは、エージェントを実行するまたはだけを変更するには、指定の値の **distrib_job_password** の **@property** と新しいパスワードを **@value**します。 アカウント自体を変更する場合は、手順の値を指定する 2 を繰り返して **distrib_job_login** の **@property** と新しい Windows アカウントを **@value**します。  
  
    -   サブスクライバーに接続するときに使用するセキュリティ モードを変更するには、値を指定 **subscriber_security_mode** の **@property** の **1** (Windows 統合認証) または **0** (SQL Server 認証) の **@value**します。  
  
    -   SQL Server 認証にサブスクライバーのセキュリティ モードを変更するとき、または SQL Server 認証のログイン情報を変更する場合は、値を指定して **subscriber_password** の **@property** と新しいパスワードを **@value**します。 手順 2 の値を指定する **subscriber_login** の **@property** し、新しいログインを **@value**します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのプロパティの指定された値でパブリッシャーを構成する場合を含む **distrib_job_login** と **distrib_job_password**, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
#### プル サブスクリプションに対するディストリビューション エージェントのセキュリティ設定を変更するには  
  
1.  サブスクライバーで、次のように実行します。 [sp_helppullsubscription](../../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md), を指定して **@publication**します。 これにより、サブスクライバーで実行されるディストリビューション エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_change_subscription_properties](../../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), を指定して **@publisher**, 、**@publisher_db**, 、**@publication**, 、のセキュリティ プロパティの名前 **@property**, 、およびプロパティの新しい値 **@value**します。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   このアカウントのパスワードを Windows アカウントは、エージェントを実行するまたはだけを変更するには、指定の値の **distrib_job_password** の **@property** と新しいパスワードを **@value**します。 アカウント自体を変更する場合は、手順の値を指定する 2 を繰り返して **distrib_job_login** の **@property** と新しい Windows アカウントを **@value**します。  
  
    -   ディストリビューターに接続するときに使用するセキュリティ モードを変更するには、値を指定 **distributor_security_mode** の **@property** の **1** (Windows 統合認証) または **0** (SQL Server 認証) の **@value**します。  
  
    -   SQL Server 認証にディストリビューターのセキュリティ モードを変更するとき、または SQL Server 認証のログイン情報を変更する場合は、値を指定して **distributor_password 用途** の **@property** と新しいパスワードを **@value**します。 手順 2 の値を指定する **distributor_login** の **@property** し、新しいログインを **@value**します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
#### プッシュ サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergesubscription](../../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md), を指定して **@publication**, 、**@subscriber**, 、および **@subscriber_db**します。 これにより、ディストリビューターで実行されるマージ エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergesubscription](../../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md), を指定して **@publication**, 、**@subscriber**, 、**@subscriber_db**, 、セキュリティ プロパティの名前 **@property**, 、およびプロパティの新しい値 **@value**します。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   このアカウントのパスワードをエージェントが実行するか、Windows アカウントを変更するには、指定の値の **merge_job_password** の **@property** と新しいパスワードを **@value**します。 アカウント自体を変更する場合は、手順の値を指定する 2 を繰り返して **merge_job_login** の **@property** と新しい Windows アカウントを **@value**します。  
  
    -   サブスクライバーに接続するときに使用するセキュリティ モードを変更するには、値を指定 **subscriber_security_mode** の **@property** の **1** (Windows 統合認証) または **0** (SQL Server 認証) の **@value**します。  
  
    -   SQL Server 認証にサブスクライバーのセキュリティ モードを変更するとき、または SQL Server 認証のログイン情報を変更する場合は、値を指定して **subscriber_password** の **@property** と新しいパスワードを **@value**します。 手順 2 の値を指定する **subscriber_login** の **@property** し、新しいログインを **@value**します。  
  
    -   パブリッシャーに接続するときに使用するセキュリティ モードを変更するには、値を指定 **publisher_security_mode** の **@property** の **1** (Windows 統合認証) または **0** (SQL Server 認証) の **@value**します。  
  
    -   SQL Server 認証にパブリッシャーのセキュリティ モードを変更するとき、または SQL Server 認証のログイン情報を変更する場合は、値を指定して **publisher_password** の **@property** と新しいパスワードを **@value**します。 手順 2 の値を指定する **publisher_login** の **@property** し、新しいログインを **@value**します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのプロパティの指定された値でパブリッシャーを構成する場合を含む **merge_job_login** と **merge_job_password**, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
#### プル サブスクリプションに対するマージ エージェントのセキュリティ設定を変更するには  
  
1.  サブスクライバーで、次のように実行します。 [sp_helpmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md), を指定して **@publication**します。 これにより、サブスクライバーで実行されるマージ エージェントのセキュリティ設定を含むサブスクリプションのプロパティが返されます。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_change_subscription_properties](../../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), を指定して **@publisher**, 、**@publisher_db**, 、**@publication**, 、のセキュリティ プロパティの名前 **@property**, 、およびプロパティの新しい値 **@value**します。  
  
3.  次のセキュリティ プロパティから変更するものに対してそれぞれ手順 2. を繰り返します。  
  
    -   このアカウントのパスワードを Windows アカウントは、エージェントを実行するまたはだけを変更するには、指定の値の **merge_job_password** の **@property** と新しいパスワードを **@value**します。 アカウント自体を変更するには、値を指定する手順 2 を繰り返して、 **merge_job_login** の **@property** と新しい Windows アカウントを **@value**します。  
  
    -   ディストリビューターに接続するときに使用するセキュリティ モードを変更するには、値を指定 **distributor_security_mode** の **@property** の **1** (Windows 統合認証) または **0** (SQL Server 認証) の **@value**します。  
  
    -   SQL Server 認証にディストリビューターのセキュリティ モードを変更するとき、または SQL Server 認証のログイン情報を変更する場合は、値を指定して **distributor_password 用途** の **@property** と新しいパスワードを **@value**します。 手順 2 の値を指定する **distributor_login** の **@property** し、新しいログインを **@value**します。  
  
    -   パブリッシャーに接続するときに使用するセキュリティ モードを変更するには、値を指定 **publisher_security_mode** の **@property** の **1** (Windows 統合認証) または **0** (SQL Server 認証) の **@value**します。  
  
    -   SQL Server 認証にパブリッシャーのセキュリティ モードを変更するとき、または SQL Server 認証のログイン情報を変更する場合は、値を指定して **publisher_password** の **@property** と新しいパスワードを **@value**します。 手順 2 の値を指定する **publisher_login** の **@property** し、新しいログインを **@value**します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
#### サブスクライバーのフィルター選択されたスナップショットを生成する、スナップショット エージェントのセキュリティ設定を変更するには  
  
1.  パブリッシャーで実行 [sp_helpdynamicsnapshot_job](../../../relational-databases/system-stored-procedures/sp-helpdynamicsnapshot-job-transact-sql.md), を指定して **@publication**します。 結果には、設定の値に注意してください **job_name** を変更するサブスクライバーのパーティションにします。  
  
2.  パブリッシャーで実行 [sp_changedynamicsnapshot_job](../../../relational-databases/system-stored-procedures/sp-changedynamicsnapshot-job-transact-sql.md), を指定して **@publication**, 、手順 1. で得た値 **@dynamic_snapshot_jobname**, と新しいパスワードを **@job_password** ログインし、エージェントを実行する Windows アカウントのパスワード、または **@job_login** と **@job_password**します。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
#### キュー リーダー エージェントのセキュリティ設定を変更するには  
  
1.  ディストリビューターで実行 [sp_helpqreader_agent](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md)します。 これにより、キュー リーダー エージェントの実行時に使用される現在の Windows アカウントが返されます。  
  
    -   ディストリビューターで実行 [sp_changeqreader_agent](../../../relational-databases/system-stored-procedures/sp-changeqreader-agent-transact-sql.md), 、Windows アカウントの設定を指定する **@job_login** と **@job_passwsord**します。  
  
    > [!NOTE]  
    >  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。 ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 エージェントのセキュリティ設定を変更すると、このディストリビューション データベースを使用するすべてのパブリッシャーのすべてのパブリケーションの設定に影響が及びます。  
  
2.  キュー リーダー エージェントは、サブスクリプションのディストリビューション エージェントと同じ接続コンテキストを使用して、サブスクライバーへの接続を作成します。  
  
#### パブリッシャーへの接続時に即時更新サブスクライバーで使用するセキュリティ モードを変更するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)します。 指定 **@publisher**, 、**@publication**, 、パブリケーション データベースの名前 **@publisher_db**, 、次のいずれかの値 **@security_mode**:  
  
    -   **0** - パブリッシャーで更新を作成する場合に SQL Server  認証を使用します。 このオプションの場合、パブリッシャーで、 **@login** および **@password**に有効なログインを指定する必要があります。  
  
    -   **1** - パブリッシャーへの接続時にサブスクライバーで変更するユーザーのセキュリティ コンテキストを使用します。 参照してください [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) 制限についてはこのセキュリティ モードに関連します。  
  
    -   **2** 使用するには、既存のユーザー定義されたリンク サーバー ログインを使用して作成 [sp_addlinkedserver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)します。  
  
#### リモート ディストリビューターのパスワードを変更するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_changedistributor_password](../../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md), 、新しいパスワードに対してこのログインを指定して **@password**します。  
  
    > [!IMPORTANT]  
    >  パスワードは変更しないで **distributor_admin** 直接します。  
  
2.  このリモート ディストリビューターを使用するすべてのパブリッシャーで実行 [sp_changedistributor_password](../../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md), 、手順 1. のパスワードを指定する **@password**します。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] を使用します。  
  
#### レプリケーション サーバーに格納されているパスワードのインスタンスをすべて変更するには  
  
1.  使用して、レプリケーション サーバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 手順 1. の接続を使用してクラスです。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeReplicationServerPasswords%2A> メソッドです。 次のパラメーターを指定します。  
  
    -   *security_mode* - <xref:Microsoft.SqlServer.Replication.ReplicationSecurityMode> パスワードのすべてのインスタンスが変更されている認証の種類を指定する値。  
  
    -   *ログイン* -パスワードのすべてのインスタンスが変更されているログインします。  
  
    -   *パスワード* -新しいパスワード値です。  
  
        > [!IMPORTANT]  
        >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、Windows .NET Framework に用意されている [暗号化サービス](http://go.microsoft.com/fwlink/?LinkId=34733) を使用します。  
  
        > [!NOTE]  
        >  メンバーだけが、 **sysadmin** 固定サーバー ロールは、このメソッドを呼び出すことができます。  
  
4.  パスワードを更新する必要のある、レプリケーション トポロジ内のすべてのサーバーについて、手順 1. から手順 3. を繰り返します。  
  
#### ディストリビューション エージェントのセキュリティ設定をプッシュ サブスクリプション用からトランザクション パブリケーション用に変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 、サブスクリプション、およびセットからの接続手順 1. のプロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  インスタンスで 1 つ以上の次のセキュリティ プロパティを設定 <xref:Microsoft.SqlServer.Replication.TransSubscription>:  
  
    -   エージェントを実行する Windows アカウントの資格情報を変更するには、設定、 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>します。  
  
    -   エージェントがサブスクライバーに接続するときに使用する認証の種類として Windows 統合認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティを **true**します。  
  
    -   エージェントがサブスクライバーに接続するときに使用する認証の種類として [SQL Server 認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティを **false**, 、サブスクライバーのログイン資格情報を指定し、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドです。  
  
        > [!NOTE]  
        >  指定された Windows 資格情報を使用してディストリビューターへのエージェント接続が常に作成 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>します。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
#### ディストリビューション エージェントのセキュリティ設定をプル サブスクリプション用からトランザクション パブリケーション用に変更するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 、サブスクリプション、およびセットからの接続手順 1. のプロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  インスタンスで 1 つ以上の次のセキュリティ プロパティを設定 <xref:Microsoft.SqlServer.Replication.TransPullSubscription>:  
  
    -   エージェントを実行する Windows アカウントの資格情報を変更するには、設定、 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>します。  
  
    -   エージェントがディストリビューターに接続するときに使用する認証の種類として Windows 統合認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティを **true**します。  
  
    -   エージェントがディストリビューターに接続するときに使用する認証の種類として [SQL Server 認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティを **false**, 、ディストリビューターのログイン資格情報を指定し、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドです。  
  
        > [!NOTE]  
        >  指定された Windows 資格情報を使用してサブスクライバーへのエージェント接続が常に作成 <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>します。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
#### マージ エージェントのセキュリティ設定をプル サブスクリプション用からマージ パブリケーション用に変更するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 、サブスクリプション、およびセットからの接続手順 1. のプロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  インスタンスで 1 つ以上の次のセキュリティ プロパティを設定 <xref:Microsoft.SqlServer.Replication.MergePullSubscription>:  
  
    -   エージェントを実行する Windows アカウントの資格情報を変更するには、設定、 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>します。  
  
    -   エージェントがディストリビューターに接続するときに使用する認証の種類として Windows 統合認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティを **true**します。  
  
    -   エージェントがディストリビューターに接続するときに使用する認証の種類として [SQL Server 認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> プロパティを **false**, 、ディストリビューターのログイン資格情報を指定し、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドです。  
  
    -   エージェントがパブリッシャーに接続するときに使用する認証の種類として Windows 統合認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> プロパティを **true**します。  
  
    -   エージェントがパブリッシャーに接続するときに使用する認証の種類として [SQL Server 認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> プロパティを **false**, 、パブリッシャーのログイン資格情報を指定し、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドです。  
  
        > [!NOTE]  
        >  指定された Windows 資格情報を使用してサブスクライバーへのエージェント接続が常に作成 <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>します。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
#### マージ エージェントのセキュリティ設定をプッシュ サブスクリプション用からマージ パブリケーション用に変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 、サブスクリプション、およびセットからの接続手順 1. のプロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
5.  インスタンスで 1 つ以上の次のセキュリティ プロパティを設定 <xref:Microsoft.SqlServer.Replication.MergeSubscription>:  
  
    -   エージェントを実行する Windows アカウントの資格情報を変更するには、設定、 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A>します。  
  
    -   エージェントがサブスクライバーに接続するときに使用する認証の種類として Windows 統合認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティを **true**します。  
  
    -   エージェントがサブスクライバーに接続するときに使用する認証の種類として [SQL Server 認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> プロパティを **false**, 、サブスクライバーのログイン資格情報を指定し、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> フィールドです。  
  
    -   エージェントがパブリッシャーに接続するときに使用する認証の種類として Windows 統合認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.MergeSubscription.PublisherSecurity%2A> プロパティを **true**します。  
  
    -   エージェントがパブリッシャーに接続するときに使用する認証の種類として [SQL Server 認証を指定する、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> のフィールド、 <xref:Microsoft.SqlServer.Replication.MergeSubscription.PublisherSecurity%2A> プロパティを **false**, 、パブリッシャーのログイン資格情報を指定し、 <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext.SqlStandardPassword%2A> フィールドです。  
  
        > [!NOTE]  
        >  指定された Windows 資格情報を使用してディストリビューターへのエージェント接続が常に作成 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>します。 このアカウントは、Windows 認証を使ってリモート接続を確立する際にも使用されます。  
  
6.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
#### 即時更新サブスクライバーがトランザクション パブリッシャーへの接続時に使用するログイン情報を変更するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> サブスクリプション データベースのクラスです。 指定 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.Name%2A> と <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 2. で指定したデータベースのプロパティが正しく定義されていないか、サブスクリプション データベースが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LinkPublicationForUpdateableSubscription%2A> メソッドを次のパラメーターを渡します。  
  
    -   *パブリッシャー* -パブリッシャーの名前。  
  
    -   *PublisherDB* -パブリケーション データベースの名前。  
  
    -   *パブリケーション* - 即時更新サブスクライバーがサブスクライブしているパブリケーションの名前。  
  
    -   *ディストリビューター* -ディストリビューターの名前。  
  
    -   *PublisherSecurity* - <xref:Microsoft.SqlServer.Replication.PublisherConnectionSecurityContext> 接続のパブリッシャーとログインの資格情報への接続時に即時更新サブスクライバーで使用されるセキュリティ モードの種類を指定するオブジェクト。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、指定されたログイン値をチェックし、該当する Windows ログイン、または、サーバー上のレプリケーションによって格納された SQL Server ログインを対象にすべてのパスワードを変更します。  
  
 [!code-csharp[HowTo#rmo_ChangeServerPasswords](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changeserverpasswords)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeServerPasswords](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changeserverpasswords)]  
  
##  <a name="FollowUp"></a> フォロー アップ: レプリケーションのセキュリティ設定を変更した後  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## 参照  
 [レプリケーション管理オブジェクトの概念](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [レプリケーション スクリプト、および #40; をアップグレードします。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md)   
 [レプリケーションのログインとパスワードの管理](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション セキュリティの推奨事項](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  