---
title: コール センター構造 (中級者向けデータ マイニング チュートリアル) へのロジスティック回帰モデルの追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ccadf7665b112b6ba1055fdcf69aeb99609c3ab3
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312431"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a>コール センター構造へのロジスティック回帰モデルの追加 (中級者向けデータ マイニング チュートリアル)
  コール センターの業務に影響する可能性のある要因を分析すると共に、スタッフのサービス品質を向上させるための具体的な改善案を提出するように求められました。 ここでは、調査モデルの構築に使用したものと同じマイニング構造を使用し、予測作成用のマイニング モデルを追加します。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のロジスティック回帰モデルは、ニューラル ネットワークのアルゴリズムを基礎としているため、ニューラル ネットワーク モデルと同等の柔軟性と機能を備えながらも、 バイナリ結果を予測するという目的に特に適したモデルと言えます。  
  
 このシナリオでは、ニューラル ネットワーク モデルに使用したものと同じマイニング構造を使用します。 ただし、新しいモデルを実務上の目的に合わせてカスタマイズします。 ここでは、サービス品質を向上させることと、経験を積んだオペレーターが何人必要かを特定することが目的であるため、それらの値を予測するモデルを設定します。  
  
 コール センター データに基づくすべてのモデルの類似性をできる限り確保するために、前の作業と同じシード パラメーターを使用します。 シード パラメーターを設定すると、モデルでのデータ処理の開始位置が同じになり、データのアーティファクトによるバリエーションを最小限に抑えることができます。  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a>コール センターのマイニング構造に新しいマイニング モデルを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、ソリューション エクスプ ローラーで、マイニング構造を右クリックして**Call Center Binned**を選択して**デザイナーを開く**です。  
  
2.  データ マイニング デザイナーで、をクリックして、**マイニング モデル**タブです。  
  
3.  をクリックして**関連マイニング モデルを作成する**です。  
  
4.  **新しいマイニング モデル** ダイアログ ボックスの**モデル名**、型`Call Center - LR`です。  **アルゴリズム名** **Microsoft ロジスティック回帰**です。  
  
5.  **[OK]** をクリックします。  
  
     新しいマイニング モデルが表示されます、**マイニング モデル**タブです。  
  
### <a name="to-customize-the-logistic-regression-model"></a>ロジスティック回帰モデルをカスタマイズするには  
  
1.  新しいマイニング モデルの列に`Call Center - LR`、Fact CallCenter ID、キーとしてのままにします。  
  
2.  ServiceGrade とレベルを 2 つの演算子の値を変更**Predict**です。  
  
     これらの列は、入力および予測の両方に使用されます。 本質的には、同じデータについて、2 つの別個のモデルを作成していることになります。ここでは、オペレーターの数を予測するモデルとサービス グレードを予測するモデルを作成しています。  
  
3.  他のすべての列を変更する**入力**です。  
  
### <a name="to-specify-the-seed-and-process-the-models"></a>シードを指定してモデルを処理するには  
  
1.  **マイニング モデルの**] タブで、名前付き Call Center - LR、モデルの列を右クリックし、選択 **[アルゴリズム パラメーターの**します。  
  
2.  HOLDOUT_SEED パラメーターの行の下の空のセルをクリックして**値**、および種類`1`です。 **[OK]** をクリックします。  
  
    > [!NOTE]  
    >  関連するすべてのモデルで同じシードを使用する限り、シードとしてどのような値を選択するかは特に重要ではありません。  
  
3.  **マイニング モデル**メニューの **および全モデルのマイニング構造の処理**です。 をクリックして**はい**サーバーに更新されたデータ マイニング プロジェクトを配置します。  
  
4.  **マイニング モデルの処理**ダイアログ ボックスで、をクリックして**実行**です。  
  
5.  をクリックして**閉じる**を閉じる、**処理の進行状況**クリックしてダイアログ ボックスで、**閉じる**で再度、**マイニング モデルの処理** ダイアログ ボックス。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [コール センター モデルの予測の作成&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [処理の要件および考慮事項&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  