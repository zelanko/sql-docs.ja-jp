---
title: 'タスク 2: テストと一致するポリシーの発行 |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: e1ffb6d7-fbc5-4695-b538-cc2302d1a17d
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0e6f8fbd3ffbfcee4db212a22d4aef223450e41c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174462"
---
# <a name="task-2-testing-and-publishing-the-matching-policy"></a>タスク 2: 照合ポリシーをテストおよびパブリッシュする
  このタスクでは、テスト、発行、 **Remove Duplicate Suppliers**照合ポリシー。  
  
1.  **照合結果**] ページで [**開始**全体のポリシーをテストします。 この場合は、ポリシーに存在するルールが 1 つだけであるため、ルールとポリシーのテスト結果が同じになります。  
  
2.  リスト ボックスのすべての一致レコードと照合スコアを確認します。 持つレコードを**緑**関連付けられているアイコンはその前にあるピボット レコードと重複しています。 いくつかの例を次に示します。  
  
    1.  レコードを**レコード ID: 1000005**のレコードを一致**レコード Id: 1000004**で**スコア: 100%** 両方のレコードがに同じ値を持つため、**SupplierID (前提条件)**、 **Supplier Name**、および**ContactEmailAddress 列**します。 DQS はクラスターのピボット レコードとしてレコードをランダムに選択します。  
  
    2.  レコード**1000023**一致するレコードの**1000022**と照合スコア: 93% であるため、2 つのレコードが同じ値を持つこと**SupplierID (前提条件)** と**Supplier Name** 、列の値が異なる、 **ContactEmailAddress**列。  
  
    3.  2 つのレコードとレコード Id を表示するリストの一番下までスクロール: **1000051**と**1000052**します。 レコード**1000052**照合スコアとの一致と見なされます**91%** 2 つのレコードの同じ値があるため、 **SupplierID**と**ContactEmailAddress** 、列の値が異なる、 **Supplier Name**列。  
  
     ![ポリシー定義 - ポリシーの結果](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-01.jpg "ポリシー定義 - ポリシーの結果")  
  
3.  任意の一致するレコード (緑色のアイコン) を右クリックし、をクリックして**詳細を表示する**各フィールドのスコアを照合スコア全体に与える影響などの照合に関する詳細情報を確認します。  
  
     ![照合スコアの詳細 ダイアログ ボックス](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-02.jpg "照合スコアの詳細 ダイアログ ボックス")  
  
4.  クリックして**閉じます**を閉じる、**照合スコアの詳細** ダイアログ ボックス。  
  
5.  クリックして**照合結果**ページの下部にあるタブ。 このタブには、一致レコードの数、不一致レコードの数、一致レコードを持つクラスターの数、平均クラスター サイズ、最小クラスター サイズ、最大クラスター サイズなどの詳細が示されます。 参照してください[照合ポリシーの作成](http://msdn.microsoft.com/library/hh270290.aspx)の詳細。 このアクティビティの結果をエクスポートすることはできません。 サンプル データに対してルールおよびポリシーをテストするためにサンプル データを使用することで、照合ポリシーを定義するだけです。  
  
     ![[結果] タブに一致する](../../2014/tutorials/media/et-testingandpublishingthematchingpolicy-03.jpg "照合結果 タブ")  
  
6.  をクリックして**完了**照合ポリシーの作成を完了します。  
  
    > [!NOTE]  
    >  ここでは、照合ポリシーを定義しました。したがって、結果を出力ファイルにエクスポートすることはできません。 基本的には、ポリシーを定義する目的でサンプル入力ファイルを使用し、ルールを作成し、サンプル データに対してルールおよびポリシーをテストしました。  
  
7.  SQL Server Data Quality Services ダイアログ ボックスで、**発行** をクリック**OK**メッセージ ボックス。 定義した照合ポリシーを公開するようになりました、 **Suppliers**ナレッジ ベース。 このナレッジ ベースを使用して、入力ファイルに対して照合プロセスを実行し、重複を特定および削除できます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3: 照合するデータ品質プロジェクトを作成および実行する](../../2014/tutorials/task-3-creating-and-running-a-data-quality-project-for-matching.md)  
  
  
