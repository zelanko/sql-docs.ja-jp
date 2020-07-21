---
title: マイニング構造のプロパティを変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4b56fc1d00fe639d78d5f01fe44554b7fe2d7cc7
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84524958"
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
  
  
