---
title: Forecasting 構造 (中級者向けデータ マイニング チュートリアル) の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 559f6aa6b31b8998703a93e84dc100ce375cbda8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139532"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Forecasting 構造の変更 (中級者向けデータ マイニング チュートリアル)
  前の作業で作成したマイニング構造には予測モデルが 1 つ存在します。 このモデルを処理して検証する前に、マイニング構造に少し手を加え、プロパティの 1 つを変更する必要があります。  
  
## <a name="modifying-the-mining-structure"></a>マイニング構造の修正  
 使用して、マイニング構造を変更することができます、**マイニング構造**データ マイニング デザイナーのタブ。 データ マイニング ウィザードでモデルを作成するときは、ReportingDate 列、ModelRegion 列、Quantity 列の 3 つを使用しました。 ただし、 **Forecasting**テーブルには、売り上げ高を予測に使用する Amount 列も含まれています。 使用して、**マイニング構造** タブで、マイニング構造にデータ ソース ビューからこの列を追加することができます。  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>Amount 列を予測マイニング構造に追加するには  
  
1.  **マイニング構造の**データ マイニング デザイナーのタブで、**データ ソース ビュー**ウィンドウで、vTimeSeries テーブルの Amount 列を選択します。  
  
2.  Amount 列をドラッグして、**データ ソース ビュー**ペインの列の一覧、 **Forecasting**構造体。  
  
     Amount 列が含まれるようになりました、 **Forecasting**マイニング構造です。  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>マイニング モデルの列の変更  
 マイニング構造に新しい列を追加したので、次は、マイニング モデルにおけるその列の使用方法を定義する必要があります。 列の使用方法を指定することができます、**マイニング モデル**データ マイニング デザイナーのタブ。  
  
 **マイニング モデル** タブで、マイニング構造を含む列を一覧表示、**構造**グリッド、およびリストの名前を持つ列で、マイニング モデルを含む列の列、この場合、モデル**Forecasting**します。 更新するには、列名をクリックします。 **Forecasting**マイニング モデルでは、Amount 列は、入力列として使用され、将来の売上を予測にも使用されます。 したがって、入力列として、さらには予測可能列として使用できるように、この列のプロパティを設定する必要があります。  
  
> [!NOTE]  
>  **マイニング モデル** タブで、同じ構造に基づく新しいモデルも作成でき、各モデルのアルゴリズムと列のプロパティを調整することができます。 ただし、これらの変更を反映するには、モデルを処理する必要があります。  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>Amount 列の使用方法を定義するには  
  
1.  **Forecasting**上のグリッドの列、**マイニング モデル** タブで、Amount 行のセルをクリックします。  
  
2.  選択**Predict**一覧から。  
  
     入力列および予測可能列として、Amount 列を使用できるようになりました。  
  
 列を選択して開く操作により、個々 の列のプロパティを変更することも、**プロパティ**ウィンドウ。 開くには、**プロパティ**ウィンドウで、列名を右クリックし、**プロパティ**します。 各モデルの列内でプロパティを変更する場合は、そのモデルのプロパティのみを変更できます。 ただし、内のプロパティを変更すると、**構造**列で、変更は、構造に関連付けられているすべてのモデルに影響します。 モデルまたは構造に変更を加えた場合は、必ず再処理して影響を確認する必要があります。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [予測モデルの処理のカスタマイズと&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [マイニング構造&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [マイニング モデル&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
