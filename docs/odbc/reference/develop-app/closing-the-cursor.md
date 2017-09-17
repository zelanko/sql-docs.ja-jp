---
title: "カーソルを閉じる |Microsoft ドキュメント"
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
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 05cf8dde95111a9f5b530b37fd9a60356f4b77bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="closing-the-cursor"></a>カーソルを閉じる
アプリケーションは、カーソルの使用が完了したら、それを呼び出す**SQLCloseCursor**カーソルを閉じます。 例:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 アプリケーションでは、カーソルを閉じ、されるまでは、別の SQL ステートメントの実行など、他のほとんどの操作、カーソルが開かれたステートメントを使用することはできません。 カーソルが開いているときに呼び出すことができる関数の一覧については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。  
  
> [!NOTE]  
>  カーソルが閉じ、アプリケーションを呼び出す必要があります**SQLCloseCursor**ではなく、 **SQLCancel**です。  
  
 カーソルを開いたままが明示的に終了するまでトランザクションをコミットまたはロールバック時に一部のデータ ソース、カーソルを閉じる点が異なります。 具体的には、結果の最後に到達した場合に設定、 **SQLFetch** SQL_NO_DATA が返される、カーソルを閉じられません。 空の結果セット (結果セットが正常に実行されたステートメントが行を返さなかった場合に作成される) であってもカーソルは、明示的に閉じる必要があります。
