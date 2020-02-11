---
title: マイニング構造 (DMX) の削除 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d5c94ec01ff5f11d2b7f663f09de0a7c1527f343
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074077"
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたマイニング構造をデータベースから削除します。 また、構造に関連付けられているすべてのマイニングモデルもデータベースから削除されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP MINING STRUCTURE <structure>  
```  
  
## <a name="arguments"></a>引数  
 *データ*  
 構造体識別子。  
  
## <a name="examples"></a>例  
 次の例は、New Mailing マイニング構造をデータベースから削除します。  
  
```  
DROP MINING STRUCTURE [New Mailing]  
```  
  
## <a name="see-also"></a>参照  
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
