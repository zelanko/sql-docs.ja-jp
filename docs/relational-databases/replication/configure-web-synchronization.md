---
title: "Web 同期の構成 | Microsoft Docs"
ms.custom: ""
ms.date: "01/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.SNAPSHARE.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.SNAPSHARE.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.VIRDIRINFO.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.CLIENTAUTH.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.DIRACCESS.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.SUBTYPE.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.ANONACCESS.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.WEBSERV.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.CLIENTAUTH.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.SUBTYPE.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.COMPLETEWIZ.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.DIRACCESS.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.ANONACCESS.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.AUTHACCESS.F1"
  - "SQL10.REP.CONFIGWEBSYNCWIZARD.AUTHACCESS.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.COMPLETEWIZ.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.VIRDIRINFO.F1"
  - "SQL13.REP.CONFIGWEBSYNCWIZARD.WEBSERV.F1"
helpviewer_keywords: 
  - "Web 同期, セキュリティに関する推奨事項"
  - "Web 同期, 構成"
ms.assetid: 21f8e4d4-cd07-4856-98f0-9c9890ebbc82
caps.latest.revision: 74
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 73
---
# Web 同期の構成
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Web 同期オプション [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] マージ レプリケーションでは、インターネット経由で HTTPS プロトコルを使用してデータのレプリケーション。 Web 同期を使用するには、最初に次の構成操作を実行する必要があります。  
  
1.  新しいドメイン ユーザー アカウントを作成し、マップ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインします。  
  
2.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) を実行しているコンピューターで、サブスクリプションが同期されるように構成します。  
  
3.  Web 同期が許可されるようにマージ パブリケーションを構成します。  
  
4.  Web 同期が使用されるように 1 つ以上のサブスクリプションを構成します。  
  
> [!NOTE]  
>  大量のデータをレプリケートまたはなどの大規模なデータ型を使用する予定の場合 **varchar (max)**, 、」セクションでは、大規模なボリュームのデータのレプリケート」を参照します。  
  
 Web 同期を正しく設定するには、特定の要件やポリシーを満たすためにセキュリティをどのように構成するかを決める必要があります。 先にこれらについて決定し、必要なアカウントを作成してから、IIS、パブリケーション、およびサブスクリプションの構成を開始することをお勧めします。  
  
 以降の手順では、説明を簡単にするために、ローカル アカウントを使用した場合の簡素化されたセキュリティ構成について説明します。 この簡素化された構成は、IIS と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパブリッシャーおよびディストリビューターの両方を同一のコンピューターで実行する環境に適しています。ただし、運用環境ではマルチサーバー トポロジを使用する可能性が高く、その方が推奨されます。 この手順のローカル アカウントは、ドメイン アカウントに置き換えることもできます。  
  
## 新しいアカウントの作成と SQL Server ログインのマッピング  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナー (replisapi.dll) は、レプリケーション Web サイトに関連付けられたアプリケーション プールに指定されているアカウントを借用することでパブリッシャーに接続します。  
  
 使用するアカウント、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」の説明に従って、レプリケーション リスナーのアクセス許可が必要する [マージ エージェント セキュリティ](../../relational-databases/replication/merge-agent-security.md), 、セクション「パブリッシャーまたはディストリビューターへの接続です。」 このアカウントに必要な権限の概要を以下に示します。  
  
-   パブリケーション アクセス リスト (PAL) のメンバーである。  
  
-   パブリケーション データベースのユーザーに関連付けられたログインにマップされている。  
  
-   ディストリビューション データベース内のユーザーに関連付けられているログインにマップされている。  
  
-   スナップショット共有の読み取り権限を持つ。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションを初めて使用する場合は、レプリケーション エージェントのアカウントとログインも作成する必要があります。 詳細については、このトピックの「パブリケーションの構成」および「サブスクリプションの構成」を参照してください。  
  
 Web 同期を構成する前に、このトピックの「Web 同期のセキュリティの推奨事項」を一読することをお勧めします。 Web 同期のセキュリティの詳細については、次を参照してください。 [Web 同期のセキュリティ アーキテクチャ](../../relational-databases/replication/security/security-architecture-for-web-synchronization.md)します。  
  
## IIS を実行しているコンピューターの構成  
 Web 同期を使用するには、IIS をインストールして構成する必要があります。 レプリケーション Web サイトの URL がないと、Web 同期を使用するようにパブリケーションを構成できません。  
  
 Web 同期は、IIS バージョン 5.0 以降でサポートされます。 IIS 7.0 では、Web 同期の構成ウィザードはサポートされていません。 IIS サーバーに web 同期コンポーネントを使用して、SQL Server 2012 以降をお勧めユーザーによりインストール SQL Server レプリケーションを使用します。 無料の SQL Server Express エディションを指定できます。  
  
 Web 同期では SSL は必須です。 証明機関によって発行されたセキュリティ証明書が必要になります。 テストだけが目的の場合は、独自に発行したセキュリティ証明書を使用できます。  
   
  
 **Web 同期用に IIS を構成するには**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Configure IIS for Web Synchronization](../../relational-databases/replication/configure-iis-for-web-synchronization.md)  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Configure IIS 7 for Web Synchronization](../../relational-databases/replication/configure-iis-7-for-web-synchronization.md)  
  
