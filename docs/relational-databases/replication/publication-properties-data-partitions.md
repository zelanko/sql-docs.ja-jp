---
title: "[パブリケーションのプロパティ], [データ パーティション] | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.datapartitions.f1
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 50ef9df48b07e6be66798ac2bd5f33dc57fe6a84
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="publication-properties-data-partitions"></a>[パブリケーションのプロパティ], [データ パーティション]
  **[パブリケーションのプロパティ]** ダイアログ ボックスの **[データ パーティション]** ページを使用すると、パラメーター化されたフィルタリングを使用するマージ パブリケーションのデータ パーティションを定義できます。 これらのパーティションを定義した後で、パーティションのスナップショットを生成して、サブスクライバーの接続プロパティ (ログイン名やコンピューター名) に基づいて複数のサブスクライバーの初期データセットを提供することができます。 また、サブスクライバーが最初に同期するときにパーティション用のスナップショットがない場合に、スナップショットの配布および生成をサブスクライバーが要求できるように設定することもできます。 詳しくは、「 [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **[追加]**  
 パーティションを定義するには **[追加]** をクリックします。 **[データ パーティションの追加]** ダイアログ ボックスで、 **HOST_NAME()** や **SUSER_SNAME()**の値を指定し、スナップショットを更新するスケジュールを定義します。  
  
 **[編集]**  
 パーティションを編集するには、グリッド内の既存のパーティションを選択して **[編集]** をクリックします。  
  
 **Del**  
 パーティションを削除するには、グリッド内の既存のパーティションを選択して **[削除]** をクリックします。  
  
 **[今すぐ選択したスナップショットを生成する]**  
 グリッドのパーティションを 1 つ以上選択して **[今すぐ選択したスナップショットを生成する]** をクリックすると、これらのパーティションのスナップショットが生成されます。  
  
 **[既存のスナップショットをクリーンアップする]**  
 グリッドのパーティションを 1 つ以上選択して **[既存のスナップショットをクリーンアップする]** をクリックすると、これらのパーティションのスナップショットがクリーンアップされます。  
  
 **[新規サブスクライバーで同期を行うとき、パーティションを自動的に定義し、必要に応じてスナップショットを生成する]**  
 スナップショットの生成および適用をサブスクライバーで要求できるようにする場合は、このオプションを選択します。 サブスクライバーが最初に同期するときに、パーティションに使用できるスナップショットを持っていない場合は、このオプションの選択が必要になることがあります。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
