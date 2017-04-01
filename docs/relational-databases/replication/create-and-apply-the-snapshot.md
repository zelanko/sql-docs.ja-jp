---
title: "スナップショットの作成および適用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スナップショット [SQL Server レプリケーション], 適用"
  - "スナップショット [SQL Server レプリケーション]、作成"
ms.assetid: 631f48bf-50c9-4015-b9d8-8f1ad92d1ee2
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# スナップショットの作成および適用
  スナップショットは、パブリケーションの作成後に、スナップショット エージェントによって生成されます。 スナップショットは、以下の方法で生成できます。  
  
-   すぐに生成。 既定では、マージ パブリケーションのスナップショットは、パブリケーションの新規作成ウィザードでパブリケーションが作成された後、すぐに生成されます。  
  
-   スケジュールで設定した時刻に生成。 上のスケジュールを指定する、 **スナップショット エージェント** を使用する場合またはパブリケーションの新規作成ウィザードのページでは、ストアド プロシージャまたはレプリケーション管理オブジェクト (RMO)。  
  
-   手動で作成。 コマンド プロンプトまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] からスナップショット エージェントを実行します。 エージェントの実行の詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) と [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
 マージ レプリケーションの場合は、スナップショット エージェントが起動するたびにスナップショットが生成されます。 トランザクション レプリケーションでは、スナップショットの生成がパブリケーションのプロパティの設定に依存 **immediate_sync**です。 プロパティが TRUE に設定されていると (パブリケーションの新規作成ウィザードを使用する際の既定の設定)、スナップショット エージェントを実行するたびにスナップショットが生成され、いつでもスナップショットをサブスクライバーに適用できます。 プロパティが FALSE に設定されている場合 (既定値を使用する場合 **sp_addpublication**)、最後のスナップショット エージェントを実行します以降、新しいサブスクリプションが追加された場合にのみ、スナップショットを生成。サブスクライバーは、スナップショット エージェントを同期する前に、完了を待つ必要があります。  
  
 既定では、スナップショットが生成されると、そのスナップショットはディストリビューター上の既定のスナップショット フォルダーに保存されます。 スナップショット ファイルは、リムーバブル ディスク、CD-ROM などのリムーバブル メディアや、既定のスナップショット フォルダー以外の場所に保存することもできます。 また、格納および転送しやすいようにファイルを圧縮することや、サブスクライバーでスナップショットを適用する前または後にスクリプトを実行することもできます。 これらのオプションの詳細については、次を参照してください。 [スナップショット オプション](../../relational-databases/replication/snapshot-options.md)します。  
  
 パラメーター化されたフィルターを使用するマージ パブリケーションに対するスナップショットの場合は、2 段階の処理でスナップショットが作成されます。 まず、パブリッシュされたオブジェクトのレプリケーション スクリプトとスキーマが含まれるスキーマ スナップショットが作成されます。ただしデータは含まれません。 次に、スキーマ スナップショットからコピーしたスクリプトとスキーマが含まれるスナップショットと、サブスクリプションのパーティションに属するデータを使用して、各サブスクリプションが初期化されます。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
 パブリッシャーで作成され、既定の位置または代替位置に格納されたスナップショットは、サブスクライバーに転送して適用することができます。 ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) によって、最初の同期時に、サブスクライバー側のサブスクリプション データベースにスナップショットが転送され、スキーマ ファイルとデータ ファイルが適用されます。 サブスクリプションの新規作成ウィザードを使用する場合、既定では、サブスクリプションの作成後すぐに最初の同期が行われます。 この動作によって制御、 **場合に初期化** ] オプションを選択、 **サブスクリプションの初期化** ウィザードのページです。 サブスクリプションの初期化後に生成されたスナップショットは、サブスクリプションに再初期化のマークが付けられない限り、サブスクライバーに適用されません。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
 ディストリビューション エージェントまたはマージ エージェントによる初期スナップショットの適用後、それらのエージェントによって以後の更新とその他のデータ変更が反映されます。 スナップショットがディストリビュートされサブスクライバーに適用されるときは、初期スナップショットまたは新しいスナップショットを待機しているサブスクライバーのみが影響を受けます。 そのパブリケーションへの他のサブスクライバー (パブリッシュされたデータへの挿入、更新、削除、またはその他の変更を既に受信中のサブスクライバー) は影響を受けません。  
  
 作成し、初期スナップショットを適用 [を作成し、初期スナップショットを適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)します。  
  
 スナップショット フォルダーの既定の場所を表示または変更するには、「  
  
-   [!含める [ssManStudioFull] (../Token/ssManStudioFull_md.md)]: [Specify the Default Snapshot Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)  
  
-   レプリケーション プログラミングおよび RMO プログラミング: [パブリッシングとディストリビューション](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
## 参照  
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)   
 [sp_addpublication & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)  
  
  