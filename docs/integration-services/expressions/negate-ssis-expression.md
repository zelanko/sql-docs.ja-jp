---
title: "- (負数化) (SSIS 式) | Microsoft Docs"
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
  - "- (負号)"
  - "負号演算子 (-)"
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# - (負数化) (SSIS 式)
  数値式を負数化します。  
  
## 構文  
  
```  
  
-numeric_expression  
  
```  
  
## 引数  
 *numeric_expression*  
 任意の数値データ型の有効な式です。 サポートされるデータ型は、符号付き数値データ型のみです。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 戻り値の型  
 データ型を返す *numeric_expression* です。  
  
## 式の例  
 この例では、変数 **Counter** の値を負数化して、数値リテラル 50 を加算します。  
  
```  
-@Counter + 50  
```  
  
## 参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  