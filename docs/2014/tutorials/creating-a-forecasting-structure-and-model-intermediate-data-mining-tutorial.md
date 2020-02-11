---
title: 予測構造とモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6e631a8983705d4f58e4b193823c9a255284f346
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63204813"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a>Forecasting 構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)
  次に、データ マイニング ウィザードを使用して、先ほど作成したデータ ソース ビューに基づく新しいマイニング構造とマイニング モデルを作成します。 この作業では、マイニング モデルで [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムが使用されるように指定します。  
  
### <a name="to-create-a-forecasting-mining-structure"></a>予測マイニング構造を作成するには  
  
1.  のソリューションエクスプローラーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックします。  
  
2.  
  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。  
  
4.  [**データマイニング構造の作成**] ページの [**使用するデータマイニング技法を指定**してください] で、[ **Microsoft タイムシリーズ**] を選択し、[**次へ**] をクリックします。  
  
5.  [**データソースビューの選択**] ページの [**使用できるデータソースビュー**] で、[ **salesbyregion**] を選択します。  
  
6.  **[次へ]** をクリックします。  
  
7.  [**テーブルの種類の指定**] ページで、vTimeSeries テーブルの [**ケース**] 列のチェックボックスがオンになっていることを確認し、[**次へ**] をクリックします。  
  
8.  [**トレーニングデータの指定**] ページで、modelregion 列と reportingdate 列の [**キー** ] 列のチェックボックスをオンにします。  
  
     ReportingDate は既定でオンになります。これは、データ ソース ビューを作成したときに、この列を論理主キーとして指定したためです。 ModelRegion を 2 つ目のキーとして追加することで、このフィールドに表示されるモデルと領域の組み合わせごとに別々の時系列を作成するようにアルゴリズムに指示します。  
  
9. Quantity 列の**入力**列と**予測可能**列のチェックボックスをオンにし、[**次へ**] をクリックします。  
  
     [**予測可能**] を選択すると、この列のデータに対して予測を作成することができます。 ただし、過去のデータに基づく予測にする必要があるため、列を入力として追加する必要もあります。  
  
10. [列の**コンテンツおよびデータ型の指定**] ページで、選択内容を確認します。  
  
     ModelRegion 列は**キー**列として指定され、reportingdate 列は自動的に**key Time**列として指定されます。 キーの種類ごとにキーを 1 つだけ指定できます。  
  
11. **[次へ]** をクリックします。  
  
12. [**ウィザードの完了**] ページで、[**マイニング構造名**] `Forecasting`に「」と入力します。  
  
    > [!NOTE]  
    >  時系列モデルでは、ドリルスルーを有効にするオプションは使用できません。  
  
13. [**マイニングモデル名**] に`Forecasting`「」と入力し、[**完了**] をクリックします。  
  
     データマイニングデザイナーが開き、作成`Forecasting`したマイニング構造が表示されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [中間データマイニングチュートリアル &#40;予測構造の変更&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Time Series アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
