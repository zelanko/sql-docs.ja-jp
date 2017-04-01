---
title: "EXP (SSIS 式) | Microsoft Docs"
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
  - "指数関数"
  - "EXP 関数"
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# EXP (SSIS 式)
  数値式の e を基数とする指数を返します。 EXP 関数は LN 関数の逆関数であり、真数と呼ばれる場合もあります。  
  
## 構文  
  
```  
  
EXP(numeric_expression)  
```  
  
## 引数  
 *numeric_expression*  
 有効な数値式です。  
  
## 戻り値の型  
 DT_R8  
  
## 解説  
 数値式は、指数の計算前に DT_R8 データ型にキャストされます。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
 返される結果は、常に正の数値です。  
  
## 式の例  
 この例では、正の値、負の値、および 0 に、EXP 関数を適用します。  
  
```  
EXP(74)  
```  
  
 1.373382979540176E+32 が返されます。  
  
```  
EXP(-27)  
```  
  
 1.879528816539083E-12 が返されます。  
  
```  
EXP(0)  
```  
  
 1 が返されます。  
  
## 参照  
 [LOG (SSIS 式)](../../integration-services/expressions/log-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  