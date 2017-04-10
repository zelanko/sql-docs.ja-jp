---
title: "CODEPOINT (SSIS 式) | Microsoft Docs"
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
  - "CODEPOINT 関数"
  - "左端の文字、式"
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# CODEPOINT (SSIS 式)
  文字式の一番左の文字の Unicode コード ポイントを返します。  
  
## 構文  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## 引数  
 *character_expression*  
 一番左の文字を評価する文字式です。  
  
## 戻り値の型  
 DT_UI2  
  
## 解説  
 *character_expression* は、DT_WSTR データ型である必要があります。  
  
 *character_expression* が NULL または空の文字列の場合、CODEPOINT は NULL を返します。  
  
## 式の例  
 この例では、文字列リテラルを使用します。 返される結果は 77 で、Unicode コード ポイントは M です。  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 この例では、変数を使用します。 **Name** が Touring Front Wheel の場合、返される結果は 84 で、Unicode コード ポイントは T です。  
  
```  
CODEPOINT(@Name)  
```  
  
## 参照  
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  