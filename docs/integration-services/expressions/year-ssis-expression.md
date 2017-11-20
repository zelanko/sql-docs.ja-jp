---
title: "YEAR (SSIS 式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a72a54b02f136f2d9acc130051e79852d72a2f1f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="year-ssis-expression"></a>YEAR (SSIS 式)
  ある日付の、年の日付要素を表す整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a>引数  
 *date*  
 任意の日付形式の日付です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_I4  
  
## <a name="remarks"></a>解説  
 引数が NULL の場合、YEAR は NULL を返します。  
  
 日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
> [!NOTE]  
>  日付リテラルが DT_DBTIMESTAMPOFFSET と DT_DBTIMESTAMP2 のいずれかの日付データ型に明示的にキャストされると、式の検証は失敗します。  
  
 YEAR 関数を使用すると、DATEPART("Year", date) 関数を使用する場合と同じ結果を、より簡単に取得できます。  
  
## <a name="expression-examples"></a>式の例  
 この例では、日付リテラルの年を表す数値が返されます。 データが mm/dd/yyyy 形式の場合、この例では "2002" が返されます。  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 この例では、 **ModifiedDate** 列内の年を表す整数が返されます。  
  
```  
YEAR(ModifiedDate)  
```  
  
 この例では、現在の日付の年を表す整数が返されます。  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a>参照  
 [DATEADD & #40 です。SSIS 式 &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [Datediff 関数 & #40 です。SSIS 式 &#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART & #40 です。SSIS 式 &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [日付と #40 です。SSIS 式 &#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [月と #40 です。SSIS 式 &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [関数と #40 です。SSIS 式 &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

