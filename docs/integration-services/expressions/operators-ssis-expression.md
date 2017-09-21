---
title: "演算子 (SSIS 式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ab52310bc72b0288369ed10bccfbf0b58e6c6ee4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="operators-ssis-expression"></a>演算子 (SSIS 式)
  このセクションでは、式の言語が提供する演算子、および式エバリュエーターが使用する演算子の優先順位と結合性について説明します。  
  
 次の表に、演算子に関するこのセクションのトピックの一覧を示します。  
  
|演算子|Description|  
|--------------|-----------------|  
|[キャストと #40 です。SSIS 式 &#41;](../../integration-services/expressions/cast-ssis-expression.md)|式をあるデータ型から別のデータ型に変換します。|  
|[& # #40; &#41;& #40 です。かっこ"&"#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/parentheses-ssis-expression.md)|式の評価順序を特定します。|  
|[+ (& a) #40 です。追加 (& a) #41;& #40 です。SSIS &#41;](../../integration-services/expressions/add-ssis.md)|2 つの数値式を加算します。|  
|[+ (& a) #40 です。連結 &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/concatenate-ssis-expression.md)|2 つの式を連結します。|  
|[-(& a) #40 です。減算 (& a) #41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/subtract-ssis-expression.md)|最初の数値式から 2 番目の数値式を減算します。|  
|[-(& a) #40 です。Negate &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/negate-ssis-expression.md)|数値式を負数化します。|  
|[& #42 です。& #40 です。乗算 (& a) #41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/multiply-ssis-expression.md)|2 つの数値式を乗算します。|  
|[除算 & #40 です。SSIS 式 &#41;](../../integration-services/expressions/divide-ssis-expression.md)|最初の数値式を 2 番目の数値式で除算します。|  
|[& #40 です。剰余 (& a) #41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/modulo-ssis-expression.md)|最初の数値式を 2 番目の数値式で割った剰余を整数値で返します。|  
|[&#124; & #124 です。& #40 です。論理 OR &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/logical-or-ssis-expression.md)|論理 OR 演算を実行します。|  
|[& & & #40 です。論理 AND &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/logical-and-ssis-expression.md)|論理 AND 演算を実行します。|  
|[!& #40 です。論理 Not &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/logical-not-ssis-expression.md)|ブール型のオペランドを否定します。|  
|[&#124;です &#40;です。ビット演算子包含的 OR&#41; &#40です。SSIS 式&#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)|2 つの整数値の OR 演算をビット単位で実行します。|  
|[^ (& a) #40 です。ビットごとの排他的 OR &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)|2 つの整数値の排他的 OR 演算をビット単位で実行します。|  
|[& & #40 です。ビットごとの AND &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/bitwise-and-ssis-expression.md)|2 つの整数値の AND 演算をビット単位で実行します。|  
|[~ & #40 です。ビットごとの Not &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/bitwise-not-ssis-expression.md)|整数の否定のビット演算を実行します。|  
|[= = (& a) #40 です。等しいと #41 です。& #40 です。SSIS 式 &#41;](../../integration-services/expressions/equal-ssis-expression.md)|2 つの式が等しいかどうかを判別するための比較を実行します。|  
|[! = (& a) #40 です。等しくない"&"#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/unequal-ssis-expression.md)|2 つの式が等しくないかどうかを判別するための比較を実行します。|  
|[& #62 です。& #40 です。大きい (& a) #41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/greater-than-ssis-expression.md)|最初の式が 2 番目の式より大きいかどうかを判別するための比較を実行します。|  
|[(& m); 60& #40 です。小さい (& a) #41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/less-than-ssis-expression.md)|最初の式が 2 番目の式未満かどうかを判別するための比較を実行します。|  
|[&#62; = (& a) #40 です。大きいまたは等しい &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/greater-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以上かどうかを判別するための比較を実行します。|  
|[(& m); 60 = (& a) #40 です。以下に &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/less-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以下かどうかを判別するための比較を実行します。|  
|[?: & #40 です。条件付き &#41;& #40 です。SSIS 式 &#41;](../../integration-services/expressions/conditional-ssis-expression.md)|ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。|  
  
 優先順位の階層内における各演算子の配置の詳細については、「 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数と #40 です。SSIS 式 &#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [高度な Integration Services 式の例](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Integration Services & #40 です。SSIS &#41;式](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
