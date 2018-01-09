---
title: "StrToValue (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: STRTOVALUE
dev_langs: kbMDX
helpviewer_keywords: StrToValue function
ms.assetid: 118a9c4f-74a3-48d5-a4f4-318664bc51bc
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37424120aee0b38303b086019e2fb74a823cdc1b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 形式の文字列によって指定されている数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *MDX_Expression*  
 直接的または間接的に 1 つのセルに解決される有効な文字列式です。  
  
## <a name="remarks"></a>Remarks  
 **StrToValue**関数は、MDX 式によって指定された数値を返します。 **StrToValue**関数は、通常使用ユーザー定義関数を 1 つのセルに解決される MDX ステートメントを外部関数から MDX 式を返します。  
  
-   CONSTRAINED フラグを使用する場合、MDX 式にはスカラー値のみを含める必要があります。 CONSTRAINED フラグは、指定された文字列によるインジェクション攻撃の危険性を軽減するために使用します。 直接スカラー値に解決できない MDX 式を指定すると、"STRTOVALUE 関数の CONSTRAINED フラグによって設定された制限に違反しました。" というエラー メッセージが表示されます。  
  
-   CONSTRAINED フラグを使用しない場合は、1 つのセルを返す有効な多次元式 (MDX) 式に解決される範囲で複雑な MDX 式を指定できます。  
  
> [!NOTE]  
>  MDX 式の結果がテキストとして格納されていても、その値を数値として返すと、返された値に対して算術演算を実行する場合に便利です。  
  
## <a name="example"></a>例  
 次の例では、 **StrToValue**値としては、各自転車の重量を返す関数。  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
