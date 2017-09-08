---
title: "算術演算子 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], arithmetic
- arithmetic operators
- math operations [Transact-SQL]
ms.assetid: a41b92a5-1061-4e4d-bb3b-a180b73c88fa
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d7ab96d4a566a34a4045b53a6b8a8ba054408df9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="arithmetic-operators-transact-sql"></a>算術演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  算術演算子は、数値型に分類されるデータ型が 1 つ以上含まれる 2 つの式の間で、数学的な操作を実行します。 データ型カテゴリの詳細については、次を参照してください。 [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)です。  
  
|演算子|意味|  
|--------------|-------------|  
|[+ (加算)](../../t-sql/language-elements/add-transact-sql.md)|追加|  
|[- (減算)](../../t-sql/language-elements/subtract-transact-sql.md)|減算|  
|[* (乗算)](../../t-sql/language-elements/multiply-transact-sql.md)|乗算|  
|[/(除算)](../../t-sql/language-elements/divide-transact-sql.md)|除算|  
|[% (剰余)](../../t-sql/language-elements/modulo-transact-sql.md)|除算による整数の剰余を返します。 たとえば、12 % 5 の場合、12 を 5 で割ると余りは 2 なので、12 % 5 = 2 となります。|  
  
 プラス記号 (+) マイナス記号 (-) 演算子も使用できますで算術演算を実行して**datetime**と**smalldatetime**値。  
  
 有効桁数と小数点以下桁数、算術演算の結果の詳細については、次を参照してください[有効桁数、小数点以下桁数、および長さ &#40;。TRANSACT-SQL と #41 です。](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  

