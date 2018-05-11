---
title: モデルでリグレッサーとして使用する列の指定 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 386458455ed75612d1705e6d25f7ee785111bbd9
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a>モデルでリグレッサーとして使用する列の指定
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  線形回帰モデルでは、予測可能な属性の値が、データをできる限り推定回帰直線に近づけるように入力を組み合わせる式の結果として表されます。 このアルゴリズムでは、入力として使用できるのは数値だけであり、最適な入力が自動的に検出されます。  
  
 ただし、リグレッサーとして含める列を指定することもできます。その場合は、モデルに FORCE_REGRESSOR パラメーターを追加して、使用するリグレッサーを指定します。 この方法は、影響が小さすぎてモデルで検出されない場合にも意味を持つ属性や、確実に式に含まれるようにしたい属性がある場合に使用できます。  
  
 [次の手順では、ニューラル ネットワークのチュートリアル](http://msdn.microsoft.com/library/42c3701a-1fd2-44ff-b7de-377345bbbd6b)で使用したのと同じサンプル データを使用して、単純な線形回帰モデルを作成する方法について説明します。 このモデルは必ずしも堅牢ではありませんが、データ マイニング デザイナーを使用して線形回帰モデルをカスタマイズする方法を示しています。  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a>単純な線形回帰モデルを作成する方法  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラーで**、 **[マイニング構造]** を展開します。  
  
2.  Call Center.dmm をダブルクリックしてデザイナーで開きます。  
  
3.  **[マイニング モデル]** メニューの **[新しいマイニング モデル]** をクリックします。  
  
4.  アルゴリズムとして **[Microsoft 線形回帰]** を選択します。 名前として「 **Call Center Regression**」と入力します。  
  
5.  **[マイニング モデル]** タブで、列の使用方法を次のように変更します。 これ以外の列はすべて **[無視]** に設定します (まだ設定されていない場合)。  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Total Operators**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  **[マイニング モデル]** メニューの **[モデル パラメーターの設定]** をクリックします。  
  
7.  パラメーター FORCE_REGRESSOR の **[値]** 列に、列の名前を入力します。次のように各かっこで囲み、コンマで区切って入力します。  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  このアルゴリズムでは、リグレッサーとして最適な列が自動的に検出されます。 リグレッサーを強制する必要があるのは、最終的な式に確実に含まれるようにしたい列がある場合だけです。  
  
8.  **[マイニング モデル]** メニューの **[モデルの処理]** をクリックします。  
  
     ビューアーでは、モデルが、回帰式を含む 1 つのノードとして表されます。 その式を **マイニング凡例**に表示したり、クエリを使用して式の係数を抽出したりすることもできます。  
  
## <a name="see-also"></a>参照  
 [Microsoft 線形回帰アルゴリズム](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)   
 [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [線形回帰モデル & #40; のマイニング モデル コンテンツAnalysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
