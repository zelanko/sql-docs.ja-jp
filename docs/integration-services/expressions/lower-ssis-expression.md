---
title: "LOWER (SSIS 式) | Microsoft Docs"
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
  - "大文字を小文字に変換"
  - "LOWER 関数"
  - "大文字 [Integration Services]"
  - "小文字"
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LOWER (SSIS 式)
  大文字が小文字に変換された状態の文字式を返します。  
  
## 構文  
  
```  
  
LOWER(character_expression)  
```  
  
## 引数  
 *character_expression*  
 小文字に変換する文字式です。  
  
## 戻り値の型  
 DT_WSTR  
  
## 解説  
 LOWER は DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LOWER による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」 および「[Cast (SSIS 式)](../../integration-services/expressions/cast-ssis-expression.md)」 を参照してください。  
  
 引数が NULL の場合、LOWER は NULL を返します。  
  
## 式の例  
 この例では、文字列リテラルを小文字に変換します。 返される結果は "new york" です。  
  
```  
LOWER("New York")  
```  
  
 この例では、**Color** 入力列の最初の文字を除くすべての文字を小文字に変換します。 Color が YELLOW の場合、返される結果は "Yellow" です。 詳細については、「[SUBSTRING (SSIS 式)](../../integration-services/expressions/substring-ssis-expression.md)」を参照してください。  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 この例では、**CityName** 変数の値を小文字に変換します。  
  
```  
LOWER(@CityName)  
```  
  
## 参照  
 [UPPER (SSIS 式)](../../integration-services/expressions/upper-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  