---
title: "サブスクリプションの再初期化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サブスクリプションの初期化 [SQL Server レプリケーション]、再初期化"
  - "サブスクリプション [SQL Server レプリケーション]、再初期化"
  - "サブスクリプションの再初期化"
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# サブスクリプションの再初期化
  サブスクリプションの再初期化では、1 つ以上のサブスクライバーに 1 つ以上のアーティクルの新しいスナップショットが適用されます。トランザクション レプリケーションとスナップショット レプリケーションでは個々のアーティクルを再初期化できますが、マージ レプリケーションではすべてのアーティクルを再初期化する必要があります。 ピア ツー ピア トランザクション レプリケーション トポロジのノードは再初期化できません。 ノードが新しいデータのコピーを確実に保持する必要がある場合は、そのノードでバックアップを復元してください。 再初期化は、以下の 2 つの場合に行われます。  
  
-   サブスクリプションを再初期化するように明示的にマークした場合。  
  
-   プロパティの変更など、再初期化を必要とする操作を実行した場合。 再初期化を必要とする処理の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
 いずれの場合も、ディストリビューション エージェントまたはマージ エージェントが次に実行されたときに、最新のスナップショットがサブスクライバーに適用されます。 スナップショット レプリケーションとトランザクション レプリケーションの場合は、再初期化が行われると、サブスクライバーで行われた変更 (まだパブリッシャーと同期されていない変更) は新しいスナップショットの適用によって上書きされます。  
  
 マージ レプリケーションの場合は、スナップショットを適用する前にすべてのデータ変更をサブスクライバーからアップロードするように選択することができます。 スナップショットが再適用される前に、パブリッシャーの保留中のスキーマ変更がサブスクライバーに適用され、前回の同期以降にサブスクライバーで行われた更新がパブリッシャーに反映されます。 この動作によって制御、 **upload_first** と **automatic_reinitialization_policy** プロパティです。 詳細については、次を参照してください。 [サブスクリプションを再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)します。 オプションを指定できますが、サブスクリプションの SQL Server Management Studio またはレプリケーション モニターを使用して再初期化のマークを付けた場合、 **サブスクリプションの再初期化** ] ダイアログ ボックスの最初の変更をアップロードします。  
  
> [!IMPORTANT]  
>  マージ パブリケーションのパラメーター化されたフィルターを追加、削除、変更する場合は、再初期化の際にサブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
 サブスクリプションを作成するとき、初期スナップショットをサブスクライバーに適用しないように指定した場合、作成されたサブスクリプションを再初期化するようにマークしても、スナップショットは適用されません。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
 **サブスクリプションを再初期化するには**  
  
 サブスクリプションのすべてのアーティクルを再初期化するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、ストアド プロシージャ、またはレプリケーション管理オブジェクト (RMO) を使用します。 スナップショット パブリケーションおよびトランザクション パブリケーションの個々のアーティクルを再初期化するには、ストアド プロシージャを使用する必要があります。 詳細については、次を参照してください。 [サブスクリプションを再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)します。  
  
## 参照  
 [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)   
 [サブスクリプションの有効期限と非アクティブ化](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  