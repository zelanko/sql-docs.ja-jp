---
title: "() (かっこ) (SSIS 式) | Microsoft Docs"
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
  - "() (かっこ演算子)"
  - "評価順序 [Integration Services]"
  - "かっこ演算子 ()"
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# () (かっこ) (SSIS 式)
  式の評価順序を特定します。 かっこで囲まれた式は、評価の優先順位が最も高くなります。 かっこで囲まれ、入れ子になっている式は、内側から外側の順に評価されます。  
  
 かっこは、複合式を理解しやすくするためにも使用されます。  
  
## 構文  
  
```  
  
(expression)  
  
```  
  
## 引数  
 *式 (expression)*  
 有効な式を指定します。  
  
## 戻り値の型  
 *expression* のデータ型。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 式の例  
 次の例では、かっこを使用して演算子の優先順位を変更する方法を示します。 最初の式は 100 と評価され、2 番目の式は 31 と評価されます。  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## 参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  