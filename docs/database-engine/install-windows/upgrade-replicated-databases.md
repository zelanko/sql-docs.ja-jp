---
title: "レプリケートされたデータベースのアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ レプリケーションのデータベース アップグレード [SQL Server レプリケーション]"
  - "レプリケーション [SQL Server]、アップグレード"
  - "トランザクション レプリケーション、データベースのアップグレード"
  - "スナップショット レプリケーション [SQL Server]、データベースのアップグレード"
  - "レプリケートされたデータベースのアップグレード"
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
caps.latest.revision: 74
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 73
---
# レプリケートされたデータベースのアップグレード
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、レプリケートされたデータベースを以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードすることができます。ノードのアップグレード中は、その他のノードでの操作を停止する必要はありません。 トポロジでサポートされるバージョンに関して、以下の規則が守られていることを確認してください。  
  
-   ディストリビューターは、パブリッシャーのバージョン以上であればどのバージョンでも使用できます (多くの場合、ディストリビューターはパブリッシャーと同じインスタンスです)。  
  
-   パブリッシャーは、ディストリビューターのバージョン以下であればどのバージョンでも使用できます。  
  
-   サブスクライバーのバージョンは、次のように、パブリケーションの種類によって異なります。  
  
    -   トランザクション パブリケーションのサブスクライバーは、2 つのパブリッシャー バージョンのうちどちらでも使用できます。 たとえば、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のパブリッシャーには [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] と [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] のサブスクライバーを設定することができます。[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] のパブリッシャーには [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] と [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のサブスクライバーを設定することができます。  
  
    -   マージ パブリケーションのサブスクライバーは、パブリッシャーのバージョン以下であればどのバージョンでも使用できます。  
  
> [!NOTE]  
>  このトピックは、セットアップ ヘルプ ドキュメントおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックで参照できます。 セットアップ ヘルプ ドキュメントで太字で表示されているトピック リンクは、オンライン ブックでのみ参照可能なトピックを示しています。  
  
## アップグレードの前にトランザクション レプリケーション用にログ リーダー エージェントを実行する方法  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする前には、パブリッシュされたテーブルからコミットされたすべてのトランザクションが、ログ リーダー エージェントによって処理されているかどうかを確認する必要があります。 すべてのトランザクションが処理されたことを確認するには、トランザクション パブリケーションを含んだ各データベースに対して次の手順を実行します。  
  
1.  データベースのログ リーダー エージェントが実行されていることを確認します。 既定では、エージェントは継続的に実行されています。  
  
2.  パブリッシュされたテーブル上のユーザー アクティビティを停止します。  
  
3.  トランザクションをディストリビューション データベースにコピーする時間をログ リーダー エージェントに与えてから、エージェントを停止します。  
  
4.  [sp_replcmds](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) を実行し、すべてのトランザクションが処理されたことを確認します。 この手順の結果セットを空にする必要があります。  
  
5.  [sp_replflush](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) を実行し、sp_replcmds から接続を閉じます。  
  
6.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのサーバー アップグレードを実行します。  
  
7.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントとログ リーダー エージェントがアップグレードの後に自動的に起動しない場合は、これらを再起動します。  
  
## アップグレード後のマージ レプリケーション用エージェントの実行  
 アップグレード後は、マージ パブリケーションごとにスナップショット エージェントを実行し、サブスクリプションごとにマージ エージェントを実行して、レプリケーション メタデータを更新します。 サブスクリプションを再初期化する必要がないので、新しいスナップショットを適用する必要はありません。 サブスクリプション メタデータは、アップグレード後に最初にマージ エージェントを実行したときに更新されます。 そのため、サブスクリプション データベースは、パブリッシャーのアップグレード中にオンライン状態でアクティブなままにすることができます。  
  
 マージ レプリケーションでは、パブリケーション データベースおよびサブスクリプション データベース内の多数のシステム テーブルに、パブリケーション メタデータおよびサブスクリプション メタデータが格納されます。 スナップショット エージェントを実行すると、パブリケーション メタデータが更新され、マージ エージェントを実行すると、サブスクリプション メタデータが更新されます。 生成が必要なのはパブリケーション スナップショットのみです。 パラメーター化されたフィルターがマージ パブリケーションで使用される場合は、各パーティションにもスナップショットが必要です。 これらのパーティション スナップショットを更新する必要はありません   
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、レプリケーション モニター、またはコマンド ラインで各エージェントを実行します。 スナップショット エージェントの実行の詳細については、次のトピックを参照してください。  
  
-   [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 マージ エージェントの実行の詳細については、次のトピックを参照してください。  
  
-   [プル サブスクリプションの同期](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [プッシュ サブスクリプションの同期](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
 マージ レプリケーションを使用するトポロジで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をアップグレードした後に、新しい機能を使用する場合は、すべてのパブリケーションのパブリケーション互換性レベルを変更します。  
  
## Standard Edition、Workgroup Edition、または Express Edition へのアップグレード  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のいずれかのエディションから別のエディションへアップグレードする前に、現在使用している機能がアップグレード先のエディションでサポートされているかどうかを確認します。 詳細については、「[SQL Server 2016 の各エディションでサポートされる機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」のレプリケーションに関するセクションを参照してください。  
  
## マージ レプリケーションの Web 同期  
 マージ レプリケーションの Web 同期オプションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナー (replisapi.dll) を、同期に使用するインターネット インフォメーション サービス (IIS) サーバーの仮想ディレクトリにコピーする必要があります。 Web 同期を構成すると、Web 同期の構成ウィザードにより、ファイルが仮想ディレクトリにコピーされます。 IIS サーバーにインストールされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをアップグレードする場合、replisapi.dll を COM ディレクトリから IIS サーバーの仮想ディレクトリへ手動でコピーする必要があります。 Web 同期の構成の詳細については、「[Web 同期の構成](../../relational-databases/replication/configure-web-synchronization.md)」を参照してください。  
  
## 以前のバージョンからレプリケートされたデータベースの復元  
 以前のバージョンからレプリケートされたデータベースのバックアップを復元するときにレプリケーション設定が保持されるようにするには、バックアップが作成されたサーバーおよびデータベースと同じ名前のサーバーおよびデータベースに復元します。  
  
## 参照  
 [管理 &#40;レプリケーション&#41;](../../relational-databases/replication/administration/administration-replication.md)   
 [レプリケーションの旧バージョンとの互換性](../../relational-databases/replication/replication-backward-compatibility.md)   
 [新機能 &#40;レプリケーション&#41;](../../relational-databases/replication/what-s-new-replication.md)   
 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [SQL Server 2016 へのアップグレード](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  