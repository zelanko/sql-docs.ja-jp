---
title: GETUTCDATE (SSIS 式) | Microsoft Docs
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
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 091063acbaea65d155e578ff6a4c21c95d941a39
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075541"
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
  
  