---
title: '[列マッピングの指定] ダイアログボックス (マイニング精度チャート) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4416a51ea32500d56c209d745065da20bf8010c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068419"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a>[列マッピングの指定] ダイアログ ボックス (マイニング精度チャート)
  
  **[列マッピングの指定]** タブを使用して、外部データ ソースからテーブルを選択し、列をデータ マイニング モデルにマッピングします。 次に外部データを使用してマイニング モデルの精度をテストして、その結果を精度チャートに表示します。  
  
 **詳細については、「** [データマイニング&#41;&#40;テストおよび検証](data-mining/testing-and-validation-data-mining.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[マイニング構造]**  
 テストする対象モデルを含む、選択されたマイニング構造を表示します。  
  
 **[構造の選択]**  
 クリックして **[マイニング構造の選択]** ダイアログ ボックスを開き、別のマイニング構造を選択します。  
  
 **[入力テーブルの選択]**  
 リフト チャートの生成に使用するために選択された入力テーブルを表示します。 モデルの精度のテストに使用するテスト データが含まれたテーブルを選択します。  
  
> [!NOTE]  
>  ペインにテーブルが表示されない場合は、 **[ケース テーブルの選択]** をクリックし、データ ソース ビューからテーブルを追加します。  
  
 **[テーブルの削除]**  
 選択されているテーブルを削除します。 テーブルが選択されていないとき、または **[入力テーブルの選択]** ボックスの一覧にテーブルが表示されていないとき、このボタンは無効になります。  
  
 **[ケース テーブルの選択]**  
 クリックして **[テーブルの選択]** ダイアログ ボックスを開き、データ ソース ビューを選択します。  
  
 **メモ**このボタンは、ケーステーブルが選択されていない場合にのみ表示されます。 別のケース テーブルを選択できるようにこのボタンを有効にするには、すべての既存のテーブルを選択し、 **[テーブルの削除]** をクリックして、一覧を消去します。  
  
 **[入れ子になったテーブルの選択]**  
 
  **[テーブルの選択]** ダイアログ ボックスを開きます。 このボタンは、ケース テーブルが選択されている場合にのみ表示されます。 関連付けられているマイニング構造に入れ子になったテーブルが含まれていない場合、このボタンは無効になります。  
  
 **[結合の変更]**  
 
  **[入れ子になった結合の指定]** ダイアログ ボックスを開きます。 このボタンは、入れ子になったテーブルが選択されている場合にのみアクティブになります。  
  
## <a name="see-also"></a>参照  
 [テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [マイニング精度チャートデザイナー &#40;データマイニング&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
