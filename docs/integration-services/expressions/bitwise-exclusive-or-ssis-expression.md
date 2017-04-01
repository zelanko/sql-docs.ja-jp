---
title: "^ (ビット演算排他的 OR) (SSIS 式) | Microsoft Docs"
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
  - "^ (ビットごとの排他的 OR 演算子)"
  - "ビットごとの排他的 OR (^)"
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# ^ (ビット演算排他的 OR) (SSIS 式)
  2 つの整数値の排他的 OR 演算をビット単位で実行します。 最初のオペランドの各ビットを 2 番目のオペランドの対応するビットと比較します。 一方のビットが 0 でもう一方のビットが 1 の場合、対応する結果ビットは 1 に設定されます。 両方のビットが 0、また両方のビットが 1 の場合、対応する結果ビットは 0 に設定されます。  
  
 どちらの条件も符号付き整数データ型か、または、どちらの条件も符号なし整数データ型である必要があります。  
  
## 構文  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## 引数  
 *integer_expression1、integer_ expression2*  
 符号付きまたは符号なし整数データ型の任意の有効な式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 戻り値の型  
 2 つの引数のデータ型によって決まります。 詳細については、「[式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」を参照してください。  
  
## 解説  
 条件のいずれかが NULL の場合、式の結果は NULL になります。  
  
## 式の例  
 この例では、変数 **NumberA** と **NumberB** 間の排他的 OR 演算をビット単位で実行します。 **NumberA** には 3 (00000011) が、**NumberB** には 7 (00000111) が含まれます。  
  
```  
@NumberA ^ @NumberB  
```  
  
 式は 4 (00000100) に評価されます。  
  
 00000011  
  
 00000111  
  
 ----------\-  
  
 00000100  
  
 この例では、**ReorderPoint** 列と **SafetyStockLevel** 列の間の排他的 OR 演算をビット単位で実行します。  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 **ReorderPoint** が 10 で **SafetyStockLevel** が 8 の場合、式は 2 (00000010) に評価されます。  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00000010  
  
 この例では、2 つの整数間の排他的 OR 演算をビット単位で実行します。  
  
```  
3 ^ 5   
```  
  
 式は 6 (00000110) に評価されます。  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000110  
  
## 参照  
 [&#124;&#124; (論理 OR) (SSIS 式)](../../integration-services/expressions/logical-or-ssis-expression.md)   
 [&#124; (ビット演算包含的 OR) (SSIS 式)](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  