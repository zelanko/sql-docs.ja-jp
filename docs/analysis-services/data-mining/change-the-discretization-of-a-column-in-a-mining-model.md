---
title: マイニング モデル内の列の分離の変更 |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8a85b645562ce39f19c15191b6b1d3ba4a7fb332
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62670449"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>マイニング モデルでの列の分離の変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 値が自動的に分離-列の数値のデータのビンのつまり、特定のシナリオ。 たとえば、データに連続する数値データが含まれている場合にデシジョン ツリー モデルを作成すると、データの分布に応じて、連続するデータの各列が自動的にビン分割されます。 データの分離方法を制御するには、モデルでのデータの使用方法を制御するマイニング構造列のプロパティを変更する必要があります。  
  
 マイニング モデルでプロパティを設定する方法については、 [「マイニング モデル列」](../../analysis-services/data-mining/mining-model-columns.md)を参照してください。  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>マイニング モデル列のプロパティを表示するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行を右クリックし、 **[プロパティ]** を選択します。  
  
     マイニング モデル全体に関連付けられているプロパティが、 **[プロパティ]** ウィンドウに表示されます。  
  
2.  画面の左側にある **[構造]** 列で、分離の対象となる連続する数値データを含んだ列をクリックします。  
  
     クリックした列に関連付けられているプロパティのみが **[プロパティ]** ウィンドウに表示されるようになります。  
  
### <a name="to-change-the-discretization-method"></a>分離メソッドを変更するには  
  
1.  **[マイニング プロパティ]** ウィンドウで、 **[コンテンツ]** の横にあるテキスト ボックスをクリックし、一覧から [ **Discretized** ] を選択します。  
  
     マイニング モデル全体に関連付けられているプロパティが、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> プロパティと <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティが有効になりました。  
  
2.  **プロパティ**ウィンドウで、テキスト ボックスには、[次へ] をクリックします<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A>値は次のいずれかを選択します。**自動**、 **EqualAreas**、または**クラスター**します。  
  
    > [!NOTE]  
    >  列の使用法が **Ignore**に設定されている場合、その列の **[プロパティ]** ウィンドウは空白になります。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
3.  データ マイニング デザイナーの **[プロパティ]** ウィンドウで、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> の横にあるテキスト ボックスをクリックし、数値を入力します。  
  
    > [!NOTE]  
    >  これらのプロパティを変更した場合は、新しい設定を使用するモデルと共に構造を再処理する必要があります。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
