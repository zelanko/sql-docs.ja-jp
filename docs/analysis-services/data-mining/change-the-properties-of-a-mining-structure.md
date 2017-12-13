---
title: "マイニング構造のプロパティの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dd5b15a108bfcb808bac85913516068477d172a1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="change-the-properties-of-a-mining-structure"></a>マイニング構造のプロパティの変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]どちらも変更することができます、マイニング構造のプロパティの 2 種類あります。  
  
-   構造全体に影響するマイニング構造のプロパティ  
  
-   構造の各列のプロパティ  
  
 他のプロパティの設定に依存するプロパティもあります。 たとえば、ビン分割動作を制御するプロパティ ( <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティや <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>プロパティ) は、その列のデータ型が **Discretized**に設定されていないと設定できません。  
  
 マイニング構造プロパティの詳細については、「 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)」を参照してください。  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>マイニング構造のプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング構造]** タブで、マイニング構造またはマイニング構造内の列を右クリックし、 **[プロパティ]**を選択します。  
  
     **[プロパティ]** ウィンドウが画面の右側に表示されます (まだ表示されていない場合)。  
  
2.  **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を選択し、新しい値を入力します。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
