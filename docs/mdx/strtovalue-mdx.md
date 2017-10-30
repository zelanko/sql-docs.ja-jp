---
title: "StrToValue (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRTOVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToValue function
ms.assetid: 118a9c4f-74a3-48d5-a4f4-318664bc51bc
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9db77d7e3d4721337ccbeb397d6cb7382209f027
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  多次元式 (MDX) 形式の文字列によって指定されている数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *MDX_Expression*  
 直接的または間接的に 1 つのセルに解決される有効な文字列式です。  
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

