---
title: ORDER BY 式リスト |マイクロソフトドキュメント
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
ms.openlocfilehash: 272fa0be844569d322679d444807f8c332b4837b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291222"
---
# <a name="order-by-expression-list"></a>ORDER BY 式リスト
式は ORDER BY 句で使用できます。 たとえば、次の句では、テーブルは 3 つのキー式(a+b、c+d、e)で並べられます。  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 セット関数またはセット関数を含む式では、順序付けはできません。
