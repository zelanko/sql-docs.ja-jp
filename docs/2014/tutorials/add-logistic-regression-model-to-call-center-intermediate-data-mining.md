---
title: コールセンター構造へのロジスティック回帰モデルの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 32e66a84dea20964c11c7de0aa568530aa8c28c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62823279"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a>コール センター構造へのロジスティック回帰モデルの追加 (中級者向けデータ マイニング チュートリアル)
  コール センターの業務に影響する可能性のある要因を分析すると共に、スタッフのサービス品質を向上させるための具体的な改善案を提出するように求められました。 ここでは、調査モデルの構築に使用したものと同じマイニング構造を使用し、予測作成用のマイニング モデルを追加します。  
  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のロジスティック回帰モデルは、ニューラル ネットワークのアルゴリズムを基礎としているため、ニューラル ネットワーク モデルと同等の柔軟性と機能を備えながらも、 バイナリ結果を予測するという目的に特に適したモデルと言えます。  
  
 このシナリオでは、ニューラル ネットワーク モデルに使用したものと同じマイニング構造を使用します。 ただし、新しいモデルを実務上の目的に合わせてカスタマイズします。 ここでは、サービス品質を向上させることと、経験を積んだオペレーターが何人必要かを特定することが目的であるため、それらの値を予測するモデルを設定します。  
  
 コール センター データに基づくすべてのモデルの類似性をできる限り確保するために、前の作業と同じシード パラメーターを使用します。 シード パラメーターを設定すると、モデルでのデータ処理の開始位置が同じになり、データのアーティファクトによるバリエーションを最小限に抑えることができます。  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a>コール センターのマイニング構造に新しいマイニング モデルを追加するには  
  
1.  のソリューションエクスプローラーで、[マイニング構造] を右クリックし、[**コールセンター**] ビンをクリックして、[デザイナーを開く] を選択します。 **** [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]  
  
2.  データマイニングデザイナーで、[**マイニングモデル**] タブをクリックします。  
  
3.  [**関連マイニングモデルの作成] を**クリックします。  
  
4.  [**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に`Call Center - LR`、「」と入力します。  [**アルゴリズム名**] で、[ **Microsoft ロジスティック回帰**] を選択します。  
  
5.  **[OK]** をクリックします。  
  
     新しいマイニングモデルが [**マイニングモデル**] タブに表示されます。  
  
### <a name="to-customize-the-logistic-regression-model"></a>ロジスティック回帰モデルをカスタマイズするには  
  
1.  新しいマイニングモデル`Call Center - LR`の列で、ファクト CALLCENTER ID をキーとして残します。  
  
2.  ServiceGrade の値とレベル2の演算子を**Predict**に変更します。  
  
     これらの列は、入力および予測の両方に使用されます。 本質的には、同じデータについて、2 つの別個のモデルを作成していることになります。ここでは、オペレーターの数を予測するモデルとサービス グレードを予測するモデルを作成しています。  
  
3.  他のすべての列を**入力**に変更します。  
  
### <a name="to-specify-the-seed-and-process-the-models"></a>シードを指定してモデルを処理するには  
  
1.  [**マイニングモデル**] タブで、Call CENTER-LR という名前のモデルの列を右クリックし、[**アルゴリズムパラメーターの設定**] を選択します。  
  
2.  HOLDOUT_SEED パラメーターの行で、[**値**] の下の空のセルをクリック`1`し、「」と入力します。 **[OK]** をクリックします。  
  
    > [!NOTE]  
    >  関連するすべてのモデルで同じシードを使用する限り、シードとしてどのような値を選択するかは特に重要ではありません。  
  
3.  [**マイニングモデル**] メニューで、[**マイニング構造とすべてのモデルの処理**] を選択します。 [**はい**] をクリックして、更新されたデータマイニングプロジェクトをサーバーに配置します。  
  
4.  [**マイニングモデルの処理**] ダイアログボックスで、[**実行**] をクリックします。  
  
5.  [**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じ、[**マイニングモデルの処理**] ダイアログボックスでもう一度 [**閉じる**] をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [「中級者向けデータマイニングチュートリアル &#40;コールセンターモデルの予測の作成&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データマイニング&#41;&#40;処理の要件と考慮事項](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
