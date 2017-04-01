---
title: "FLOOR (SSIS 式) | Microsoft Docs"
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
  - "式以下の最大の整数"
  - "FLOOR 関数 [SSIS]"
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# FLOOR (SSIS 式)
  数値式以下で最大の整数を返します。  
  
## 構文  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## 引数  
 *numeric_expression*  
 有効な数値式です。  
  
## 戻り値の型  
 引数の式の数値データ型です。 結果は、*numeric_expression*と同じデータ型の、計算値の整数部分になります。  
  
## 解説  
 引数が NULL の場合、FLOOR は NULL を返します。  
  
## 式の例  
 次の例では、正の値、負の値、および 0 に FLOOR 関数を適用します。  
  
```  
FLOOR(123.45)  
```  
  
 123.00 を返します  
  
```  
FLOOR(-123.45)  
```  
  
 -124.00 を返します  
  
```  
FLOOR(0.00)  
```  
  
 0.00 を返します。  
  
## 参照  
 [CEILING (SSIS 式)](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  