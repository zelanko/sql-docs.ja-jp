---
title: ORDER BY 式リスト |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e531a26f0436c598fa04acc11e9735bb80faed44
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="order-by-expression-list"></a>ORDER BY 式リスト
式は、ORDER BY 句で使用できます。 たとえば、次の句でテーブルが順序付けに 3 つのキー式によって: + の b、c +、d、および e。  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 集合関数または set 関数を含む式で順序付けは許可されません。
