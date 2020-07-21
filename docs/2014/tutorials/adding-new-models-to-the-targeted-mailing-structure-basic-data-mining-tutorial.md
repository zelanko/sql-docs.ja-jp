---
title: 絞り込みメール配信構造への新しいモデルの追加 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 285ee82110ffdef521d75fb43343f4889663e981
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62822641"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>絞り込みメール配信構造への新しいモデルの追加 (基本的なデータ マイニング チュートリアル)
  このタスクでは、データマイニングデザイナーの [**マイニングモデル**] タブを使用して、2つの追加のモデルを定義します。 モデルの作成には、Microsoft クラスタリング アルゴリズムと Microsoft Naive Bayes アルゴリズムを使用します。 この 2 つのアルゴリズムを選択する理由は、不連続値 (自転車の購入) を予測できるためです。 これらのアルゴリズムの詳細については、「 [Microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)」と「 [Microsoft Naive Bayes algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md) 」を参照してください。  
  
### <a name="to-create-a-clustering-mining-model"></a>クラスター マイニング モデルを作成するには  
  
1.  のデータマイニングデザイナーで [**マイニングモデル**] タブに[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]切り替えます。  
  
     デザイナーには、マイニング構造用と、前のレッスンで作成した`TM_Decision_Tree`マイニングモデル用の2つの列が表示されていることに注意してください。  
  
2.  [**構造**] 列を右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
3.  [**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に`TM_Clustering`「」と入力します。  
  
4.  [**アルゴリズム名**] で、[ **Microsoft クラスタリング**] を選択します。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 データマイニングデザイナーの [**マイニングモデル**] タブに新しいモデルが表示されるようになりました。 クラスタリングアルゴリズムを使用して[!INCLUDE[msCoName](../includes/msconame-md.md)]構築されたこのモデルでは、類似した特性を持つ顧客をクラスターにグループ化し、各クラスターの自転車の購入を予測します。 新しいモデルの列の使用法とプロパティを変更することはできますが、 `TM_Clustering`このチュートリアルではモデルを変更する必要はありません。  
  
### <a name="to-create-a-naive-bayes-mining-model"></a>Naive Bayes マイニング モデルを作成するには  
  
1.  データマイニングデザイナーの [**マイニングモデル**] タブで、[**構造**列] を右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
2.  [**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に`TM_NaiveBayes`「」と入力します。  
  
3.  [**アルゴリズム名**] で [ **Microsoft Naive Bayes**] を選択し、[ **OK**] をクリックします。  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、継続している**Age**と**年収**の列がサポートされていないことを示すメッセージが表示されます。  
  
4.  [**はい**] をクリックしてメッセージを確認し、続行します。  
  
 データマイニングデザイナーの [**マイニングモデル**] タブに新しいモデルが表示されます。 このタブでは、すべてのモデルの列の使用法とプロパティを変更できますが、 `TM_NaiveBayes`このチュートリアルではモデルを変更する必要はありません。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [「&#40;基本的なデータマイニングチュートリアル」では、対象となるメーリングの構造でのモデルの処理&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Analysis Services データマイニング &#40;構造へのマイニングモデルの追加&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)   
 [データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [データ マイニング オブジェクトの移動](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
