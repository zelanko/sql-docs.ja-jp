---
title: カーソルを閉じる |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299142"
---
# <a name="closing-the-cursor"></a>カーソルを閉じる
アプリケーションは、カーソルの使用を終了すると **、SQLCloseCursor**を呼び出してカーソルを閉じます。 次に例を示します。  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 アプリケーションがカーソルをクローズするまで、カーソルがオープンされたステートメントは、他の SQL ステートメントの実行など、他のほとんどの操作に使用できません。 カーソルが開いている間に呼び出すことができる関数の完全なリストについては、「[付録 B : ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。  
  
> [!NOTE]  
>  カーソルを閉じるには、アプリケーションは SQL**キャンセル**ではなく**SQLCloseCursor**を呼び出す必要があります。  
  
 カーソルは、トランザクションがコミットまたはロールバックされる場合を除き、明示的に閉じられるまで開いたままです。 特に **、SQLFetch**がSQL_NO_DATAを返すときに結果セットの末尾に達しても、カーソルは閉じません。 空の結果セットのカーソル (ステートメントが正常に実行されたが、行が返されない場合に作成される結果セット) も、明示的に閉じる必要があります。
