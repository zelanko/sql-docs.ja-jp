---
title: "ISNULL (SSIS 式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NULL 値 [Integration Services]"
  - "ISNULL 関数"
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ISNULL (SSIS 式)
  式が NULL かどうかに基づいてブール型の結果を返します。  
  
## 構文  
  
```  
  
ISNULL(expression)  
```  
  
## 引数  
 *式 (expression)*  
 任意のデータ型の有効な式です。  
  
## 戻り値の型  
 DT_BOOL  
  
## 式の例  
 この例では、 **DiscontinuedDate** 列に NULL 値が含まれる場合、TRUE を返します。  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 この例では、 **LastName** 列の値が NULL の場合、"Unknown last name" を返し、NULL でない場合は **LastName**の値を返します。  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 この例では、変数 **AddDays** の値に関係なく、 **DaysToManufacture**列が NULL の場合は常に TRUE を返します。  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## 参照  
 [関数 &#40;SSIS 式&#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  