---
title: --(コメント) (DMX) Summary |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 71e6c616cef5a2f4945a1335e1297aa3ad3a2ce4
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669377"
---
# <a name="---comment-dmx-summary"></a>--(コメント) (DMX) の概要
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  実行しないテキスト文字列を示し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。 コメントは、データマイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の末尾に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>Remarks  
 この演算子は、単一行または入れ子になったコメントに使用します。 --を使用して挿入されたコメントは、改行文字で区切られます。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、「 [&#40;dmx&#41;](../dmx/comments-dmx.md)に関するコメント」を参照してください。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#41; &#40;スラッシュの星 &#40;コメント](../dmx/slash-star-comment-dmx.md)   
 [DMX&#41;&#41; &#40;スラッシュ &#40;コメント](../dmx/double-slash-comment-dmx.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
