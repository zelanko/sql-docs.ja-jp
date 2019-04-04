---
title: スラッシュ アスタリスク (コメント) (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1d96c65ea1dd187d5678987447415ca419ad10d7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020750"
---
# <a name="slash-star-comment-dmx"></a>スラッシュ アスタリスク (コメント) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は実行されません。 コメント文字の間のテキストを評価しませんサーバー/* と\*/。 コメントは、データ マイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>コメント  
 複数行のコメントは、/* と \*/ で示す必要があります。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、[コメント&#40;DMX&#41;](../dmx/comments-dmx.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [2 つのスラッシュ&#40;コメント&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)   
 [--&#40;コメント&#41; &#40;DMX&#41;の概要](../dmx/comment-dmx-summary.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
