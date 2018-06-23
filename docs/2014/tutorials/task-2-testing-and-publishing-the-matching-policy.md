---
title: '作業 2: テストと一致するポリシーを公開 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8f67535e5ad4969983b06fcb710c1dfce1d97cb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174286"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a>タスク 2: 照合ポリシーをテストおよびパブリッシュする
  このタスクでテストおよび公開、 **Remove Duplicate Suppliers**照合ポリシーです。  
  
1.  **照合結果**] ページで [**開始**全体のポリシーをテストします。 この場合は、ポリシーに存在するルールが 1 つだけであるため、ルールとポリシーのテスト結果が同じになります。  
  
2.  リスト ボックスのすべての一致レコードと照合スコアを確認します。 レコードが、**緑**それに関連付けられているアイコンは、その前にあるピボット レコードと重複します。 次に例をいくつかを示します。  
  
    1.  レコードを**レコード ID: 1000005**のレコードを一致**レコード Id: 1000004**で**スコア: 100%** 両方のレコード値があるため、同じの**SupplierID (前提条件)**、 **Supplier Name**、および**ContactEmailAddress 列**です。 DQS はクラスターのピボット レコードとしてレコードをランダムに選択します。  
  
    2.  レコード**1000023**レコードの照合は、 **1000022**と照合スコア: 93% が 2 つのレコードの値が同一**SupplierID (前提条件)** と**Supplier Name** 、列の値が異なる、 **ContactEmailAddress**列です。  
  
    3.  レコード Id を持つ 2 つのレコードを表示するリストの一番下までスクロールします。 **1000051**と**1000052**です。 レコード**1000052**照合スコアとも一致と見なされます**91%** 2 つのレコードの値が同じであるため、 **SupplierID**と**ContactEmailAddress** 、列の値が異なる、 **Supplier Name**列です。  
  
     ![ポリシーの定義 - ポリシーの結果](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "ポリシーの定義 - ポリシーの結果")  
  
3.  (緑色のアイコン) の一致レコードを右クリックし、をクリックして**詳細を表示する**各フィールドのスコアの照合スコア全体に与える影響などの照合に関する詳細を表示します。  
  
     ![ダイアログ ボックスの詳細を照合スコア](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "照合スコアの詳細 ダイアログ ボックス")  
  
4.  をクリックして**閉じる**を閉じる、**照合スコアの詳細** ダイアログ ボックス。  
  
5.  をクリックして**照合結果**ページの下部にあるタブ。 このタブには、一致レコードの数、不一致レコードの数、一致レコードを持つクラスターの数、平均クラスター サイズ、最小クラスター サイズ、最大クラスター サイズなどの詳細が示されます。 参照してください[照合ポリシーの作成](http://msdn.microsoft.com/library/hh270290.aspx)詳細についてはします。 このアクティビティの結果をエクスポートすることはできません。 サンプル データに対してルールおよびポリシーをテストするためにサンプル データを使用することで、照合ポリシーを定義するだけです。  
  
     ![[結果] タブに一致する](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "照合結果 タブ")  
  
6.  をクリックして**完了**照合ポリシーの作成を完了します。  
  
    > [!NOTE]  
    >  ここでは、照合ポリシーを定義しました。したがって、結果を出力ファイルにエクスポートすることはできません。 基本的には、ポリシーを定義する目的でサンプル入力ファイルを使用し、ルールを作成し、サンプル データに対してルールおよびポリシーをテストしました。  
  
7.  SQL Server Data Quality Services ダイアログ ボックスで、**発行** をクリック**OK**メッセージ ボックスにします。 定義した照合ポリシーを公開するようになりました、 **Suppliers**サポート技術情報。 このナレッジ ベースを使用して、入力ファイルに対して照合プロセスを実行し、重複を特定および削除できます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3: 照合するデータ品質プロジェクトを作成および実行する](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  