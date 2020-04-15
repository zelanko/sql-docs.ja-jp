---
title: データ バッファ アドレス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578e4e37a78818cb640d9f32e2480cec5951df63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305273"
---
# <a name="data-buffer-address"></a>データ バッファーのアドレス
アプリケーションは、引数でドライバーにデータ バッファーのアドレスを渡します。 *ValuePtr* たとえば、次の**SQLBindCol**の呼び出しでは、アプリケーションは*Date*変数のアドレスを指定します。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 [「バッファーの割り当てと解放」](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)セクションで説明したように、バッファーがバインドされないまで、遅延バッファーのアドレスは有効である必要があります。  
  
 特に禁止されていない限り、データ バッファーのアドレスは null ポインターにすることができます。 ドライバーにデータを送信するために使用するバッファーの場合、これは、ドライバーは、バッファーに通常含まれている情報を無視します。 ドライバーからデータを取得するために使用されるバッファーの場合、これはドライバーが値を返さない原因となります。 どちらの場合も、ドライバーは、対応するデータ バッファー長引数を無視します。
