---
title: カーソルを閉じる |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 723e40e6d83eed84ed93ee1eeab3535622ad5f04
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299142"
---
# <a name="closing-the-cursor"></a>カーソルを閉じる
アプリケーションがカーソルの使用を終了すると、 **Sqlcloを**呼び出してカーソルを閉じます。 次に例を示します。  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 アプリケーションがカーソルを閉じるまでは、カーソルを開いているステートメントを他のほとんどの操作 (別の SQL ステートメントの実行など) に使用することはできません。 カーソルが開いているときに呼び出すことができる関数の完全な一覧については、「[付録 B: ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。  
  
> [!NOTE]  
>  カーソルを閉じるには、アプリケーションは**SQLCancel**ではなく**sqlcloを**呼び出す必要があります。  
  
 カーソルは明示的に閉じられるまで開いたままになります。トランザクションがコミットまたはロールバックされる場合を除きます。この場合、一部のデータソースはカーソルを閉じます。 具体的には、 **Sqlfetch**によって SQL_NO_DATA が返された場合、はカーソルを閉じません。 空の結果セットのカーソルも (ステートメントが正常に実行されたものの、行が返されなかった場合に作成された結果セット)、明示的に閉じる必要があります。
