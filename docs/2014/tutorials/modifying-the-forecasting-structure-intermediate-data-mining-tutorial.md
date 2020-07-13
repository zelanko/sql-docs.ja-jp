---
title: 予測構造の変更 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a86ddf0a715fc3a2313f555e898b3bd94cf66d8c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63301298"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Forecasting 構造の変更 (中級者向けデータ マイニング チュートリアル)
  前の作業で作成したマイニング構造には予測モデルが 1 つ存在します。 このモデルを処理して検証する前に、マイニング構造に少し手を加え、プロパティの 1 つを変更する必要があります。  
  
## <a name="modifying-the-mining-structure"></a>マイニング構造の修正  
 マイニング構造を変更するには、データマイニングデザイナーの [**マイニング構造**] タブを使用します。 データ マイニング ウィザードでモデルを作成するときは、ReportingDate 列、ModelRegion 列、Quantity 列の 3 つを使用しました。 ただし、**予測**テーブルには、売上高の予測に使用できる amount 列も含まれています。 [**マイニング構造**] タブを使用すると、データソースビューからマイニング構造にこの列を追加できます。  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>Amount 列を予測マイニング構造に追加するには  
  
1.  データマイニングデザイナーの [**マイニング構造**] タブの [**データソースビュー** ] ペインで、vTimeSeries テーブルの Amount 列を選択します。  
  
2.  [**データソースビュー** ] ペインの [Amount] 列を、**予測**構造の列の一覧にドラッグします。  
  
     Amount 列が**予測**マイニング構造に含まれるようになりました。  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>マイニング モデルの列の変更  
 マイニング構造に新しい列を追加したので、次は、マイニング モデルにおけるその列の使用方法を定義する必要があります。 列を使用する方法は、データマイニングデザイナーの [**マイニングモデル**] タブで指定できます。  
  
 [**マイニングモデル**] タブには、マイニング構造に含まれる列がグリッドの [**構造**] 列に一覧表示され、モデルの名前を持つ列にマイニングモデルに含まれている列が一覧表示されます (この場合は [**予測**])。 更新するには、列名をクリックします。 **予測**マイニングモデルでは、[Amount] 列が入力列として使用され、将来の売上を予測するためにも使用されます。 したがって、入力列として、さらには予測可能列として使用できるように、この列のプロパティを設定する必要があります。  
  
> [!NOTE]  
>  [**マイニングモデル**] タブでは、同じ構造に基づいて新しいモデルを作成することもできます。また、各モデルのアルゴリズムと列のプロパティを調整することもできます。 ただし、これらの変更を反映するには、モデルを処理する必要があります。  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>Amount 列の使用方法を定義するには  
  
1.  [**マイニングモデル**] タブのグリッドの [**予測**] 列で、Amount 行のセルをクリックします。  
  
2.  一覧から [ **Predict** ] を選択します。  
  
     入力列および予測可能列として、Amount 列を使用できるようになりました。  
  
 列を選択し、[**プロパティ**] ウィンドウを開くことで、個々の列のプロパティを変更することもできます。 [**プロパティ**] ウィンドウを開くには、列名を右クリックし、[**プロパティ**] を選択します。 各モデルの列内でプロパティを変更する場合は、そのモデルのプロパティのみを変更できます。 ただし、**構造**列内のプロパティを変更すると、その変更は構造に関連付けられているすべてのモデルに影響を及ぼします。 モデルまたは構造に変更を加えた場合は、必ず再処理して影響を確認する必要があります。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [予測モデルのカスタマイズと処理 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [マイニング構造 &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [マイニング モデル (Analysis Services - データ マイニング)](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
