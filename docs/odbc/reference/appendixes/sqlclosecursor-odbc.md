---
title: "SQLCloseCursor_ODBC |Microsoft ドキュメント"
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
helpviewer_keywords: SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e8c9120543ad0b7ca7b04ad4085bae25c1840623
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLCloseCursor**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLCloseCursor**を参照してください[SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)です。  
  
 カーソル ライブラリには、呼び出すことはできません。 **SQLCloseCursor**開いているカーソルなし。 この作業を行うと、SQLSTATE 24000 (無効なカーソルの状態) が返されます。 呼び出す**SQLFreeStmt**で、*オプション*SQL_CLOSE のときにカーソルが開いていないは、カーソル ライブラリでサポートされています。
