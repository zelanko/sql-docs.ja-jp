---
title: "[サブスクリプションのプロパティ - サブスクライバー] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subproperties.subscriber.f1"
helpviewer_keywords: 
  - "[サブスクリプションのプロパティ] ダイアログ ボックス"
ms.assetid: bef66929-3234-4a45-8ec4-3b271519d07a
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# [サブスクリプションのプロパティ - サブスクライバー]
   **サブスクリプションのプロパティ** 、サブスクライバーでのダイアログ ボックスでは、表示し、プル サブスクリプションのプロパティを設定することができます。  
  
 内の各プロパティ、 **サブスクリプションのプロパティ** ] ダイアログ ボックスに説明が含まれます。 プロパティをクリックすると、ダイアログ ボックスの一番下に説明が表示されます。 このトピックでは、いくつかのプロパティについて追加情報を示します。 プロパティは次のように分類されます。  
  
-   すべてのサブスクリプションに適用されるプロパティ。  
  
-   トランザクション サブスクリプションに適用されるプロパティ。  
  
-   マージ サブスクリプションに適用されるプロパティ。  
  
 読み取り専用として表示されているオプションの場合、サブスクリプションが作成されている場合にのみ設定できます。 サブスクリプションの新規作成ウィザードで使用することのできないオプションを設定する場合は、サブスクリプションをストアド プロシージャで作成します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 」および「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」を参照してください。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントのジョブがサブスクリプションに対してまだ作成されていない場合、ほとんどのサブスクリプション プロパティは表示されません。 プル サブスクリプションのエージェント ジョブを作成するには、実行 [sp_addpullsubscription_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) スナップショット パブリケーションまたはトランザクション パブリケーションに対するサブスクリプション) (または [sp_addmergepullsubscription_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) (のマージ パブリケーションに対するサブスクリプション)。  
  
## すべてのサブスクリプションに対するオプション  
 **[スナップショットからパブリッシュされたデータを初期化]**  
 サブスクリプションがスナップショットで初期化されるか (既定)、別の方法で初期化されるかを決定します。 サブスクリプションの初期化の詳細については、次を参照してください。 [サブスクリプションを初期化](../../relational-databases/replication/initialize-a-subscription.md)します。  
  
 **[スナップショットの場所]**  
 初期化または再初期化の際にアクセスするスナップショット ファイルの場所を決定します。 場所は次の値のいずれかです。  
  
-   **既定の場所**: 既定の場所はディストリビューターを構成するときに定義されます。 詳細については、次を参照してください。 [指定、既定のスナップショットの場所と #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)します。  
  
-   **代替フォルダー**: で指定できる、別の場所、 **パブリケーションのプロパティ** ] ダイアログ ボックス。 詳細については、次を参照してください。 [代替スナップショット フォルダーの場所](../../relational-databases/replication/alternate-snapshot-folder-locations.md)します。  
  
-   **動的スナップショット フォルダー**: パラメーター化された行フィルターを使用するマージ パブリケーションのスナップショットの場所。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
-   **FTP フォルダー**: フォルダーのファイル転送プロトコル (FTP) サーバーにアクセスします。 詳細については、次を参照してください。 [FTP でスナップショットを転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)します。  
  
 **[スナップショット フォルダー]**  
 以外の任意の値を選択する場合は、 **既定の場所** の **スナップショットの場所** オプション、スナップショット フォルダーへのパスを指定する必要があります。  
  
 **[Windows 同期マネージャーを使用]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーを使用して、サブスクリプションを同期化できるかどうかを決定します。  
  
 **セキュリティ**  
 クリックして、 **エージェント プロセス アカウント** 行を [プロパティ] ボタンをクリックして (**...**)、ディストリビューション エージェントまたはマージ エージェントをサブスクライバーで実行するアカウントを変更します。 接続に関するセキュリティ オプションは、サブスクリプションの種類によって異なります。  
  
-   トランザクション パブリケーションに対するサブスクリプションの場合: ディストリビューション エージェントがディストリビューターへの接続を作成するアカウントを変更するにはクリックして **ディストリビューター接続**, 、[プロパティ] ボタンをクリックして (**...**)。  
  
-   トランザクション パブリケーションに対する即時更新サブスクリプション: サブスクライバーからパブリッシャーへの変更を反映するために使用する方法を変更する前に説明したディストリビューター接続だけでなく:] をクリックして **パブリッシャー接続**, 、[プロパティ] ボタンをクリックして (**...**)。  
  
