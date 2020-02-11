---
title: マイニングモデルでの入れ子になったテーブルのフィルター処理 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f57d691587d658e968cd79cf4f4ab4731db29915
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63267477"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a>マイニング モデルでの入れ子になったテーブルのフィルター処理 (中級者向けデータ マイニング チュートリアル)
  モデルの作成と検証が完了したら、顧客データのサブセットに焦点を絞ります。 たとえば、特定の品目が入っているバスケットのみを分析したり、一定期間に何も購入しなかった顧客の人口統計を分析したりすることができます。  
  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を使用すると、マイニング モデルで使用されるデータをフィルター処理できます。 この機能は、別のデータを使用するために新しいデータソースビューを設定する必要がないため、便利です。 「基本的なデータ マイニング チュートリアル」では、ケース テーブルに条件を適用することでフラット テーブルのデータをフィルター処理する方法について学習しました。 ここでは、入れ子になったテーブルに適用するフィルターを作成します。  
  
## <a name="filters-on-nested-vs-case-tables"></a>入れ子になったテーブルとケース テーブルでのフィルターの違い  
 データ ソース ビューにケース テーブルと入れ子になったテーブルが含まれている場合は、アソシエーション モデルで使用されているデータ ソース ビューと同様に、ケース テーブルの値、入れ子になったテーブルでの値の有無、または両方の組み合わせをフィルター処理できます。  
  
 ここでは、まずアソシエーション モデルのコピーを作成し、関連する新しいモデルに IncomeGroup 属性と Region 属性を追加して、ケース テーブルでこれらの属性をフィルター処理できるようにします。  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a>アソシエーション モデルのコピーを作成して変更するには  
  
1.  の[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] `Association` [**マイニングモデル**] タブで、モデルを右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
2.  [**モデル名**] に`Association Filtered`「」と入力します。 [**アルゴリズム名**] で、[ **Microsoft アソシエーションルール**] を選択します。 **[OK]** をクリックします。  
  
3.  アソシエーションのフィルター選択されたモデルの列で、IncomeGroup 行をクリックし、値を**Ignore**から**Input**に変更します。  
  
 次に、新しいアソシエーション モデルでケース テーブルに対してフィルターを作成します。 このフィルターでは、対象の地域または収入レベルの顧客のみがモデルに渡されます。 さらに、買い物かごに 1 つ以上の品目が入っていた顧客のみがモデルで使用されるように指定する 2 番目のフィルター条件を追加します。  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a>マイニング モデルにフィルターを追加するには  
  
1.  [**マイニングモデル**] タブで、フィルター処理されたモデルの関連付けを右クリックし、[**モデルフィルターの設定**] をクリックします。  
  
2.  
  **[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。  
  
3.  [**マイニング構造列**] ボックスで、[IncomeGroup] を選択します。  
  
     テキスト ボックスの左側のアイコンが変化して、選択されたアイテムが列であることが示されます。  
  
4.  [**演算子**] ボックスをクリックし、 **=** 一覧から演算子を選択します。  
  
5.  [**値**] テキストボックスをクリックし`High` 、ボックスに「」と入力します。  
  
6.  グリッドの次の行をクリックします。  
  
7.  グリッドの次の行の [ **AND** ] テキストボックスをクリックし、[ **or**] を選択します。  
  
8.  [**マイニング構造列**] ボックスで、[IncomeGroup] を選択します。 [**値**] テキストボックスに「 `Moderate`」と入力します。  
  
     作成したフィルター条件が [**式**] テキストボックスに自動的に追加され、次のように表示されます。  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. グリッド内の次の行をクリックし、既定値としての演算子**をそのままにします。**  
  
10. [**演算子**] には、既定値の [ **Contains**] をそのまま使用します。 [**値**] テキストボックスをクリックします。  
  
11. [**フィルター** ] ダイアログボックスの [**マイニング構造列**] の最初の行で`Model`、[] を選択します。  
  
12. [**演算子**] で [ **IS not NULL**] を選択します。 [**値**] テキストボックスは空白のままにします。 **[OK]** をクリックします。  
  
     [**モデルフィルター** ] ダイアログボックスの [**式**] ボックスのフィルター条件は、入れ子になったテーブルに新しい条件が含まれるように自動的に更新されます。 完成した式は次のようになります。  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a>ドリルスルーを有効にして、フィルター選択されたモデルを処理するには  
  
1.  [**マイニングモデル**] タブで、 `Association Filtered`モデルを右クリックし、[**プロパティ**] をクリックします。  
  
2.  **Allowdrillthrough スルー**プロパティを**True**に変更します。  
  
3.  マイニングモデルを右クリックし、[**モデルの処理**] を選択します。 `Association Filtered`  
  
4.  エラーメッセージで [**はい]** をクリックして、新しいモデル[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]をデータベースに配置します。  
  
5.  [**マイニング構造の処理**] ダイアログボックスで、[**実行**] をクリックします。  
  
6.  処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを終了し、もう一度 [**閉じる**] をクリックして [**マイニング構造の処理**] ダイアログボックスを閉じます。  
  
 Microsoft 汎用コンテンツ ツリー ビューアーで NODE_SUPPORT の値を参照すると、フィルター選択されたモデルに含まれているケースの数が元のモデルよりも少ないことを確認できます。  
  
## <a name="remarks"></a>解説  
 ここで作成した入れ子になったテーブルのフィルターでは、そのテーブルに少なくとも 1 つの行があるかどうかのみがチェックされますが、特定の製品の有無を確認するフィルター条件を作成することもできます。  たとえば、次のようなフィルターを作成できます。  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 このステートメントでは、ケース テーブルの顧客を水筒 (water bottle) の購入者のみに制限しています。 ただし、入れ子になったテーブルの属性数には制限がないため、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では選択できる値の一覧が表示されません。 代わりに、値を正確に入力する必要があります。  
  
 [クエリの**編集**] をクリックして、フィルター式を手動で変更できます。 ただし、フィルター式の一部を手動で変更すると、グリッドが無効になり、その後はテキスト編集モードのみでフィルター式を操作する必要があります。 グリッド編集モードに戻すには、フィルター式を消去して最初からやり直す必要があります。  
  
> [!WARNING]  
>  入れ子になったテーブル フィルターで LIKE 演算子を使用することはできません。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [&#41;の関連付けの予測 &#40;中級者向けデータマイニングチュートリアル](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [モデルフィルターの構文と例 &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [マイニングモデルのフィルター &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
