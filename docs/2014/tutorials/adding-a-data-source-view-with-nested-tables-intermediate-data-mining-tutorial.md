---
title: 入れ子になったテーブルを含むデータソースビューの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 648b9d561ae340b67ed5e2d1aa878969e5a3bc47
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822781"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a>入れ子になったテーブルを伴うデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)
  マーケット バスケット モデルを作成するには、結合データをサポートしているデータ ソース ビューを使用する必要があります。 このデータ ソース ビューは、シーケンス クラスター シナリオでも使用されます。  
  
 このデータソースビューは、*入れ子になったテーブル*が含まれているため、作業していた可能性があります。 *入れ子になったテーブル*とは、ケーステーブル内の1つの行に関する複数行の情報を含むテーブルです。 たとえば、モデルで顧客の購入行動を分析する場合は、顧客ごとに固有の行があるテーブルをケース テーブルとして使用するのが一般的です。 しかし、1 人の顧客が複数の商品を購入することもあります。また、顧客の一連の購入記録を分析したり、一緒に購入されることの多い商品を分析することが必要になる場合もあります。 モデルを使ってこのような購入記録を論理的に表すには、データ ソース ビューに、顧客ごとの購入記録を一覧表示するテーブルを 1 つ追加します。  
  
 この入れ子になった購入記録テーブルは、多対一のリレーションシップで顧客テーブルに関連付けられます。 入れ子になったテーブルには顧客ごとに複数の行を作成でき、各行には購入された製品 (通常、購入が行われた注文に関する情報が追加されます)、注文時の価格、適用されたプロモーションなどが記録されます。 入れ子になったテーブルの情報は、モデルへの入力または予測可能な属性として使用できます。  
  
 このレッスンでは、次のタスクを実行します。  
  
-   データソースに[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]データソースビューを追加します。  
  
-   このビューにケース テーブルと入れ子になったテーブルを追加します。  
  
-   ケース テーブルと入れ子になったテーブルの間に多対一のリレーションシップを指定します。  
  
    > [!NOTE]  
    >  . 説明した手順に正確に従い、ケース テーブルと入れ子になったテーブルの間のリレーションシップを正しく指定して、モデルの処理時にエラーが発生しないようにすることが重要です。  
  
-   データの列がモデルでどのように使用されるかを定義します。  
  
 ケーステーブルと入れ子になったテーブルの操作、および入れ子になったテーブルキーの選択方法の詳細については、「[入れ子になったテーブル &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。  
  
### <a name="to-add-a-data-source-view"></a>データ ソース ビューを追加するには  
  
1.  ソリューションエクスプローラーで、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。  
  
     データ ソース ビュー ウィザードが開きます。  
  
2.  
  **[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**データソースの選択**] ページの [**リレーショナルデータソース**] で、 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 「基本的なデータマイニングチュートリアル」で作成したデータソースを選択します。 **[次へ]** をクリックします。  
  
4.  [**テーブルとビューの選択**] ページで、次のテーブルを選択し、右矢印をクリックして新しいデータソースビューに追加します。  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  **[次へ]** をクリックします。  
  
6.  既定では、[**ウィザードの完了**] ページにはという名前[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]のデータソースビューがあります。 名前をに`Orders`変更し、[**完了**] をクリックします。  
  
     データソースビューデザイナーが開き、 `Orders`データソースビューが表示されます。  
  
### <a name="to-create-a-relationship-between-tables"></a>2 つのテーブル間のリレーションシップを作成するには  
  
1.  データ ソース ビュー デザイナーで、2 つのテーブルを横に並べて配置します (vAssocSeqLineItems テーブルが左で vAssocSeqOrders テーブルが右)。  
  
2.  VAssocSeqLineItems テーブルの**Ordernumber**列を選択します。  
  
3.  列を vAssocSeqOrders テーブルにドラッグし、 **Ordernumber**列に配置します。  
  
    > [!IMPORTANT]  
    >  結合の "多" の側を表す vAssocSeqLineItems 入れ子になったテーブルの**Ordernumber**列を、結合の一方の側を表す vAssocSeqOrders ケーステーブルにドラッグしてください。  
  
     VAssocSeqLineItems テーブルと vAssocSeqOrders テーブルの間*に多対一のリレーションシップ*が新たに存在するようになりました。 テーブルを正しく結合した場合は、データ ソース ビューに次のように表示されます。  
  
     ![想定されていた、入れ子になったテーブルとケース テーブルとの多対一結合](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "想定されていた、入れ子になったテーブルとケース テーブルとの多対一結合")  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [&#40;中級者向けデータマイニングチュートリアルの作成&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [マイニング構造 &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [マイニングモデル &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
