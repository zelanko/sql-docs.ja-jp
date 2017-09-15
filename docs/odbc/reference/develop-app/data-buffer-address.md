---
title: "データ バッファーのアドレス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7d57b8ec52324dd4bec320b6179507ab3102e629
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-buffer-address"></a>データ バッファーのアドレス
アプリケーションでは、データ バッファーのアドレスを行い、多くの場合、という名前の引数でドライバーに*ValuePtr*または類似した名前です。 たとえば、呼び出しでは、次に**SQLBindCol**、アプリケーションのアドレスを指定する、*日付*変数。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 説明したように、[割り当てと解放バッファー](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  セクションで、遅延のバッファーのアドレス必要があるまで有効なバッファーがバインド解除します。  
  
 具体的には禁止されている場合を除き、データ バッファーのアドレスは、null ポインターを指定できます。 ドライバーにデータを送信するために使用、バッファーのこれにより、バッファーに通常含まれる情報を無視するドライバーです。 ドライバーからのデータの取得に使用されるバッファーの場合、これが原因に値を返さないドライバー。 どちらの場合は、ドライバーは、対応するデータのバッファー長の引数を無視します。
