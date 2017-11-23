---
title: "データ バッファーのアドレス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 726505eca506b437cbf728d0821ef99ef7d90aea
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
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
