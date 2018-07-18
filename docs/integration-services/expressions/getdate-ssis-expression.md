---
title: GETDATE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5353e13e6c50f5a7f1438f7cd172211e2d45937e
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35403384"
---
# <a name="getdate-ssis-expression"></a>GETDATE (SSIS 式)
  システムの現在の日付を、DT_DBTIMESTAMP 形式で返します。 GETDATE 関数に引数はありません。  
  
> [!NOTE]  
>  GETDATE 関数から返される結果の長さは 29 文字です。  
  
## <a name="syntax"></a>構文  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="result-types"></a>戻り値の型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>式の例  
 この例では、現在の日付の年が返されます。  
  
```  
DATEPART("year",GETDATE())  
```  
  
 この例では、 **ModifiedDate** 列にある日付と現在の日付の間の日数が返されます。  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 この例では、現在の日付に 3 か月追加した値が返されます。  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>参照  
 [GETUTCDATE (SSIS 式)](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
