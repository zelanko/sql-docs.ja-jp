---
title: データソースビューの作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ac7730e8437eaed304ed69c40e45fc93ee9b5531
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68888648"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a>データ ソース ビューの作成 (基本的なデータ マイニング チュートリアル)
  データ ソース ビューは、データ ソース上に構築され、データのサブセットを定義します。このデータ ソース ビューを、マイニング構造で使用できます。 また、データ ソース ビューを使用して、列の追加、計算列や集計の作成、および名前付きビューの追加を行うこともできます。 データ ソース ビューを使用すると、プロジェクトに関連するデータの選択、テーブルどうしの関連付け、データの構造の変更などの操作を、元のデータ ソースを変更せずに実行できます。 詳細については、 [「多次元モデルのデータ ソース ビュー」](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)を参照してください。  
  
### <a name="to-create-a-data-source-view"></a>データ ソース ビューを作成するには  
  
1.  
  **ソリューション エクスプローラー**で **[データ ソース ビュー]** を右クリックし、 **[新しいデータ ソース ビュー]** をクリックします。  
  
2.  
  **[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  
  **[データ ソースの選択]** ページの **[リレーショナル データ ソース]** で、前回の作業で作成した [Adventure Works DW 2012] データ ソースを選択します。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  新しいデータ ソースを作成する場合は、 **[データ ソース]** を右クリックし、 **[新しいデータ ソース]** をクリックして、データ ソース ウィザードを開始します。  
  
4.  
  **[テーブルとビューの選択]** ページで次のオブジェクトを選択し、右矢印をクリックして、これらのオブジェクトを新しいデータ ソース ビューに追加します。  
  
    -   **ProspectiveBuyer (dbo)** -見込み自転車購入者のテーブル  
  
    -   **Vtargetmail (dbo)** -過去の自転車購入者に関する履歴データの表示  
  
5.  **[次へ]** をクリックします。  
  
6.  既定では、Adventure Works DW 2012 という名前のデータ ソース ビューが **[ウィザードの完了]** ページに表示されます。 名前をに`Targeted Mailing`変更し、[**完了**] をクリックします。  
  
     新しいデータ ソース ビューが **[Targeted Mailing.dsv [Design]]** タブで開きます。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [データソースの作成 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: &#40;の基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造の作成&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データソースビュー &#40;Analysis Services の定義&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
