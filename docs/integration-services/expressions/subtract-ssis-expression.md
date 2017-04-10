---
title: "- (減算) (SSIS 式) | Microsoft Docs"
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
  - "- (減算)"
  - "減算演算子 (-)"
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# - (減算) (SSIS 式)
  最初の数値式から 2 番目の数値式を減算します。  
  
## 構文  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## 引数  
 *numeric_expression1、numeric_expression2*  
 数値データ型の有効な式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 戻り値の型  
 2 つの引数のデータ型によって決まります。 詳細については、「[式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」を参照してください。  
  
## 解説  
 式が正しい順序で評価されるようにするために、マイナス単項式はかっこで囲みます。  
  
## 解説  
 オペランドのいずれかが NULL の場合、結果は NULL になります。  
  
## 式の例  
 この例では、数値リテラルを減算します。  
  
```  
5 - 6.09  
```  
  
 この例では、**ListPrice** 列の値から **StandardCost** 列の値を減算します。  
  
```  
ListPrice - StandardCost  
```  
  
 この例では、計算した値を **ListPrice** 列から減算します。 変数 **Discount%** は、名前に % 文字が含まれているため、角かっこで囲む必要があります。 詳細については、「[識別子 &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md)」を参照してください。  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## 参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  