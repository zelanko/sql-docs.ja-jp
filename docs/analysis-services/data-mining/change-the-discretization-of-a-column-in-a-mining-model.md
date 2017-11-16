---
title: "マイニング モデル内の列の分離を変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a3f4295bb22bdc8d3e66fa8e69c1346b7d226953
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>マイニング モデルでの列の分離の変更
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、特定の状況で値が自動的に分離 (データが数値列にビン分割) されます。 たとえば、データに連続する数値データが含まれている場合にデシジョン ツリー モデルを作成すると、データの分布に応じて、連続するデータの各列が自動的にビン分割されます。 データの分離方法を制御するには、モデルでのデータの使用方法を制御するマイニング構造列のプロパティを変更する必要があります。  
  
 マイニング モデルでプロパティを設定する方法については、 [「マイニング モデル列」](../../analysis-services/data-mining/mining-model-columns.md)を参照してください。  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>マイニング モデル列のプロパティを表示するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行を右クリックし、 **[プロパティ]**を選択します。  
  
     マイニング モデル全体に関連付けられているプロパティが、 **[プロパティ]** ウィンドウに表示されます。  
  
2.  画面の左側にある **[構造]** 列で、分離の対象となる連続する数値データを含んだ列をクリックします。  
  
     クリックした列に関連付けられているプロパティのみが **[プロパティ]** ウィンドウに表示されるようになります。  
  
### <a name="to-change-the-discretization-method"></a>分離メソッドを変更するには  
  
1.  **[マイニング プロパティ]** ウィンドウで、 **[コンテンツ]**の横にあるテキスト ボックスをクリックし、一覧から [ **Discretized** ] を選択します。  
  
     マイニング モデル全体に関連付けられているプロパティが、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> プロパティと <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティが有効になりました。  
  
2.  データ マイニング デザイナーの **[プロパティ]** ウィンドウで、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> の横にあるテキスト ボックスをクリックし、 **[Automatic]**、 **[EqualAreas]**、 **[Cluster]**を参照してください。  
  
    > [!NOTE]  
    >  列の使用法が **Ignore**に設定されている場合、その列の **[プロパティ]** ウィンドウは空白になります。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
3.  データ マイニング デザイナーの **[プロパティ]** ウィンドウで、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> の横にあるテキスト ボックスをクリックし、数値を入力します。  
  
    > [!NOTE]  
    >  これらのプロパティを変更した場合は、新しい設定を使用するモデルと共に構造を再処理する必要があります。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  

