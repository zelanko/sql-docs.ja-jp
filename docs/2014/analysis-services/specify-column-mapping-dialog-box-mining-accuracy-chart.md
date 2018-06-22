---
title: 列マッピング ダイアログ ボックス (マイニング精度チャート) の指定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 350b0f55f7ae4d445945905984f3e68a34d5c318
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073327"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a>[列マッピングの指定] ダイアログ ボックス (マイニング精度チャート)
  **[列マッピングの指定]** タブを使用して、外部データ ソースからテーブルを選択し、列をデータ マイニング モデルにマッピングします。 次に外部データを使用してマイニング モデルの精度をテストして、その結果を精度チャートに表示します。  
  
 **詳細情報:** 「[テストおよび検証 &#40;データ マイニング&#41;](data-mining/testing-and-validation-data-mining.md)」  
  
## <a name="options"></a>および  
 **マイニング構造**  
 テストする対象モデルを含む、選択されたマイニング構造を表示します。  
  
 **構造を選択します。**  
 クリックして **[マイニング構造の選択]** ダイアログ ボックスを開き、別のマイニング構造を選択します。  
  
 **入力テーブルを選択します。**  
 リフト チャートの生成に使用するために選択された入力テーブルを表示します。 モデルの精度のテストに使用するテスト データが含まれたテーブルを選択します。  
  
> [!NOTE]  
>  ペインにテーブルが表示されない場合は、 **[ケース テーブルの選択]** をクリックし、データ ソース ビューからテーブルを追加します。  
  
 **テーブルを削除します。**  
 選択されているテーブルを削除します。 テーブルが選択されていないとき、または **[入力テーブルの選択]** ボックスの一覧にテーブルが表示されていないとき、このボタンは無効になります。  
  
 **ケース テーブルを選択します。**  
 クリックして **[テーブルの選択]** ダイアログ ボックスを開き、データ ソース ビューを選択します。  
  
 **注** このボタンは、ケース テーブルが選択されていない場合にのみ表示されます。 別のケース テーブルを選択できるようにこのボタンを有効にするには、すべての既存のテーブルを選択し、 **[テーブルの削除]** をクリックして、一覧を消去します。  
  
 **入れ子になったテーブルを選択します。**  
 **[テーブルの選択]** ダイアログ ボックスを開きます。 このボタンは、ケース テーブルが選択されている場合にのみ表示されます。 関連付けられているマイニング構造に入れ子になったテーブルが含まれていない場合、このボタンは無効になります。  
  
 **結合を変更します。**  
 **[入れ子になった結合の指定]** ダイアログ ボックスを開きます。 このボタンは、入れ子になったテーブルが選択されている場合にのみアクティブになります。  
  
## <a name="see-also"></a>参照  
 [テストと検証タスク、および操作方法&#40;データ マイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [マイニング精度チャート デザイナー&#40;データ マイニング&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  