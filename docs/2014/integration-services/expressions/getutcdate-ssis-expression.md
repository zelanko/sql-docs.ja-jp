---
title: GETUTCDATE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d266d5c329776279f21dfbfdaa51a823f460a407
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087102"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (SSIS 式)
  システムの現在の日付を、DT_DBTIMESTAMP 形式を使用して UTC 時刻 (世界協定時またはグリニッジ標準時) で返します。 GETUTCDATE 関数に引数はありません。  
  
## <a name="syntax"></a>構文  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="result-types"></a>戻り値の型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>式の例  
 この例では、現在の日付の年が UTC 時刻で返されます。  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 この例では、 **ModifiedDate** 列にある日付と現在の UTC 日付の間の日数が返されます。  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 この例では、現在の UTC 日付に 3 か月追加した値が返されます。  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>参照  
 [GETDATE &#40;SSIS 式&#41;](getdate-ssis-expression.md)   
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  
