---
title: スラッシュの星 (コメント) (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b3186c0646ad54fc0632f8b023dcd448cebd1ee9
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670039"
---
# <a name="slash-star-comment-dmx"></a>スラッシュの星 (コメント) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  実行しないテキスト文字列を示し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。 サーバーでは、コメント文字/* と/の間のテキストは評価されません \* 。 コメントは、データマイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の末尾に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>Remarks  
 複数行のコメントは、/* と \*/ で示す必要があります。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、「 [&#40;dmx&#41;](../dmx/comments-dmx.md)に関するコメント」を参照してください。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#41; &#40;スラッシュ &#40;コメント](../dmx/double-slash-comment-dmx.md)   
 [--&#40;コメント&#41; &#40;DMX&#41; の概要](../dmx/comment-dmx-summary.md)   
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