## Web ガーデンの作成  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーでは、スレッドごとに同時に 2 つの同期処理がサポートされます。 この制限を超えると、レプリケーション リスナーが応答しなくなる可能性があります。 replisapi.dll に割り当てられるスレッドの数は、アプリケーション プールの "ワーカー プロセスの最大数" プロパティで決まります。 既定では、このプロパティは 1 に設定されます。  
  
 1 つの CPU で同時にサポートできる同期処理の数を増やすには、"ワーカー プロセスの最大数" プロパティの値を大きくします。 CPU ごとのワーカー プロセスの数を増やしてスケールアウトすることを、"Web ガーデン" を作成するといいます。  
  
 Web ガーデンを作成すると、同時に 3 つ以上のサブスクライバーを同期できるようになります。 このとき、replisapi.dll による CPU 使用率も増加するため、サーバーの全体的なパフォーマンスは低下することがあります。 "ワーカー プロセスの最大数" の値を選択するときは、それらのバランスを考慮することが重要です。  
  
#### IIS 7 でワーカー プロセスの最大数を増やす  
  
1.   **インターネット インフォメーション サービス (IIS) マネージャー**, ローカル サーバー] ノードを展開しをクリックし、 **アプリケーション プール** ノードです。  
  
2.  Web 同期サイトに関連付けられているアプリケーション プールを選択し、クリックして **の詳細設定** 上、 **アクション** ウィンドウです。  
  
3.  [詳細設定] ダイアログ ボックスで、下にある、 **プロセス モデル** というラベルの行見出しをクリックして **ワーカー プロセスの最大数**します。 プロパティの値を変更し、クリックして **OK**します。  
  
## パブリケーションの構成  
 Web 同期を使用するには、標準のマージ トポロジと同じ方法でパブリケーションを作成します。 詳細については、次を参照してください。 [発行データおよびデータベース オブジェクト](../../relational-databases/replication/publish/publish-data-and-database-objects.md)します。  
  
 パブリケーションを作成した後は、次の方法のいずれかを使用して Web 同期を許可するオプションを有効にする: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 、[!INCLUDE[tsql](../../includes/tsql-md.md)], 、またはレプリケーション管理オブジェクト (RMO)。 Web 同期を有効にするには、サブスクライバー接続の Web サーバー アドレスを指定する必要があります。  
  
 初めてパブリッシャーを使用している場合は、ディストリビューターおよびスナップショット共有も構成する必要があります。 各サブスクライバー側のマージ エージェントには、スナップショット共有の読み取り権限が必要です。 詳細については、次を参照してください。 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md) と [スナップショット フォルダーをセキュリティで保護された](../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
 **gen** websync の予約語は、xml ファイルです。 という名前の列を含むテーブルをパブリッシュしないで **gen**します。  
  
## サブスクリプションの構成  
 パブリケーションを有効にし、IIS を構成した後、プル サブスクリプションを作成し、そのプル サブスクリプションが IIS を使用して同期するように指定します。 (Web 同期はプル サブスクリプションでのみサポートされます)。  
  
## SQL Server の以前のバージョンからアップグレードします。  
 構成されている既存の Web 同期トポロジがあり、アップグレードする場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、Replisapi.dll の最新バージョンを Web 同期で使用される仮想ディレクトリにコピーされることを確認する必要があります。 既定では、Replisapi.dll の最新バージョンは C:\Program files \microsoft SQL Server である\\< nnn\>\COM します。  
  
## 大量のデータのレプリケート  
 サブスクライバー コンピューター上で発生する可能性があるメモリの問題を回避できるように、Web 同期では、変更の転送に使用する XML ファイルに既定の最大サイズの 100 MB を使用します。 この制限は、次のレジストリ キーを設定して引き上げることができます。  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\Replication**  
  
 **WebSyncMaxXmlSize DWORD 2000000**  
  
 このキーに許容される値の範囲は 100 MB ～ 4 GB です。 値は KB 単位で指定します。 このパラメーターに大きな値を設定することで、その量のデータを同期できることが保証されるわけではありません。 サブスクライバー コンピューター上で使用できる連続したメモリの量によって制限することが効果的です。 100 MB を超える値を設定する必要がある場合は、値を段階的に増加させ、サブスクライバー上の一般的なワークロードでメモリの使用量をテストすることをお勧めします。  
  
 XML ファイルの最大サイズが 4 GB でも、バッチ内のそのファイルからの変更がレプリケーションによって同期されます。 データとメタデータの最大バッチ サイズは 25 MB です。 各バッチ内のデータが約 20 MB を超えないようにする必要があります。この場合、メタデータやその他のオーバーヘッドも考慮に入れます。 この制限による影響を次に示します。  
  
-   データとメタデータが 25 MB を超す要因となる列はレプリケートできません。 これは、大規模なデータ型をなどが含まれた行をレプリケートするときに問題がある可能性があります **varchar (max)**します。  
  
-   大量のデータをレプリケートする場合に、マージ エージェントのバッチ サイズの調整が必要になることがあります。  
  
 マージ レプリケーションのバッチ サイズの単位で *世代*, 、アーティクルごとに変更のコレクションであります。 使用して、バッチ内の生成結果の数が指定されている、–**DownloadGenerationsPerBatch** と –**UploadGenerationsPerBatch** 、マージ エージェントのパラメーターです。 詳細については、次を参照してください。 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)します。  
  
 大量のデータを扱う場合は、バッチ処理の各パラメーターに小さい数を指定します。 最初は値を 10 にして、アプリケーションのニーズとパフォーマンスに応じて調整することをお勧めします。 通常、これらのパラメーターは、エージェント プロファイルで指定します。 プロファイルの詳細については、次を参照してください。 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)します。  
  
