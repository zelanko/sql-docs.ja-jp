---
title: マイニング構造のプロパティの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 56942ebc74e1a0b49303f842ec2668a46f6f209f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689337"
---
# <a name="change-the-properties-of-a-mining-structure"></a>マイニング構造のプロパティの変更
  マイニング構造には次の 2 種類のプロパティがあり、どちらも変更できます。  
  
-   構造全体に影響するマイニング構造のプロパティ  
  
-   構造の各列のプロパティ  
  
 他のプロパティの設定に依存するプロパティもあります。 たとえば、ビン分割動作を制御するプロパティ (<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティや <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> プロパティ) は、その列のデータ型が `Discretized` に設定されていないと設定できません。  
  
 マイニング構造プロパティの詳細については、「 [マイニング構造列](mining-structure-columns.md)」を参照してください。  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>マイニング構造のプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング構造]** タブで、マイニング構造またはマイニング構造内の列を右クリックし、 **[プロパティ]** を選択します。  
  
     **[プロパティ]** ウィンドウが画面の右側に表示されます (まだ表示されていない場合)。  
  
2.  **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を選択し、新しい値を入力します。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](mining-structure-tasks-and-how-tos.md)  
  
  
