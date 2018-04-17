---
title: カーソルを閉じる |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 54cc6515ea7b0c60916e9bb1ebd00d0b05af549e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="closing-the-cursor"></a>カーソルを閉じる
アプリケーションは、カーソルの使用が完了したら、それを呼び出す**SQLCloseCursor**カーソルを閉じます。 以下に例を示します。  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 アプリケーションでは、カーソルを閉じ、されるまでは、別の SQL ステートメントの実行など、他のほとんどの操作、カーソルが開かれたステートメントを使用することはできません。 カーソルが開いているときに呼び出すことができる関数の一覧については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。  
  
> [!NOTE]  
>  カーソルが閉じ、アプリケーションを呼び出す必要があります**SQLCloseCursor**ではなく、 **SQLCancel**です。  
  
 カーソルを開いたままが明示的に終了するまでトランザクションをコミットまたはロールバック時に一部のデータ ソース、カーソルを閉じる点が異なります。 具体的には、結果の最後に到達した場合に設定、 **SQLFetch** SQL_NO_DATA が返される、カーソルを閉じられません。 空の結果セット (結果セットが正常に実行されたステートメントが行を返さなかった場合に作成される) であってもカーソルは、明示的に閉じる必要があります。
