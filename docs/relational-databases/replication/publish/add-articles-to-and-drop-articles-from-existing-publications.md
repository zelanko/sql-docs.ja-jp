---
title: "既存のパブリケーションでのアーティクルの追加および削除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アーティクル [SQL Server レプリケーション]、ドロップ"
  - "アーティクルの削除"
  - "removing articles"
  - "アーティクルのドロップ"
  - "アーティクルの追加"
  - "レプリケーションの管理, アーティクル"
  - "パブリケーション [SQL Server レプリケーション], アーティクルの追加と削除"
  - "アーティクル [SQL Server レプリケーション]、追加"
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# 既存のパブリケーションでのアーティクルの追加および削除
  パブリケーションを作成したら、アーティクルを追加および削除できます。 アーティクルはいつでも追加できますが、アーティクルを削除するために必要な操作は、レプリケーションの種類と、アーティクルを削除するタイミングによって異なります。  
  
## アーティクルの追加  
 アーティクルを追加するには、アーティクルへのパブリケーションの追加、パブリケーションの新しいスナップショットの作成、サブスクリプションの同期による新しいアーティクルのスキーマとデータの適用を行います。  
  
> [!NOTE]  
>  マージ パブリケーションにアーティクルを追加すると、既存のアーティクルは、新しいアーティクルによって異なります。、、を使用して両方のアーティクルの処理順序を指定する必要があります、 **@processing_order** のパラメーター [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) と [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 たとえば、テーブルをパブリッシュし、テーブルが参照している関数はパブリッシュしない場合を考えます。 この関数をパブリッシュしないと、サブスクライバー側でテーブルを作成できないとします。 パブリケーションに関数を追加すると: の値を指定して **1** の **@processing_order** のパラメーター **sp_addmergearticle**; の値を指定 **2** の **@processing_order** のパラメーター **sp_changemergearticle**, 、テーブル名、パラメーターを指定する **@article**します。 この処理順序により、サブスクライバー側で関数に依存するテーブルを作成する前に、関数の作成が求められるようになります。 各アーティクルに使用する値は、関数の値がテーブルの値より小さければ、別の値でもかまいません。  
  
1.  次のいずれかの方法を使用して、1 つ以上のアーティクルを追加します。  
  
    -   [パブリケーションと #40; からの追加およびドロップ記事SQL Server Management Studio と #41 です。](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)  
  
2.  パブリケーションにアーティクルを追加したら、パブリケーションの新しいスナップショット (およびパラメーター化されたフィルターを使用したマージ パブリケーションの場合は、すべてのパーティション) を作成する必要があります。 その後、ディストリビューション エージェントまたはマージ エージェントによって、新しいアーティクルのスキーマおよびデータがサブスクライバーにコピーされます (パブリケーション全体が再初期化されるわけではありません)。  
  
    -   新しいスナップショットを作成するを参照してください。 [を作成し、初期スナップショットを適用](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)します。  
  
    -   パラメーター化されたフィルターには、マージ パブリケーションの新しいスナップショットを作成するを参照してください。 [パラメーター化されたフィルターによるマージ パブリケーションのスナップショットを作成](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)します。  
  
3.  スナップショットを作成したら、サブスクリプションを同期し、新しいアーティクルのスキーマおよびデータをコピーします。  
  
    -   プッシュ サブスクリプションを同期するには、次を参照してください。 [プッシュ サブスクリプションを同期](../../../relational-databases/replication/synchronize-a-push-subscription.md)します。  
  
    -   プル サブスクリプションを同期するには、次を参照してください。 [プル サブスクリプションを同期](../../../relational-databases/replication/synchronize-a-pull-subscription.md)します。  
  
## アーティクルの削除  
 アーティクルはパブリケーションからいつでも削除できます。ただし、次の動作について考慮する必要があります。  
  
-   パブリケーションからアーティクルを削除しても、パブリケーション データベースからオブジェクトが削除されたり、サブスクリプション データベースから対応するオブジェクトが削除されるわけではありません。 ドロップを使用して \< オブジェクト> を必要に応じて、これらのオブジェクトを削除します。 外部キー制約を通じて公開されたその他の記事に関連するアーティクルを削除する場合、手動でまたはオンデマンドでスクリプトの実行を使用して、サブスクライバーでテーブルを削除すること勧め: 適切なドロップを含むスクリプトを指定する \< オブジェクト> ステートメントです。 詳細については、次を参照してください。 [同期中にスクリプトを実行する (&) #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)します。  
  
-   互換性レベル 90RTM 以上のマージ パブリケーションの場合、アーティクルはいつでも削除できますが、新しいスナップショットが必要です。 さらに、次のことを考慮する必要があります。  
  
    -   アーティクルが結合フィルター リレーションシップまたは論理レコード リレーションシップの親アーティクルの場合、最初にリレーションシップの削除が必要ですが、これには再初期化が必要になります。  
  
    -   アーティクルにパブリケーションの最後のパラメーター化されたフィルターが含まれる場合、サブスクリプションを再初期化する必要があります。  
  
-   互換性レベルが 90RTM 未満のマージ パブリケーションの場合、アーティクルは特別な注意をせずに、サブスクリプションの初期同期の前に削除できます。 1 つ以上のサブスクリプションが同期された後にアーティクルが削除された場合、サブスクリプションの削除、再作成、および同期が必要です。  
  
-   スナップショット パブリケーションまたはトランザクション パブリケーションの場合、アーティクルはサブスクリプションを作成する前に、特別な事項を考慮せずに削除できます。 1 つ以上のサブスクリプションが作成された後にアーティクルが削除された場合、サブスクリプションの削除、再作成、および同期が必要です。 サブスクリプションの削除の詳細については、次を参照してください。 [パブリケーションをサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md) と [sp_dropsubscription & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)します。 **sp_dropsubscription** サブスクリプション全体ではなく、サブスクリプションから 1 つのアーティクルを削除することができます。  
  
1.  パブリケーションからアーティクルを削除するには、アーティクルを削除し、パブリケーションの新しいスナップショットを作成します。 アーティクルを削除すると、現在のスナップショットは無効になります。したがって新しいスナップショットを作成する必要があります。  
  
    -   を、パブリケーションからアーティクルを削除するには、を参照してください。 [にアーティクルを追加し、パブリケーション & #40; からアーティクルを削除SQL Server Management Studio と #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md) または [アーティクルを削除](../../../relational-databases/replication/publish/delete-an-article.md)します。  
  
2.  パブリケーションからアーティクルを削除したら、パブリケーションの新しいスナップショット (およびパラメーター化されたフィルターを使用したマージ パブリケーションの場合は、すべてのパーティション) を作成する必要があります。  
  
    -   新しいスナップショットを作成するを参照してください。 [を作成し、初期スナップショットを適用](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)します。  
  
    -   パラメーター化されたフィルターには、マージ パブリケーションの新しいスナップショットを作成するを参照してください。 [パラメーター化されたフィルターによるマージ パブリケーションのスナップショットを作成](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)します。  
  
 前述のように、場合によっては、アーティクルを削除するために、サブスクリプションの削除、再作成、および同期が必要になる場合があります。 詳細については、次を参照してください。 [パブリケーションをサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md) と [データの同期](../../../relational-databases/replication/synchronize-data.md)します。  
  
## 参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)   
 [パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  