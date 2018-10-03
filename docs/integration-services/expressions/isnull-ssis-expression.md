---
title: ISNULL (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b67df5ddb8b3d1e0d450135d403d0c45eaf8a753
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647730"
---
# <a name="isnull-ssis-expression"></a>ISNULL (SSIS 式)
  式が NULL かどうかに基づいてブール型の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 任意のデータ型の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="expression-examples"></a>式の例  
 この例では、 **DiscontinuedDate** 列に NULL 値が含まれる場合、TRUE を返します。  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 この例では、 **LastName** 列の値が NULL の場合、"Unknown last name" を返し、NULL でない場合は **LastName**の値を返します。  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 この例では、変数 **AddDays** の値に関係なく、 **DaysToManufacture**列が NULL の場合は常に TRUE を返します。  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>参照  
 [関数 &#40;SSIS 式&#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
