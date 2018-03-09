---
title: "マイニング モデル (DMX) の削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DROP_MINING_MODEL
dev_langs: DMX
helpviewer_keywords:
- DROP MINING MODEL statement
- deleting mining models
- removing mining models
- dropping mining models
- mining models [Analysis Services], deleting
ms.assetid: 8ff561d0-a526-4712-9fff-11df9f8c45a1
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 363b3e52463f2c9e58a3f31895e4a685a28761c6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="drop-mining-model-dmx"></a>DROP MINING MODEL (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データベースからマイニング モデルを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP MINING MODEL <model >  
```  
  
## <a name="arguments"></a>引数  
 *model*  
 モデル識別子です。  
  
## <a name="examples"></a>使用例  
 次のサンプル コードは、マイニング モデル NBSample を削除します。  
  
```  
DROP MINING MODEL [NBSample]  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
