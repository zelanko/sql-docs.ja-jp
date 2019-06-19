---
title: ORDER BY 式リスト |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c6be518211edb07251ff9234b095f3d3dde248b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63024273"
---
# <a name="order-by-expression-list"></a>ORDER BY 式リスト
式は、ORDER BY 句で使用できます。 たとえば、次の句でテーブルが順序付けに 3 つのキー式によって: a + の b、c +、d、および e。  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 集合関数または set 関数を含む式で順序付けは許可されません。
