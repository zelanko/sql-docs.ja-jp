---
title: 更新 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9c4f8c1b48ccc6b3f2c2363671f5e3c072f77042
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669174"
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
 任意。 列リストから返される値を制限する条件。  
  
## <a name="examples"></a>例  
 次の例では、 **UPDATE**ステートメントによって、クラスターの既定の名前が `Cluster 1` `001` よりわかりやすい名前に変更され `Likely Customers` ます。  
  
```  
UPDATE [TM Clustering].CONTENT  
SET NODE_CAPTION= 'Likely Customers'  
WHERE NODE_UNIQUE_NAME = '001'  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
