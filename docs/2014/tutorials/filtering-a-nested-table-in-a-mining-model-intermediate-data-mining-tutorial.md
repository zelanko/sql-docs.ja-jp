---
title: マイニング モデル (中級者向けデータ マイニング チュートリアル) で入れ子になったテーブルをフィルター処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9b11971c6e6005c7e1d65a1728e8b8aac818b41c
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312320"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a>マイニング モデルでの入れ子になったテーブルのフィルター処理 (中級者向けデータ マイニング チュートリアル)
  モデルの作成と検証が完了したら、顧客データのサブセットに焦点を絞ります。 たとえば、特定の品目が入っているバスケットのみを分析したり、一定期間に何も購入しなかった顧客の人口統計を分析したりすることができます。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を使用すると、マイニング モデルで使用されるデータをフィルター処理できます。 別のデータを使用する新しいデータ ソース ビューを設定する必要がないために、この機能の使用をお勧めします。 「基本的なデータ マイニング チュートリアル」では、ケース テーブルに条件を適用することでフラット テーブルのデータをフィルター処理する方法について学習しました。 ここでは、入れ子になったテーブルに適用するフィルターを作成します。  
  
## <a name="filters-on-nested-vs-case-tables"></a>入れ子になったテーブルとケース テーブルでのフィルターの違い  
 データ ソース ビューにケース テーブルと入れ子になったテーブルが含まれている場合は、アソシエーション モデルで使用されているデータ ソース ビューと同様に、ケース テーブルの値、入れ子になったテーブルでの値の有無、または両方の組み合わせをフィルター処理できます。  
  
 ここでは、まずアソシエーション モデルのコピーを作成し、関連する新しいモデルに IncomeGroup 属性と Region 属性を追加して、ケース テーブルでこれらの属性をフィルター処理できるようにします。  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a>アソシエーション モデルのコピーを作成して変更するには  
  
1.  **マイニング モデル**のタブ[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を右クリックし、`Association`モデル、および選択**新しいマイニング モデル**です。  
  
2.  **モデル名**、型`Association Filtered`です。 **アルゴリズム名** **Microsoft アソシエーション ルール**です。 **[OK]** をクリックします。  
  
3.  [Association Filtered モデルの列で、[IncomeGroup] 行] をクリックし、値から変更**無視**に**入力**です。  
  
 次に、新しいアソシエーション モデルでケース テーブルに対してフィルターを作成します。 このフィルターでは、対象の地域または収入レベルの顧客のみがモデルに渡されます。 さらに、買い物かごに 1 つ以上の品目が入っていた顧客のみがモデルで使用されるように指定する 2 番目のフィルター条件を追加します。  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a>マイニング モデルにフィルターを追加するには  
  
1.  **マイニング モデル**] タブで、Association Filtered、モデルを右クリックし、選択 **[モデル フィルターの**します。  
  
2.  **[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。  
  
3.  **マイニング構造列**テキスト ボックスで、IncomeGroup です。  
  
     テキスト ボックスの左側のアイコンが変化して、選択されたアイテムが列であることが示されます。  
  
4.  クリックして、**演算子**テキスト ボックスと選択、 **=** 一覧から演算子。  
  
5.  クリックして、**値**テキスト ボックス、および種類`High`ボックス。  
  
6.  グリッドの次の行をクリックします。  
  
7.  クリックして、**や**クリックし、グリッドの次の行のテキスト ボックス**または**です。  
  
8.  **マイニング構造列**テキスト ボックスで、IncomeGroup です。 **値**テキスト ボックスで、「`Moderate`です。  
  
     作成したフィルター条件が自動的に追加、**式**テキスト ボックスで、し、次のように表示する必要があります。  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. 演算子として、既定のままにしてグリッドの次の行をクリックして**AND**です。  
  
10. **演算子**、既定値をそのまま**Contains**です。 クリックして、**値**テキスト ボックス。  
  
11. **フィルター**ダイアログ ボックスの下の最初の行で**マイニング構造列**`Model`です。  
  
12. **演算子** **IS NOT NULL**です。 ままにして、**値**ボックスは空白です。 **[OK]** をクリックします。  
  
     フィルター条件、**式**のテキスト ボックス、**モデル フィルター**  ダイアログ ボックスが自動的に更新され、入れ子になったテーブルに新しい条件が含まれます。 完成した式は次のようになります。  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a>ドリルスルーを有効にして、フィルター選択されたモデルを処理するには  
  
1.  **マイニング モデル** タブで、右クリックし、`Association Filtered`モデル、および選択**プロパティ**です。  
  
2.  変更、 **AllowDrillThrough**プロパティを**True**です。  
  
3.  右クリックし、`Association Filtered`マイニング モデル、および選択**プロセス モデル**です。  
  
4.  をクリックして**はい**に新しいモデルを配置するエラー メッセージに、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。  
  
5.  **マイニング構造の処理**ダイアログ ボックスで、をクリックして**実行**です。  
  
6.  処理が完了したらクリックして**閉じる**を終了する、**処理の進行状況** ダイアログ ボックスをクリック**閉じる**を終了するには、もう一度、**マイニング構造の処理**  ダイアログ ボックス。  
  
 Microsoft 汎用コンテンツ ツリー ビューアーで NODE_SUPPORT の値を参照すると、フィルター選択されたモデルに含まれているケースの数が元のモデルよりも少ないことを確認できます。  
  
## <a name="remarks"></a>コメント  
 ここで作成した入れ子になったテーブルのフィルターでは、そのテーブルに少なくとも 1 つの行があるかどうかのみがチェックされますが、特定の製品の有無を確認するフィルター条件を作成することもできます。  たとえば、次のようなフィルターを作成できます。  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 このステートメントでは、ケース テーブルの顧客を水筒 (water bottle) の購入者のみに制限しています。 ただし、入れ子になったテーブルの属性数には制限がないため、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では選択できる値の一覧が表示されません。 代わりに、値を正確に入力する必要があります。  
  
 クリックして**クエリの編集**フィルター式を手動で変更します。 ただし、フィルター式の一部を手動で変更すると、グリッドが無効になり、その後はテキスト編集モードのみでフィルター式を操作する必要があります。 グリッド編集モードに戻すには、フィルター式を消去して最初からやり直す必要があります。  
  
> [!WARNING]  
>  入れ子になったテーブル フィルターで LIKE 演算子を使用することはできません。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [アソシエーションを予測する&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [モデル フィルターの構文と例&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [マイニング モデル フィルターの&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  