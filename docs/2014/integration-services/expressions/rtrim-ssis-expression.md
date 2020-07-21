---
title: RTRIM (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1f42da39dfeea3e135e2f7b432c0f4009c08c4a0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428189"
---
# <a name="rtrim-ssis-expression"></a>RTRIM (SSIS 式)
  末尾のスペースを削除した後の文字式を返します。  
  
> [!NOTE]  
>  RTRIM では、タブや改行文字などの空白文字は削除されません。 Unicode には各種スペースを表すコード ポイントが用意されていますが、この関数では Unicode コード ポイント 0x0020 のみが認識されます。 Unicode に変換される 2 バイト文字セット (DBCS) の文字列には、0x0020 以外のスペース文字が含まれる場合があり、このようなスペースはこの関数で削除できません。 すべての種類のスペースを削除するには、スクリプト コンポーネントから実行するスクリプト内で、Microsoft Visual Basic .NET の RTrim メソッドを使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 スペースを削除する対象となる文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>解説  
 RTRIM は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、RTRIM による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。  
  
 引数が NULL の場合、RTRIM は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
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
  
## <a name="see-also"></a>参照  
 [LTRIM (SSIS 式)](trim-ssis-expression.md)   
 [TRIM &#40;SSIS 式&#41;](trim-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
