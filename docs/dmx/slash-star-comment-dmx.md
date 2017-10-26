---
title: "Star (コメント) (DMX) をスラッシュ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- commenting characters
- forward slash-asterisk character pairs
- /*...*/ (comment)
ms.assetid: 163976cc-aa47-4eda-bd98-03c1a397f80e
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5bfaadd08f5a9aba145c754f281cf1d2c8e38496
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="slash-star-comment-dmx"></a>スラッシュ スター (コメント) (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 サーバーが、コメント文字の間のテキストを評価できません/* と\*/です。 コメントは、データ マイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>解説  
 によって複数行のコメントを示す必要があります/* と\*/です。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、次を参照してください。[コメント (&) #40";"DMX"&"#41;](../dmx/comments-dmx.md)です。  
  
## <a name="see-also"></a>参照  
 [2 つのスラッシュ & #40 です。コメント &#41;& # #40; DMX &#41;](../dmx/double-slash-comment-dmx.md)   
 [--& #40 です。コメント &#41;& # #40; DMX &#41;概要](../dmx/comment-dmx-summary.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子 (&) #40";"DMX"&"#41;](../dmx/operators-dmx.md)  
  
  

