---
title: 算術演算子 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], arithmetic
- arithmetic operators
- math operations [Transact-SQL]
ms.assetid: a41b92a5-1061-4e4d-bb3b-a180b73c88fa
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ca21840e43eeffeaf1608d3ccab8794e18ff3a2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43057825"
---
# <a name="arithmetic-operators-transact-sql"></a>算術演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  算術演算子は、数値型に分類されるデータ型が 1 つ以上含まれる 2 つの式の間で、数学的な操作を実行します。 データ型の分類の詳細については、「[Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)」を参照してください。  
  
|演算子|意味|  
|--------------|-------------|  
|[+ (加算)](../../t-sql/language-elements/add-transact-sql.md)|加算|  
|[- (減算)](../../t-sql/language-elements/subtract-transact-sql.md)|減算|  
|[* (乗算)](../../t-sql/language-elements/multiply-transact-sql.md)|乗算|  
|[/ (除算)](../../t-sql/language-elements/divide-transact-sql.md)|除算|  
|[% (剰余)](../../t-sql/language-elements/modulo-transact-sql.md)|除算による整数の剰余を返します。 たとえば、12 % 5 の場合、12 を 5 で割ると余りは 2 なので、12 % 5 = 2 となります。|  
  
 + および - 演算子を使用して、**datetime** および **smalldatetime** 型の値に対して算術演算を実行することもできます。  
  
 算術演算の結果の有効桁数と小数点以下桁数の詳細については、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [数学関数 &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
