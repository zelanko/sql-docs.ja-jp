---
title: "UPPER (SSIS 式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1764b39b0242ce7e23d56c9c74f7b953f45009b2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="upper-ssis-expression"></a>UPPER (SSIS 式)
  小文字が大文字に変換された状態の文字式を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 大文字に変換する対象となる文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>解説  
 UPPER は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、UPPER による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](../../integration-services/expressions/cast-ssis-expression.md)」を参照してください。  
  
 引数が NULL の場合、UPPER は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、文字列リテラルを大文字に変換します。 返される結果は "HELLO" です。  
  
```  
UPPER("hello")  
```  
  
 この例では、 **FirstName** 列の最初の文字を大文字に変換します。 **FirstName** が anna の場合、返される結果は "A" です。 詳細については、「[SUBSTRING &#40;SSIS 式&#41;](../../integration-services/expressions/substring-ssis-expression.md)」を参照してください。  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 この例では、**PostalCode** 変数の値を大文字に変換します。 **PostalCode** が k4b1s2 の場合、返される結果は "K4B1S2" です。  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a>参照  
 [低 &#40; です。SSIS 式と &#41; です。](../../integration-services/expressions/lower-ssis-expression.md)   
 [関数と &#40; です。SSIS 式と &#41; です。](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

