---
title: 'タスク 1: 照合ポリシーの定義 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0b0ccf6217899b5368cf27f93951e0a7ddc0cf48
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083554"
---
# <a name="task-1-defining-a-matching-policy"></a>タスク 1: 照合ポリシーを定義する
  ここでは、1 つのルールを持つ照合ポリシーを作成します。 ルールでは、: **Supplier ID**、つまり、ルール内の他のドメインを使用する前に Supplier Id が一致する必要があることです。 このルールではその他の 2 つのドメイン: **Supplier Name**で**類似性**値に設定**70%** と**Contact Email**で**類似性**値に設定**30%** です。  
  
1.  メイン ページで**DQS クライアント**をクリックして**右矢印** の横に**Suppliers**ナレッジ ベースを選択し**照合ポリシー**です。  
  
     ![[ポリシー]、[メイン メニューに一致するページ](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "照合ポリシー]、[メイン メニュー] ページ")  
  
2.  **マップ**] ページで、[ **Excel ファイル**の**データソース**です。  
  
3.  をクリックして**参照**にそのフィルターが設定されていることを確認**Excel ブック**を選択して**Cleansed Supplier List.xls**クレンジング アクティビティを実行した後にエクスポートしたファイルです。  
  
    > [!NOTE]  
    >  このアクティビティは照合ポリシーの定義を主な目的としています。このため、このアクティビティの最後に結果をエクスポートすることはできません。 次のレッスンでは、照合アクティビティ用のデータ品質プロジェクトを作成し、この照合ポリシーを使用して仕入先の一覧から重複を削除します。  
  
4.  マップ**SupplierID**列**Supplier ID**ドメイン、 **Supplier Name**列**Supplier Name**ドメイン、 **ContactEmailAddress**列**Contact Email**ドメイン。 照合ポリシーの定義で使用するドメインのみにソース列をマップする必要があります。 このレッスンでは、照合ポリシー アクティビティで使用するための Supplier ID、Supplier Name、および Contact Email ドメインを作成します。  
  
     ![照合ポリシーの定義の処理のページをマップ](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "マップの照合ポリシーの定義の処理 ページ")  
  
5.  をクリックして **[次へ]** に移動する、**照合ポリシー**ページの場所を定義して、照合ポリシー ルールを 1 つにします。  
  
6.  をクリックして**照合ルールを作成**ポリシーのルールを作成するには、ツールバーのボタンをクリックします。  
  
     ![照合ルール ツールバー ボタンを作成して](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "照合ルール ツール バー ボタンを作成します。")  
  
7.  **ルールの詳細**、右側のウィンドウの入力**Remove Duplicate Suppliers**の**ルール名**です。  
  
8.  をクリックして**新しいドメイン要素を追加**右側のペインのツールバーでします。  
  
     ![新しいドメイン要素ボタンを追加するルールの詳細 -](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "ルールの詳細 - 新しいドメイン要素ボタンを追加します。")  
  
9. 選択**Supplier ID**の**ドメイン**を選択し、**前提条件となる**チェック ボックスをオンします。 注意して**類似**に自動的に設定されている**Exact**です。 設定して**Supplier ID**として、**前提条件となる**、こと、2 つのレコードには、このフィールドの値が 100% の一致を返す必要があります、それ以外の場合、レコードは考慮されません一致および内の他の句を指定する、規則は無視されます。  
  
     ![重複する仕入先ルールの定義を削除する](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "重複する仕入先ルールの定義を削除します。")  
  
10. をクリックして**新しいドメイン要素を追加**ツールバーをもう一度からです。  
  
11. 選択**Supplier Name**ドメインで、**と似ています**の**類似**、および種類**70**の**重み**.  ここでは、レコードが一致と見なされるためには仕入先名が類似しているだけでよいこと、つまり完全に一致しなくてもよいことを指定しています。 重みは、このフィールドのスコアが照合スコア全体に与える影響を示します。  
  
12. 前の 2 つの手順を繰り返して追加**Contact Email**を持つドメイン**30**の**重み**です。  
  
13. 注意して、**最小照合スコア**に設定されている**80%**、これは、「値、**全般**のタブ、**構成**のページ**DQS 管理**です。 このスコアは、しきい値より大きな値に増やすことだけができます。  
  
14. 注意して**重複するクラスター**オプションを選択します。 このオプションを使用すると、レコードを複数のクラスターに表示できます。 [重複しないクラスター] に設定を変更すると、共通のレコードを持つクラスターが 1 つのクラスターに結合されます。  
  
15. **開始**ボタンこのページを使用するポリシーとは別に、各ルールをテストする一方、次のページで [スタート] ボタンでは、ポリシー全体 (ポリシーのすべてのルール) をテストすることができます。  
  
16. をクリックして**次**に切り替えるには、**照合結果**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 2: 照合ポリシーをテストおよびパブリッシュする](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  