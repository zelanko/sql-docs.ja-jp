---
title: CustomData (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- EXISTS
dev_langs:
- kbMDX
helpviewer_keywords:
- Exists function
ms.assetid: 61d9f5a2-6f56-4179-a39b-317c8e0a2cdd
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 717d8aa2aea972cf1193f279d3bf2b6283a9657e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="customdata-mdx"></a>CustomData (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  値を返します、 **CustomData**定義されている、それ以外の場合、接続文字列プロパティ**null**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>戻り値  
 **CustomData**関数を取得できます、 **CustomData**接続文字列プロパティと、構成など、多次元式 (MDX) 関数およびステートメントで使用する設定を渡す[UserName (MDX)](../mdx/username-mdx.md)と[CALL ステートメント (MDX)](../mdx/mdx-data-manipulation-call.md)です。 たとえば、この関数で指定できますを動的セキュリティ式内の文字列値の許可/拒否されたセット メンバーを選択する、 **CustomData**接続文字列プロパティです。  
  
## <a name="example"></a>例  
 次のクエリによって返される値を表示する、 **CustomData**計算されるメジャー内の関数。  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
