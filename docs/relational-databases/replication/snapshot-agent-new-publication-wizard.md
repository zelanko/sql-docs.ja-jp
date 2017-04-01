---
title: "[スナップショット エージェント] (パブリケーションの新規作成ウィザード) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.configuresnapshotagent.f1"
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# [スナップショット エージェント] (パブリケーションの新規作成ウィザード)
  [スナップショット エージェント] では、新しいサブスクリプションの初期化に使用されるパブリケーション スキーマおよびデータを含んでいるファイルを作成します。 既定では、スナップショット エージェントは、パブリケーションの新規作成ウィザードでパブリケーションが作成されるとすぐに実行されます。 続いて、エージェントが指定したスケジュールに従って実行されます。 エージェントが実行されるたびに新しいスナップショット ファイルが作成されるかどうかは、選択したレプリケーションおよびオプションの種類によって異なります。 詳細については、次を参照してください。 [を作成し、スナップショットの適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)します。  
  
 パラメーター化されたフィルターを使用するマージ パブリケーションでは、パブリケーション スナップショットの完了後、データの各パーティションのスナップショットを作成する必要があります。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
## オプション  
 **スナップショットをすぐに作成** (マージ レプリケーション) または **スナップショットをすぐに作成し、サブスクリプションの初期化に使用可能なスナップショットを保持する** (トランザクション レプリケーション)  
 パブリケーションの新規作成ウィザードが完了した後、すぐにスナップショットを作成する場合は、このチェック ボックスを選択します。 スナップショットのプロパティを変更する予定の場合は、このチェック ボックスをオフ、 **パブリケーションのプロパティ** 、スナップショットを生成する前にダイアログ ボックスまたはスナップショットを使用せず、サブスクライバーが初期化されます。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントの適切なジョブを開始するために、ウィザードによりディストリビューターへの接続が要求される場合があります。  
  
 **[以下のスケジュールでスナップショット エージェントを実行する]**  
 スナップショット エージェントを実行するための既定のスケジュールを受け入れるかをクリックして **変更** スケジュールを指定します。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  