---
title: スラッシュの星 (コメント) (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5d0b929ba60915f116d9ff6843b4f20b3105a7ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942845"
---
# <a name="slash-star-comment-dmx"></a>スラッシュの星 (コメント) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  実行しないテキスト文字列[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]を示します。 サーバーでは、コメント文字/* と\*/の間のテキストは評価されません。 コメントは、データマイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の末尾に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>解説  
 複数行のコメントは、/* と \*/ で示す必要があります。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、「 [&#40;dmx&#41;](../dmx/comments-dmx.md)に関するコメント」を参照してください。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#41; &#40;スラッシュ &#40;コメント](../dmx/double-slash-comment-dmx.md)   
 [--&#40;コメント&#41; &#40;DMX&#41; の概要](../dmx/comment-dmx-summary.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
