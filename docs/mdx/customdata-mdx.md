---
title: CustomData (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 172915d99b231490cbdca24f70d1d38da27a1d3d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248321"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  値を返します、 **CustomData**定義。 それ以外の場合、接続文字列プロパティ**null**します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>戻り値  
 **CustomData**関数を取得できます、 **CustomData**接続文字列プロパティと構成など、多次元式 (MDX) 関数およびステートメントで使用される設定を渡す[UserName (MDX)](../mdx/username-mdx.md)と[CALL ステートメント (MDX)](../mdx/mdx-data-manipulation-call.md)します。 内の文字列値の許可または拒否されたセット メンバーを選択するこの関数を動的セキュリティ式で使用するなど、 **CustomData**接続文字列プロパティ。  
  
## <a name="example"></a>例  
 次のクエリによって返される値が表示されます、 **CustomData**計算されるメジャー内の関数。  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
