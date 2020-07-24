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
ms.openlocfilehash: f77d71eab284b695171e923cfe53b53575d45d94
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971540"
---
# <a name="update-dmx"></a>更新 (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
  