## Web 同期のセキュリティの推奨事項  
 Web 同期にはセキュリティ関連の選択項目が多数あります。 次の方法が推奨されます。  
  
-    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターとパブリッシャーが同じコンピューター (マージ レプリケーションで一般的なセットアップ) にすることができます。 ただし、IIS は別のコンピューターにインストールする必要があります。  
  
-   SSL (Secure Sockets Layer) を使用して、IIS を実行しているコンピューターとサブスクライバーとの間の接続を暗号化します。 これは、Web 同期では必須です。  
  
-   サブスクライバーから IIS までの接続に基本認証を使用します。 基本認証を使用すると、IIS では、委任を必要とすることなくサブスクライバーの代わりにパブリッシャーやディストリビューターに接続できます。 統合認証を使用する場合は、委任が必要です。  
  
    > [!NOTE]  
    >  基本認証は、資格情報を IIS に渡すための方法です。 基本認証がウィンドウの指定できない IIS への接続に対してドメイン アカウントを使用します。  
  
-   スナップショット エージェントを Windows ドメイン アカウントで実行するように指定し、エージェントがそのアカウントとして接続を確立するように指定します  (これは既定の構成です)。各マージ エージェントを、サブスクライバー コンピューターを使用するユーザーのドメイン アカウントで実行するように指定し、エージェントがそのアカウントとして接続を確立するように指定します。  
  
     エージェントが必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
-   同じドメイン アカウントのアカウントとパスワードを指定すると、マージ エージェントを使用して 1 つとして指定、 **Web サーバー情報** または値を指定するときにサブスクリプションの新規作成ウィザードのページ、 **@internet_url** と **@internet_login** のパラメーター [sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。 このアカウントには、スナップショット共有の読み取り権限が必要です。  
  
-   各パブリケーションでは、IIS 用に個別の仮想ディレクトリを使用する必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナー (Replisapi.dll) の実行に使用するアカウントは、同期の際にパブリッシャーとディストリビューターに接続するアカウントでもあります。 したがって、パブリッシャーとディストリビューターで SQL ログイン アカウントにマップされている必要があります。 詳細については、「アクセス許可 [SQL Server レプリケーション リスナーの設定」」セクションを参照してください、 [Web 同期用に IIS 構成](../../relational-databases/replication/configure-iis-for-web-synchronization.md)します。  
  
-   IIS を実行しているコンピューターにパブリッシャーからスナップショットを配信するときに、FTP を使用できます。 IIS を実行しているコンピューターからサブスクライバーにスナップショットを配信するときには、常に HTTPS が使用されます。 詳細については、次を参照してください。 [FTP でスナップショットを転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)します。  
  
-   レプリケーション トポロジ内のサーバーがファイアウォールの内側にあるとき、Web 同期を有効にするために、ファイアウォールのポートを開くことが必要になる場合があります。  
  
    -   サブスクライバー コンピューターは、SSL を使用する HTTPS (通常はポート 443 を使用するように構成されます) 経由で、IIS を実行しているコンピューターに接続します。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーは、ポート 80 を使用するように構成は、通常、HTTP 経由で接続できます。  
  
    -   通常、IIS を実行しているコンピューターは、ポート 1433 (既定のインスタンス用) を使用してパブリッシャーまたはディストリビューターに接続します。 パブリッシャーまたはディストリビューターが、サーバー上の既定のインスタンスとは別に存在する名前付きインスタンスである場合、その名前付きインスタンスへの接続には通常はポート 1500 が使用されます。  
  
    -   IIS を実行しているコンピューターがファイアウォールによってディストリビューターから分離すると、スナップショットの配信を使用する FTP 共有、FTP に使用するポートを開く必要があります。 詳細については、次を参照してください。 [FTP でスナップショットを転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)します。  
  
> [!IMPORTANT]  
>  ファイアウォールのポートを開くと、サーバーが攻撃を受けやすくなります。 ポートを開く前に、ファイアウォール システムについて理解しておいてください。 詳細については、「 [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)」を参照してください。  
  
## 参照  
 [マージ レプリケーションの Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  