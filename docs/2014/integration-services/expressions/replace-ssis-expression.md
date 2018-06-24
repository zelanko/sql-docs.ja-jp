---
title: REPLACE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7888b72ed7193a1c2910db06a70496ee30761903
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074423"
---
# <a name="replace-ssis-expression"></a>REPLACE (SSIS 式)
  式に含まれている文字列を別の文字列または空の文字列で置き換えた文字式を返します。  
  
> [!NOTE]  
>  REPLACE 関数では、長い文字列が頻繁に使用されます。 切り捨ての結果を効率よく処理できる場合もあれば、結果により警告またはエラーが発生する場合もあります。 詳しくは、「[構文 &#40;SSIS&#41;](syntax-ssis.md)」をご覧ください。  
  
## <a name="syntax"></a>構文  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 検索対象となる有効な文字式です。  
  
 *searchstring*  
 関数により検索される有効な文字式です。  
  
 *replacementstring*  
 置換後の式となる有効な文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>コメント  
 *searchstring* の長さを 0 にすることはできません。  
  
 *replacementstring* の長さは 0 にすることができます。  
  
 *searchstring* 引数および *replacementstring* 引数には、変数と列を使用できます。  
  
 REPLACE は、DT_WSTR データ型でのみ機能します。 *character_expression1、character_expression2* 、および *character_expression3* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、REPLACE による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳細については、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。  
  
 いずれかの引数が NULL の場合、REPLACE は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、文字列リテラルを使用します。 返される結果は "All Terrain Bike" です。  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 この例では、 **Product** 列から文字列 "Bike" を削除します。  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 この例では、 **DaysToManufacture** 列の値を置換します。 **DaysToManufacture** 列は整数データ型で、式の内部で DT_WSTR データ型にキャストされます。  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>参照  
 [部分文字列&#40;SSIS 式&#41;](substring-ssis-expression.md)   
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  