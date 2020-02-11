---
title: 更新 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2d28df68512f9c97faebf3ee00b2aa34a2b8d1a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028672"
---
# <a name="update-dmx"></a>更新 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データマイニングモデルの**NODE_CAPTION**列を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPDATE <model>.CONTENT  
SET NODE_CAPTION='new caption'  
[WHERE <condition expression>]  
```  
  
## <a name="arguments"></a>引数  
 *model*  
 モデル識別子。  
  
 *新しいキャプション*  
 **NODE_CAPTION**列の新しい名前を含む文字列。  
  
 *条件式*  
 省略可能。 列リストから返される値を制限する条件。  
  
## <a name="examples"></a>例  
 次の例では、 **UPDATE**ステートメントによって、クラスター `Cluster 1` `001`の既定の名前がよりわかりやすい名前`Likely Customers`に変更されます。  
  
```  
UPDATE [TM Clustering].CONTENT  
SET NODE_CAPTION= 'Likely Customers'  
WHERE NODE_UNIQUE_NAME = '001'  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
