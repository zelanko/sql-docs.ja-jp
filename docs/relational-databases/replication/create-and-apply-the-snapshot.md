---
title: "スナップショットの作成および適用 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], applying
- snapshots [SQL Server replication], creating
ms.assetid: 631f48bf-50c9-4015-b9d8-8f1ad92d1ee2
caps.latest.revision: "38"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4834625127d034e228416aa5ba0f25f9314b3734
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-and-apply-the-snapshot"></a>スナップショットの作成および適用
  スナップショットは、パブリケーションの作成後に、スナップショット エージェントによって生成されます。 スナップショットは、以下の方法で生成できます。  
  
-   すぐに生成。 既定では、マージ パブリケーションのスナップショットは、パブリケーションの新規作成ウィザードでパブリケーションが作成された後、すぐに生成されます。  
  
-   スケジュールで設定した時刻に生成。 スケジュールは、パブリケーションの新規作成ウィザードの **[スナップショット エージェント]** ページで指定するか、ストアド プロシージャまたはレプリケーション管理オブジェクト (RMO) の使用時に指定します。  
  
-   手動で作成。 コマンド プロンプトまたは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]からスナップショット エージェントを実行します。 エージェントの実行の詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)」および「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。  
  
 マージ レプリケーションの場合は、スナップショット エージェントが起動するたびにスナップショットが生成されます。 トランザクション レプリケーションでは、スナップショットの生成はパブリケーション プロパティ **immediate_sync**の設定で決まります。 プロパティが TRUE に設定されていると (パブリケーションの新規作成ウィザードを使用する際の既定の設定)、スナップショット エージェントを実行するたびにスナップショットが生成され、いつでもスナップショットをサブスクライバーに適用できます。 プロパティが FALSE に設定されていると ( **sp_addpublication**を使用する場合の既定の設定)、最後にスナップショット エージェントを実行してから新しいサブスクリプションが追加された場合にのみスナップショットが生成されます。サブスクライバーは、スナップショット エージェントが完了するまで同期することはできません。  
  
 既定では、スナップショットが生成されると、そのスナップショットはディストリビューター上の既定のスナップショット フォルダーに保存されます。 スナップショット ファイルは、リムーバブル ディスク、CD-ROM などのリムーバブル メディアや、既定のスナップショット フォルダー以外の場所に保存することもできます。 また、格納および転送しやすいようにファイルを圧縮することや、サブスクライバーでスナップショットを適用する前または後にスクリプトを実行することもできます。 これらのオプションの詳細については、「 [Snapshot Options](../../relational-databases/replication/snapshot-options.md)」をご覧ください。  
  
 パラメーター化されたフィルターを使用するマージ パブリケーションに対するスナップショットの場合は、2 段階の処理でスナップショットが作成されます。 まず、パブリッシュされたオブジェクトのレプリケーション スクリプトとスキーマが含まれるスキーマ スナップショットが作成されます。ただしデータは含まれません。 次に、スキーマ スナップショットからコピーしたスクリプトとスキーマが含まれるスナップショットと、サブスクリプションのパーティションに属するデータを使用して、各サブスクリプションが初期化されます。 詳細については、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」を参照してください。  
  
 パブリッシャーで作成され、既定の位置または代替位置に格納されたスナップショットは、サブスクライバーに転送して適用することができます。 ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) によって、最初の同期時に、サブスクライバー側のサブスクリプション データベースにスナップショットが転送され、スキーマ ファイルとデータ ファイルが適用されます。 サブスクリプションの新規作成ウィザードを使用する場合、既定では、サブスクリプションの作成後すぐに最初の同期が行われます。 この動作は、ウィザードの **[サブスクリプションの初期化]** ページの **[次の場合に初期化]** オプションによって制御されます。 サブスクリプションの初期化後に生成されたスナップショットは、サブスクリプションに再初期化のマークが付けられない限り、サブスクライバーに適用されません。 詳細については、「 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)」を参照してください。  
  
 ディストリビューション エージェントまたはマージ エージェントによる初期スナップショットの適用後、それらのエージェントによって以後の更新とその他のデータ変更が反映されます。 スナップショットがディストリビュートされサブスクライバーに適用されるときは、初期スナップショットまたは新しいスナップショットを待機しているサブスクライバーのみが影響を受けます。 そのパブリケーションへの他のサブスクライバー (パブリッシュされたデータへの挿入、更新、削除、またはその他の変更を既に受信中のサブスクライバー) は影響を受けません。  
  
 初期スナップショットを作成および適用するには、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
 スナップショット フォルダーの既定の場所を表示または変更するには、「  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [既定のスナップショットの場所の指定 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)  
  
-   レプリケーション プログラミングおよび RMO プログラミング: [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)  
  
  
