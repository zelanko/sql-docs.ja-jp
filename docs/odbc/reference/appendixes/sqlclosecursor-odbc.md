---
title: "SQLCloseCursor_ODBC |Microsoft ドキュメント"
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
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fcc680ec815afa700c00c9d8a69c5826944153a4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLCloseCursor**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLCloseCursor**を参照してください[SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)です。  
  
 カーソル ライブラリには、呼び出すことはできません。 **SQLCloseCursor**開いているカーソルなし。 この作業を行うと、SQLSTATE 24000 (無効なカーソルの状態) が返されます。 呼び出す**SQLFreeStmt**で、*オプション*SQL_CLOSE のときにカーソルが開いていないは、カーソル ライブラリでサポートされています。
