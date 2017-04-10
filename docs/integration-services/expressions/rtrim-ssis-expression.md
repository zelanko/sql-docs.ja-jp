---
title: "RTRIM (SSIS 式) | Microsoft Docs"
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
  - "RTRIM 関数"
  - "末尾の空白"
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# RTRIM (SSIS 式)
  末尾のスペースを削除した後の文字式を返します。  
  
> [!NOTE]  
>  RTRIM では、タブや改行文字などの空白文字は削除されません。 Unicode には各種スペースを表すコード ポイントが用意されていますが、この関数では Unicode コード ポイント 0x0020 のみが認識されます。 Unicode に変換される 2 バイト文字セット (DBCS) の文字列には、0x0020 以外のスペース文字が含まれる場合があり、このようなスペースはこの関数で削除できません。 すべての種類のスペースを削除するには、スクリプト コンポーネントから実行するスクリプト内で、Microsoft Visual Basic .NET の RTrim メソッドを使用できます。  
  
## 構文  
  
```  
  
RTRIM(character expression)  
```  
  
## 引数  
 *character_expression*  
 スペースを削除する対象となる文字式です。  
  
## 戻り値の型  
 DT_WSTR  
  
## 解説  
 RTRIM は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、RTRIM による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」 および「[Cast (SSIS 式)](../../integration-services/expressions/cast-ssis-expression.md)」 を参照してください。  
  
 引数が NULL の場合、RTRIM は NULL を返します。  
  
## 式の例  
 この例では、文字列リテラルから末尾のスペースが削除されます。 返される結果は "Hello" です。  
  
```  
RTRIM("Hello   ")  
```  
  
 この例では、 **FirstName** 列と **LastName** 列の連結列から、末尾のスペースが削除されます。  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 この例では、 **FirstName** 変数から末尾のスペースが削除されます。  
  
```  
RTRIM(@FirstName)  
```  
  
## 参照  
 [LTRIM (SSIS 式)](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [TRIM (SSIS 式)](../../integration-services/expressions/trim-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  