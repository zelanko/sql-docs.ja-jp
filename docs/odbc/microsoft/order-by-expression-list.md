---
description: ORDER BY 式リスト
title: ORDER BY 式-list |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd084a1012d445c89cacba168f21267238bc250f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340618"
---
# <a name="order-by-expression-list"></a>ORDER BY 式リスト
式は ORDER BY 句で使用できます。 たとえば、次の句では、テーブルは a + b、c + d、e という3つのキー式で並べ替えられます。  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Set 関数または set 関数を含む式では、順序付けは許可されません。
