---
title: "LTRIM (SSIS 式) | Microsoft Docs"
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
  - "先頭の空白"
  - "LTRIM 関数"
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LTRIM (SSIS 式)
  先頭のスペースを削除した後の文字式を返します。  
  
> [!NOTE]  
>  LTRIM では、タブや改行文字などの空白文字は削除されません。 Unicode には各種スペースを表すコード ポイントが用意されていますが、この関数では Unicode コード ポイント 0x0020 のみが認識されます。 Unicode に変換される 2 バイト文字セット (DBCS) の文字列には、0x0020 以外のスペース文字が含まれる場合があり、このようなスペースはこの関数で削除できません。 すべての種類のスペースを削除するには、スクリプト コンポーネントから実行するスクリプト内で、Microsoft Visual Basic .NET の LTrim メソッドを使用できます。  
  
## 構文  
  
```  
  
LTRIM(character expression)  
```  
  
## 引数  
 *character_expression*  
 スペースを削除する対象となる文字式です。  
  
## 戻り値の型  
 DT_WSTR  
  
## 解説  
 LTRIM は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、LTRIM による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](../../integration-services/expressions/cast-ssis-expression.md)」を参照してください。  
  
 引数が NULL の場合、LTRIM は NULL を返します。  
  
## 式の例  
 この例では、文字列リテラルから先頭のスペースが削除されます。 返される結果は "Hello" です。  
  
```  
LTRIM("    Hello")  
```  
  
 この例では、**FirstName** 列から先頭のスペースが削除されます。  
  
```  
LTRIM(FirstName)  
```  
  
 この例では、**FirstName** 変数から先頭のスペースが削除されます。  
  
```  
LTRIM(@FirstName)  
```  
  
## 参照  
 [RTRIM &#40;SSIS 式&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [TRIM &#40;SSIS 式&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [関数 &#40;SSIS 式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  