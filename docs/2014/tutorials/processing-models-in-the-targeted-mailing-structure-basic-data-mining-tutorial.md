---
title: 絞り込みメール配信構造でのモデルの処理 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 605088d405cbd2dcfba92a2da5fa4e07c38d8f0b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188230"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a>絞り込みメール配信構造でのモデルの処理 (基本的なデータ マイニング チュートリアル)
  作成したマイニング モデルを参照したり操作したりする前に、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを配置し、マイニング構造とマイニング モデルを処理する必要があります。  
  
-   *配置*によってサーバーにプロジェクトが送信され、サーバー上のそのプロジェクトにオブジェクトが作成されます。  
  
-   *処理*で[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は、リレーショナルデータソースのデータをオブジェクトに格納します。  
  
 モデルを使用するには、事前にそのモデルを配置して処理する必要があります。 また、新しいデータの追加などにより、モデルに変更を加えた場合は、モデルを再配置して再処理する必要があります。  
  
## <a name="ensuring-consistency-with-holdoutseed"></a>HoldoutSeed との一貫性の確保  
 プロジェクトを配置し、構造とモデルを処理すると、データ構造内の個々の行が数値型のシード値に基づいてトレーニング セットまたはテスト セットに割り当てられます。 既定では、数値型のシード値は、データ構造の属性に基づいて計算されます。 ただし、モデルの特定の側面を変更すると、シード値も変更されるため、微妙に異なる結果につながります。 したがって、ここで説明した結果が同じであることを確認するために、では*holdout seed*固定提示シード`12`を任意に割り当てます。 提示されたシードは、サンプリング アルゴリズムの初期化に使用され、すべてのマイニング構造とそのモデルで同じ方法でデータが分割されるようにします。  
  
 この値は、トレーニング セット内に含まれるケースの数に影響しません。単純に、モデルを構築するたびに、同じ分割方法が使用されることを保証します。  
  
 提示されたシードの詳細については、「[データセットのトレーニングとテスト](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)」を参照してください。  
  
#### <a name="to-set-the-holdout-seed"></a>提示されたシードを設定するには  
  
1.  のデータマイニングデザイナーで、[**マイニング構造**] タブまたは [**マイニングモデル**] タブをクリックし[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ます。  
  
     **絞り込みメール配信 MiningStructure**が**プロパティ**ペインに表示されます。  
  
2.  **F4**キーを押して、[**プロパティ**] ウィンドウが開いていることを確認します。  
  
3.  **Cachemode**が**KeepTrainingCases**に設定されていることを確認します。  
  
4.  「 `12` For **HoldoutSeed**」と入力します。  
  
## <a name="deploying-and-processing-the-models"></a>モデルの配置と処理  
 データマイニングデザイナーでは、モデルまたは基になるデータに対して行った変更のスコープに応じて、どのオブジェクトを処理するかを決定できます。  
  
 ここでは、既存の設定に変更を加えるのではなく、新しいデータと新しいモデルを使用するため、構造とすべてのモデルを同時に処理します。  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a>プロジェクトを配置してすべてのマイニング モデルを処理するには  
  
1.  [**マイニングモデル**] メニューで、[**マイニング構造とすべてのモデルの処理**] を選択します。  
  
     マイニング構造に変更を加えた場合は、マイニング モデルを処理する前にプロジェクトをビルドして配置するように求められます。 **[はい]** をクリックします。  
  
2.  [**マイニング構造の処理-対象メーリング**] ダイアログボックスで [**実行**] をクリックします。  
  
     **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。 使用するコンピューターによっては、モデル処理に多少時間がかかる場合があります。  
  
3.  モデルの処理が完了したら、 **[処理の進行状況]** ダイアログ ボックスの **[閉じる]** をクリックします。  
  
4.  [**マイニング構造の処理- \<構造>** ] ダイアログボックスで [**閉じる**] をクリックします。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [&#40;基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造への新しいモデルの追加&#41;](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [処理の要件および注意事項 &#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
