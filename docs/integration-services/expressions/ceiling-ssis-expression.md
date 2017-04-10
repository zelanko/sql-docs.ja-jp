---
title: "CEILING (SSIS 式) | Microsoft Docs"
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
  - "最小の整数、式の結果以上"
  - "CEILING 関数 [SSIS]"
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# CEILING (SSIS 式)
  数値式以上で最小の整数値を返します。  
  
## 構文  
  
```  
  
CEILING(numeric_expression)  
```  
  
## 引数  
 *numeric_expression*  
 有効な数値式です。  
  
## 戻り値の型  
 関数に送信された数値式のデータ型です。  
  
## 解説  
 引数が NULL の場合、CEILING は NULL を返します。  
  
## 式の例  
 この例では、正の値、負の値、および 0 に CEILING 関数を適用します。  
  
```  
CEILING(123.74)  
```  
  
 124.00 を返します。  
  
```  
CEILING(-124.27)  
```  
  
 -124.00 を返します。  
  
```  
CEILING(0.00)  
```  
  
 0.00 を返します。  
  
## 参照  
 [FLOOR &#40;SSIS 式&#41;](../../integration-services/expressions/floor-ssis-expression.md)   
 [関数 &#40;SSIS 式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  