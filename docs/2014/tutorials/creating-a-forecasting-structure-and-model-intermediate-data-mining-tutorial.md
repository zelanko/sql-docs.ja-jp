---
title: Forecasting 構造およびモデル (中級者向けデータ マイニング チュートリアル) の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 47d6e75a691c53fe1658fb5f79ee2bde8e9c2d01
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312270"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a>Forecasting 構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)
  次に、データ マイニング ウィザードを使用して、先ほど作成したデータ ソース ビューに基づく新しいマイニング構造とマイニング モデルを作成します。 この作業では、マイニング モデルで [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムが使用されるように指定します。  
  
### <a name="to-create-a-forecasting-mining-structure"></a>予測マイニング構造を作成するには  
  
1.  ソリューション エクスプ ローラーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を右クリックして**マイニング構造**選択**新しいマイニング構造**です。  
  
2.  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  **定義方法の選択** ページであることを確認**既存のリレーショナル データベースまたはデータ ウェアハウスから**を選択して、をクリックして**次**です。  
  
4.  **データ マイニング構造の作成**] ページの [**を使用するデータ マイニング技法?** を選択**Microsoft タイム シリーズ**、順にクリック **[次へ]** です。  
  
5.  **データ ソース ビューの選択** ページの **使用可能なデータ ソース ビュー** **SalesByRegion**です。  
  
6.  **[次へ]** をクリックします。  
  
7.  **テーブルの種類の指定** ページで、チェック ボックスを確認してください、**ケース**vTimeSeries テーブルの列を選択して、をクリックして**次**です。  
  
8.  **トレーニング データの指定** ページで、チェック ボックスをオン、**キー** ModelRegion 列および ReportingDate 列の列です。  
  
     ReportingDate は既定でオンになります。これは、データ ソース ビューを作成したときに、この列を論理主キーとして指定したためです。 ModelRegion を 2 つ目のキーとして追加することで、このフィールドに表示されるモデルと領域の組み合わせごとに別々の時系列を作成するようにアルゴリズムに指示します。  
  
9. チェック ボックスをオン、**入力**と**予測可能**列、Quantity、列、およびクリックを **[次へ]** です。  
  
     選択して**Predictable**、この列のデータの予測を作成することを示します。 ただし、過去のデータに基づく予測にする必要があるため、列を入力として追加する必要もあります。  
  
10. ページで**コンテンツおよびデータ型の列の指定の**、選択内容を確認します。  
  
     ModelRegion 列は、として指定されて、**キー**列および ReportingDate 列として指定されて自動的に、 **Key Time**列です。 キーの種類ごとにキーを 1 つだけ指定できます。  
  
11. **[次へ]** をクリックします。  
  
12. **ウィザードの完了** ページの**マイニング構造名**、型`Forecasting`です。  
  
    > [!NOTE]  
    >  時系列モデルでは、ドリルスルーを有効にするオプションは使用できません。  
  
13. **マイニング モデル名**、型`Forecasting`、クリックして**完了**です。  
  
     データ マイニング デザイナーで開いて、表示、`Forecasting`先ほど作成したマイニング構造です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [Forecasting 構造の変更&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング デザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft タイム シリーズ アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  