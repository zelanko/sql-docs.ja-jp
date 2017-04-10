---
title: "| (ビット演算包含的 OR) (SSIS 式) | Microsoft Docs"
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
  - "| (ビット演算包含的 OR)"
  - "ビット演算包含的 OR (|)"
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# | (ビット演算包含的 OR) (SSIS 式)
  2 つの整数値の OR 演算をビット単位で実行します。 最初のオペランドの各ビットを 2 番目のオペランドの対応するビットと比較します。 いずれかのビットが 1 の場合、対応する結果ビットは 1 に設定されます。 それ以外の場合、対応する結果ビットはゼロ (0) に設定されます。  
  
 どちらの条件も符号付き整数データ型か、または、どちらの条件も符号なし整数データ型である必要があります。  
  
## 構文  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## 引数  
 *integer_expression1 ,integer_ expression2*  
 符号付きまたは符号なし整数データ型の任意の有効な式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 戻り値の型  
 2 つの引数のデータ型によって決まります。 詳細については、「[式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」を参照してください。  
  
## 解説  
 条件のいずれかが NULL の場合、式の結果は NULL になります。  
  
## 式の例  
 この例では、変数 **NumberA** と **NumberB** 間で包含的 OR 演算をビット単位で実行します。 **NumberA** には 3 (00000011) が、**NumberB** には 9 (00001001) が含まれます。  
  
```  
@NumberA | @NumberB  
```  
  
 式は 11 (00001011) に評価されます。  
  
 00000011  
  
 00001001  
  
 ----------\-  
  
 00001011  
  
 この例では、**ReorderPoint** 列と **SafetyStockLevel** 列の間でビット演算子包含的 OR を実行します。  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 **ReorderPoint** が 10 で **SafetyStockLevel** が 8 の場合、式は 10 (00001010) に評価されます。  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001010  
  
 この例では、2 つの整数間の包含的 OR 演算をビット単位で実行します。  
  
```  
3 | 5   
```  
  
 式は 7 (00001011) に評価されます。  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000111  
  
## 参照  
 [&#124;&#124; (論理 OR) (SSIS 式)](../../integration-services/expressions/logical-or-ssis-expression.md)   
 [^ (ビット演算子排他的 OR) (SSIS 式)](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  