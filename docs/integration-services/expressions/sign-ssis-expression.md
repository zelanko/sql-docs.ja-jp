---
title: "SIGN (SSIS 式) | Microsoft Docs"
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
  - "正の値 [Integration Services]"
  - "SIGN 関数"
  - "負の値"
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# SIGN (SSIS 式)
  数値式の符号として正 (+1)、負 (-1)、0 のいずれかを返します。  
  
## 構文  
  
```  
  
SIGN(numeric_expression)  
```  
  
## 引数  
 *numeric_expression*  
 有効な符号付き数値式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 戻り値の型  
 DT_I4  
  
## 解説  
 引数が NULL の場合、SIGN は NULL を返します。  
  
## 式の例  
 この例では、数値リテラルの符号を返します。 返される結果は -1 です。  
  
```  
SIGN(-123.45)  
```  
  
 この例では、**StandardCost** 列を **DealerPrice** 列から減算した結果の符号を返します。  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## 参照  
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  