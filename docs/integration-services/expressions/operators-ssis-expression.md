---
title: "演算子 (SSIS 式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSIS, 演算子"
  - "SQL Server Integration Services, 演算子"
  - "演算子 [Integration Services]"
  - "式 [Integration Services], 演算子"
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# 演算子 (SSIS 式)
  このセクションでは、式の言語が提供する演算子、および式エバリュエーターが使用する演算子の優先順位と結合性について説明します。  
  
 次の表に、演算子に関するこのセクションのトピックの一覧を示します。  
  
|演算子|Description|  
|--------------|-----------------|  
|[キャスト (SSIS 式)](../../integration-services/expressions/cast-ssis-expression.md)|式をあるデータ型から別のデータ型に変換します。|  
|[() (括弧) (SSIS 式)](../../integration-services/expressions/parentheses-ssis-expression.md)|式の評価順序を特定します。|  
|[+ (加算) (SSIS)](../../integration-services/expressions/add-ssis.md)|2 つの数値式を加算します。|  
|[+ (連結) (SSIS 式)](../../integration-services/expressions/concatenate-ssis-expression.md)|2 つの式を連結します。|  
|[- (減算) (SSIS 式)](../../integration-services/expressions/subtract-ssis-expression.md)|最初の数値式から 2 番目の数値式を減算します。|  
|[- (否定) (SSIS 式)](../../integration-services/expressions/negate-ssis-expression.md)|数値式を負数化します。|  
|[* (乗算) (SSIS 式)](../../integration-services/expressions/multiply-ssis-expression.md)|2 つの数値式を乗算します。|  
|[除算 (SSIS 式)](../../integration-services/expressions/divide-ssis-expression.md)|最初の数値式を 2 番目の数値式で除算します。|  
|[(剰余) (SSIS 式)](../../integration-services/expressions/modulo-ssis-expression.md)|最初の数値式を 2 番目の数値式で割った剰余を整数値で返します。|  
|[&#124;&#124; (論理 OR) (SSIS 式)](../../integration-services/expressions/logical-or-ssis-expression.md)|論理 OR 演算を実行します。|  
|[&& (論理 AND) (SSIS 式)](../../integration-services/expressions/logical-and-ssis-expression.md)|論理 AND 演算を実行します。|  
|[! (論理 Not) (SSIS 式)](../../integration-services/expressions/logical-not-ssis-expression.md)|ブール型のオペランドを否定します。|  
|[| (ビット演算子包括的 OR) (SSIS 式)](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)|2 つの整数値の OR 演算をビット単位で実行します。|  
|[^ (ビット演算子排他的 OR) (SSIS 式)](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)|2 つの整数値の排他的 OR 演算をビット単位で実行します。|  
|[& (ビット演算子 AND) (SSIS 式)](../../integration-services/expressions/bitwise-and-ssis-expression.md)|2 つの整数値の AND 演算をビット単位で実行します。|  
|[~ (ビット演算子 Not) (SSIS 式)](../../integration-services/expressions/bitwise-not-ssis-expression.md)|整数の否定のビット演算を実行します。|  
|[== (等しい) (SSIS 式)](../../integration-services/expressions/equal-ssis-expression.md)|2 つの式が等しいかどうかを判別するための比較を実行します。|  
|[!= (等しくない) (SSIS 式)](../../integration-services/expressions/unequal-ssis-expression.md)|2 つの式が等しくないかどうかを判別するための比較を実行します。|  
|[> (より大きい) (SSIS 式)](../../integration-services/expressions/greater-than-ssis-expression.md)|最初の式が 2 番目の式より大きいかどうかを判別するための比較を実行します。|  
|[&#60; (より小さい) (SSIS 式)](../../integration-services/expressions/less-than-ssis-expression.md)|最初の式が 2 番目の式未満かどうかを判別するための比較を実行します。|  
|[&#62;= (以上) (SSIS 式)](../../integration-services/expressions/greater-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以上かどうかを判別するための比較を実行します。|  
|[&#60;= (以下) (SSIS 式)](../../integration-services/expressions/less-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以下かどうかを判別するための比較を実行します。|  
|[? : (条件) (SSIS 式)](../../integration-services/expressions/conditional-ssis-expression.md)|ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。|  
  
 優先順位の階層内における各演算子の配置の詳細については、「[演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)」を参照してください。  
  
## 参照  
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)   
 [Integration Services 式の詳細の例](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Integration Services (SSIS) 式](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  