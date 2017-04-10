---
title: "~ (ビット演算 Not) (SSIS 式) | Microsoft Docs"
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
  - "ビット演算子 NOT (~)"
  - "~ (ビット演算子 NOT)"
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# ~ (ビット演算 Not) (SSIS 式)
  整数の否定のビット演算を実行します。 この演算子は、符号付きおよび符号なし整数データ型に適用できます。  
  
## 構文  
  
```  
  
~integer_expression  
  
```  
  
## 引数  
 *integer_expression*  
 整数データ型の任意の有効な式を指定します。 *integer*_*expression* は整数で、ビット演算用に 2 進数に変換されます。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 戻り値の型  
 データ型を返す *integer_expression* です。  
  
## 解説  
 なし  
  
## 式の例  
 この例では、数値 170 (0000 0000 1010 1010) に対し、ビット演算 ~ (NOT) を実行します。 この数値は符号付き整数です。  
  
```  
  
~ 170  
```  
  
 式は -170 (1111111101010101) に評価されます。  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## 参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  