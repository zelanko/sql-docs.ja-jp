---
title: "マイニング モデルのテストに使用する列の選択 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [data mining], predictable mining columns
- Mining Accuracy Chart [Analysis Services], columns
- predictable mining columns [Analysis Services]
ms.assetid: c6a8f23a-da21-4f31-9521-99460d624649
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 995738c17a385d26e647a6c650c21a791b872a0e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="choose-the-column-to-use-for-testing-a-mining-model"></a>マイニング モデルのテストに使用する列の選択
  マイニング モデルの精度を測定する前に、評価するのがどの結果なのかを決定する必要があります。 多くのデータ マイニング モデルでは、モデルの作成時に、予測可能な属性として使用する少なくとも 1 つの列を選択する必要があります。 そのため、モデルの精度をテストするときに、通常はその属性をテスト対象として選択する必要があります。  
  
 次の一覧では、テストに使用する予測可能な属性を選択する際のいくつかの追加の考慮事項について説明します。  
  
-   一部の種類のデータ マイニング モデルでは、複数の属性を予測できます。たとえば、ニューラル ネットワークでは、多くの属性間の関係を調べることができます。  
  
-   クラスター モデルなど、他の種類のマイニング モデルには、予測可能な属性がなくてもかまいません。 予測可能な属性がない場合、クラスター モデルはテストできません。  
  
-   散布図を作成するか、回帰モデルの精度を測定するには、連続する予測可能な属性を結果として選択する必要があります。 その場合、対象の値は指定できません。 散布図以外のものを作成する場合は、基になるマイニング構造列のコンテンツの種類も、 **[不連続]** または **[分離]**である必要があります。  
  
-   不連続属性を予測可能な結果として選択した場合は、対象の値を指定することも、 **[予測値]** フィールドを空のままにすることもできます。 **予測値**を含める場合、グラフは対象の値の予測でのモデルの効果だけを測定します。 対象となる結果を指定しない場合、モデルはすべての結果の予測で精度が測定されます。  
  
-   複数のモデルを含めて、それらを 1 つの精度チャートで比較する場合、すべてのモデルは同じ予測可能列を使用する必要があります。  
  
-   クロス検証レポートを作成する場合は、同じ予測可能な属性を持つすべてのモデルが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって自動的に分析されます。  
  
-   オプションの **[予測列と値の同期]**が選択されている場合は、同じ名前および一致するデータ型を持つ予測可能列が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって自動的に選択されます。 列がこれらの基準を満たさない場合は、このオプションをオフにして、手動で予測可能列を選択できます。 モデルとは異なる列を持つ外部データ セットのモデルをテストしている場合は、このように操作しなければならないことがあります。 ただし、不適切なデータ型の列を選択すると、エラーが発生するか、正しい結果を得ることができません。  
  
### <a name="specify-the-outcome-to-predict"></a>予測する結果の指定  
  
1.  マイニング構造をダブルクリックしてデータ マイニング デザイナーで開きます。  
  
2.  **[マイニング精度チャート]** タブをクリックします。  
  
3.  **[入力の選択]** タブを選択します。  
  
4.  **[入力の選択]** タブの **[予測可能列名]**で、グラフに含めるモデルごとに予測可能列を選択します。  
  
     **[予測可能列名]** ボックスに表示されるマイニング モデル列は、使用法が **[予測]** または **[予測のみ]**に設定されている列だけです。  
  
5.  モデルのリフト値を指定する場合は、 **[予測値]** の一覧から、測定する特定の結果値を選択する必要があります。  
  
## <a name="see-also"></a>参照  
 [モデルのテスト データの選択およびマップ](../../analysis-services/data-mining/choose-and-map-model-testing-data.md)   
 [精度チャートの種類と設定を選択してグラフのオプション](../../analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
