---
title: "LEFT (SSIS 式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# LEFT (SSIS 式)
  指定された文字式の一番左の部分から指定された数の文字を返します。  
  
## 構文  
  
```  
  
LEFT(character_expression,number)  
```  
  
## 引数  
 *character_expression*  
 文字の抽出元となる文字式です。  
  
 *number*  
 返す文字の数を示す整数式です。  
  
## 戻り値の型  
 DT_WSTR  
  
## 解説  
 *number* が *character_expression* より長い場合、関数は *character_expression* を返します。  
  
 *number* が 0 の場合、関数は長さが 0 の文字列を返します。  
  
 *number* が負の値の場合、関数はエラーを返します。  
  
 *number* 引数には、変数および列を使用できます。  
  
 LEFT は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LEFT による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」 および「[Cast (SSIS 式)](../../integration-services/expressions/cast-ssis-expression.md)」 を参照してください。  
  
 引数のいずれかが NULL の場合、LEFT は NULL を返します。  
  
## 式の例  
 次の例では、文字列リテラルを使用します。 返される結果は `"Mountain"` です。  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## 参照  
 [RIGHT (SSIS 式)](../../integration-services/expressions/right-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  