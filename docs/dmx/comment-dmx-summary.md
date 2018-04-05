---
title: -(コメント) (DMX) の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- commenting characters
- double hyphens
- -- (comment character)
ms.assetid: 487b580b-5b81-4e52-8868-4fa809e4ef58
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 40b4189e6ce20c49ad7aab24b53ea41900b022f5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="---comment-dmx-summary"></a>-(コメント) (DMX) の概要
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、データ マイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>Remarks  
 1 行のコメントまたは入れ子にしたコメントには、この演算子を使用します。 -- を使用して挿入されたコメントは、改行文字によって区切られます。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、次を参照してください。[コメント &#40;DMX&#41;](../dmx/comments-dmx.md)です。  
  
## <a name="see-also"></a>参照  
 [スラッシュ スター &#40;です。コメント &#41;& # #40; DMX &#41;](../dmx/slash-star-comment-dmx.md)   
 [2 つのスラッシュ &#40;です。コメント &#41;& # #40; DMX &#41;](../dmx/double-slash-comment-dmx.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
