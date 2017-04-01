---
title: "ABS (SSIS 式) | Microsoft Docs"
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
  - "ABS 関数"
  - "絶対値、正"
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ABS (SSIS 式)
  数値式の正の絶対値を返します。  
  
## 構文  
  
```  
  
ABS(numeric_expression)  
```  
  
## 引数  
 *numeric_expression*  
 符号付きまたは符号なしの数値式です。  
  
## 戻り値の型  
 関数に送信された数値式のデータ型です。  
  
## 解説  
 引数が NULL の場合、ABS は NULL を返します。  
  
## 式の例  
 次の例では、正の数および負の数に ABS 関数を適用します。 どちらも 1.23 を返します。  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 この例では、変数 **HighTemperature** および **LowTempature**の値を減算する式に対して ABS 関数を適用します。  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## 参照  
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  