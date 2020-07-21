---
title: 演算子 (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2851d5b0f8681b46a8c5b4efc714620fa5cd64f0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428309"
---
# <a name="operators-ssis-expression"></a>演算子 (SSIS 式)
  このセクションでは、式の言語が提供する演算子、および式エバリュエーターが使用する演算子の優先順位と結合性について説明します。  
  
 次の表に、演算子に関するこのセクションのトピックの一覧を示します。  
  
|演算子|説明|  
|--------------|-----------------|  
|[キャスト (SSIS 式)](cast-ssis-expression.md)|式をあるデータ型から別のデータ型に変換します。|  
|[() (括弧) (SSIS 式)](parentheses-ssis-expression.md)|式の評価順序を特定します。|  
|[+ (加算) (SSIS)](add-ssis.md)|2 つの数値式を加算します。|  
|[+ (連結) (SSIS 式)](concatenate-ssis-expression.md)|2 つの式を連結します。|  
|[- (減算) (SSIS 式)](subtract-ssis-expression.md)|最初の数値式から 2 番目の数値式を減算します。|  
|[- (否定) (SSIS 式)](negate-ssis-expression.md)|数値式を負数化します。|  
|[* (乗算) (SSIS 式)](multiply-ssis-expression.md)|2 つの数値式を乗算します。|  
|[除算 (SSIS 式)](divide-ssis-expression.md)|最初の数値式を 2 番目の数値式で除算します。|  
|[(剰余) (SSIS 式)](modulo-ssis-expression.md)|最初の数値式を 2 番目の数値式で割った剰余を整数値で返します。|  
|[&#124;&#124; (論理 OR) (SSIS 式)](logical-or-ssis-expression.md)|論理 OR 演算を実行します。|  
|[&& (論理 AND) (SSIS 式)](logical-and-ssis-expression.md)|論理 AND 演算を実行します。|  
|[\! &#40;論理 NOT&#41; &#40;SSIS 式&#41;](logical-not-ssis-expression.md)|ブール型のオペランドを否定します。|  
|[&#124; (ビット演算子包括的 OR) (SSIS 式)](bitwise-inclusive-or-ssis-expression.md)|2 つの整数値の OR 演算をビット単位で実行します。|  
|[^ (ビット演算子排他的 OR) (SSIS 式)](bitwise-exclusive-or-ssis-expression.md)|2 つの整数値の排他的 OR 演算をビット単位で実行します。|  
|[& (ビット演算子 AND) (SSIS 式)](bitwise-and-ssis-expression.md)|2 つの整数値の AND 演算をビット単位で実行します。|  
|[~ (ビット演算子 Not) (SSIS 式)](bitwise-not-ssis-expression.md)|整数の否定のビット演算を実行します。|  
|[== &#40;等しい&#41; &#40;SSIS 式&#41;](equal-ssis-expression.md)|2 つの式が等しいかどうかを判別するための比較を実行します。|  
|[\!= &#40;等しくない&#41; &#40;SSIS 式&#41;](unequal-ssis-expression.md)|2 つの式が等しくないかどうかを判別するための比較を実行します。|  
|[&#62; &#40;より大きい&#41; &#40;SSIS 式&#41;](greater-than-ssis-expression.md)|最初の式が 2 番目の式より大きいかどうかを判別するための比較を実行します。|  
|[&#60; &#40;より小さい&#41; &#40;SSIS 式&#41;](less-than-ssis-expression.md)|最初の式が 2 番目の式未満かどうかを判別するための比較を実行します。|  
|[&#62;= &#40;以上&#41; &#40;SSIS 式&#41;](greater-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以上かどうかを判別するための比較を実行します。|  
|[&#60;= &#40;以下&#41; &#40;SSIS 式&#41;](less-than-or-equal-to-ssis-expression.md)|最初の式が 2 番目の式以下かどうかを判別するための比較を実行します。|  
|[? : &#40;条件&#41; &#40;SSIS 式&#41;](conditional-ssis-expression.md)|ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。|  
  
 優先順位の階層内における各演算子の配置の詳細については、「 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数 &#40;SSIS 式&#41;](functions-ssis-expression.md)   
 [Integration Services 式の詳細の例](examples-of-advanced-integration-services-expressions.md)   
 [Integration Services &#40;SSIS&#41; 式](integration-services-ssis-expressions.md)  
  
  
