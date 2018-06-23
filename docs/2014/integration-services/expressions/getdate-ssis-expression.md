---
title: GETDATE (SSIS 式) | Microsoft Docs
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
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9161d114b9f103dc857c26a07b3c107d14a00b40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176432"
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
 [GETUTCDATE &#40;SSIS 式&#41;](getutcdate-ssis-expression.md)   
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  