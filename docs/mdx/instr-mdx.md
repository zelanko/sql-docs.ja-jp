---
title: "Instr (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5638c358-47da-40ad-b988-1a5214c05492
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 59c741dbecfb75b370bf2cc4ce103f00b695345d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="instr-mdx"></a>Instr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つ目の文字列の、2 つ目の文字列内での最初の出現位置を返します。  
  
## <a name="syntax"></a>構文  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>引数  
 *開始*  
 (省略可) 各検索の開始位置を設定する数値式。 この値が省略された場合、検索は最初の文字位置から開始します。 start が null の場合、関数の戻り値は未定義となります。  
  
 *searched_string*  
 検索する文字列式を指定します。  
  
 *search_string*  
 検索するのには、文字列式です。  
  
 *比較*  
 (省略可) 整数値です。 この引数は常に無視されます。 その他の互換性に定義されている**Instr**他の言語の関数。  
  
## <a name="return-value"></a>戻り値  
 開始位置を表す整数値*String2*で*String1*です。  
  
 また、 **InStr**関数、条件に応じて次の表に示す値を返します。  
  
|条件|戻り値|  
|---------------|------------------|  
|String1 の長さが 0|ゼロ (0)|  
|String1 が NULL|未定義|  
|String2 の長さが 0|start|  
|String2 が NULL|未定義|  
|String2 が見つからない|ゼロ (0)|  
|start が Len(String2) よりも大きい|ゼロ (0)|  
  
## <a name="remarks"></a>解説  
  
> [!WARNING]  
>  **Instr**常に大文字と小文字を実行します。  
  
## <a name="example"></a>例  
 次の例の使用方法を示しています、 **Instr**関数とは異なる結果を返すシナリオです。  
  
```  
with   
    member [Date].[Date].[Results] as "Results"  
    member measures.[lowercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[uppercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "O")  
    member measures.[searched string is empty]            as InStr( "", "o")  
    member measures.[searched string is null]             as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[search string is empty]              as InStr( "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is empty start 10]     as InStr(10, "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is null]               as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[found from start 10]                 as InStr( 10, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NOT found from start 17]             as InStr( 17, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NULL start]                          as iif(IsError(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Error", iif(IsNull(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Null","Is undefined"))  
    member measures.[start greater than searched length]  as InStr( 170, "abcdefghijklmnñopqrstuvwxyz", "o")  
  
select  [Results] on columns,  
       { measures.[lowercase found in lowercase string]  
       , measures.[uppercase found in lowercase string]  
       , measures.[searched string is empty]  
       , measures.[searched string is null]  
       , measures.[search string is empty]  
       , measures.[search string is empty start 10]  
       , measures.[search string is null]  
       , measures.[found from start 10]  
       , measures.[NOT found from start 17]  
       , measures.[NULL start]   
       , measures.[start greater than searched length]  
       } on rows  
  
from [Adventure Works]  
```  
  
 取得した結果を次の表に示します。  
  
|||  
|-|-|  
||[結果]|  
|小文字の文字列で小文字を検索|16|  
|小文字文字列で大文字を検索|16|  
|検索した文字列が空|0|  
|検索した文字列が NULL|未定義|  
|検索する文字列が空|1|  
|検索する文字列が開始位置 10 から空|10|  
|検索する文字列が NULL|未定義|  
|開始位置 10 から検索|16|  
|開始位置 17 から検索されない|0|  
|NULL で開始|未定義|  
|検索した長さを超えて開始|0|  
  
  