-   マージ パブリケーションに対するサブスクリプションをクリックして **パブリッシャー接続**, 、[プロパティ] ボタンをクリックして (**...**)。  
  
 各エージェントに必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
## トランザクション サブスクリプションに対するオプション  
 **[更新可能なサブスクリプション]**  
 サブスクライバーの変更がパブリッシャーにレプリケートされるかどうかを決定します。 変更は、キュー更新または即時更新を使用してレプリケートすることができます。 オプション **サブスクライバーの更新方法** メソッドを使用して決定します。 詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
## マージ サブスクリプションに対するオプション  
 **[パーティション定義 (HOST_NAME)]**  
 マージ レプリケーションの 2 つのシステム関数 (または両方のフィルターがどちらの関数を参照している場合) のいずれかの評価をサブスクライバーが受け取るデータを特定の同期中に使用するパブリケーションにパラメーター化されたフィルターの: **SUSER_SNAME()** または **HOST_NAME()**します。 既定では、 **HOST_NAME()** 、マージ エージェントが実行されているがサブスクリプションの新規作成ウィザードでこの値を上書きするコンピューターの名前を返します。 詳細については、パラメーター化フィルターをオーバーライドする **HOST_NAME()**, を参照してください [パラメーター化された行フィルター](../../relational-databases/replication/merge/parameterized-row-filters.md)します。  
  
 **サブスクリプションの種類** と **優先順位**  
 サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションであるかどうかを表示します (これは、サブスクリプションが作成された後では変更できません)。 サーバー サブスクリプションは、他のサブスクライバーへのデータの再パブリッシュと、競合解決方法の優先度の割り当てができます。  
  
 サブスクリプションの新規作成ウィザードでサーバーのサブスクリプションの種類を選択した場合、サブスクライバーには競合解決方法で使用される優先度が割り当てられます。  
  
 **[競合を対話的に解決する (対話的な解決をサポートするアーティクルに対してのみ適用されます)]**  
 インタラクティブ競合回避モジュールのユーザー インターフェイスを使用して、マージ同期中の競合を回避するかどうかを決定します。 値が必要です **を有効にする** の **Windows 同期マネージャーを使用して**します。 詳細については、「 [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md)」を参照してください。  
  
 **[Web 同期]**  
 **Web 同期を使用して** に接続するかどうか、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、サブスクリプションを同期するインターネット インフォメーション サービス (IIS) サーバー。 このオプションは、パブリケーションに対して Web 同期が有効である場合のみ有効です。 詳細については、次を参照してください。 [マージ レプリケーション用に Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)します。  
  
 選択した場合 **True** の **Web 同期を使用**:  
  
-   IIS でサーバーに完全なアドレスを入力 **Web サーバー アドレス**です。  
  
-   をクリックして、 **Web サーバーの接続** 行を [プロパティ] ボタンをクリックして (**...**) を設定またはサブスクライバーが IIS サーバーに接続するためのアカウントを変更します。  
  
-   変更 **Web サーバーのタイムアウト** 必要な場合です。 タイムアウトは Web 同期要求の期限が切れるまでの期間 (秒単位) です。  
  
 構成の詳細については、次を参照してください。 [Web 同期の構成](../../relational-databases/replication/configure-web-synchronization.md)します。  
  
## 参照  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  