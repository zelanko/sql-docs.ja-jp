---
title: "[パブリケーションのプロパティ], [データ パーティション] | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.datapartitions.f1"
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# [パブリケーションのプロパティ], [データ パーティション]
   **データ パーティション** のページ、 **パブリケーションのプロパティ** ] ダイアログ ボックスでは、パラメーター化されたフィルターを使用するマージ パブリケーションのデータ パーティションを定義することができます。 これらのパーティションを定義した後で、パーティションのスナップショットを生成して、サブスクライバーの接続プロパティ (ログイン名やコンピューター名) に基づいて複数のサブスクライバーの初期データセットを提供することができます。 また、サブスクライバーが最初に同期するときにパーティション用のスナップショットがない場合に、スナップショットの配布および生成をサブスクライバーが要求できるように設定することもできます。 詳しくは、「 [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。  
  
## オプション  
 **[追加]**  
 クリックして **追加** 区分を定義します。  **データ パーティションの追加** ] ダイアログ ボックスの値を指定 **HOST_NAME()** や **SUSER_SNAME()**, 、し、スナップショットを更新するスケジュールを定義します。  
  
 **[編集]**  
 グリッドで、既存のパーティションを選択し、をクリックして **編集** パーティションを編集します。  
  
 **Del**  
 グリッドで、既存のパーティションを選択し、クリックして **削除** パーティションを削除します。  
  
 **[今すぐ選択したスナップショットを生成する]**  
 グリッドで、1 つまたは複数のパーティションを選択し、クリックして **今すぐ選択したスナップショットを生成する** をこれらのパーティションのスナップショットを生成します。  
  
 **[既存のスナップショットをクリーンアップする]**  
 グリッドで、1 つまたは複数のパーティションを選択し、クリックして **既存のスナップショットをクリーンアップする** これらのパーティションのスナップショットをクリーンアップします。  
  
 **[新規サブスクライバーで同期を行うとき、パーティションを自動的に定義し、必要に応じてスナップショットを生成する]**  
 スナップショットの生成および適用をサブスクライバーで要求できるようにする場合は、このオプションを選択します。 サブスクライバーが最初に同期するときに、パーティションに使用できるスナップショットを持っていない場合は、このオプションの選択が必要になることがあります。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [パラメーター化された行フィルター](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  