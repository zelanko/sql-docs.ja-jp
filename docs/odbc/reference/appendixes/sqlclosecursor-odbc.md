---
title: SQLCloseCursor_ODBC |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1b61267d093e11bf7ea25158f5dc6a29ccba6a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296302"
---
# <a name="sqlclosecursor_odbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLCloseCursor**関数の使用方法について説明します。 **SQLCloseCursor**の一般的な情報については、「 [SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)」を参照してください。  
  
 カーソル ライブラリは、オープン カーソルを使用せずに**SQLCloseCursor**を呼び出すことはサポートされていません。 これを試みると、SQLSTATE 24000 (無効なカーソル状態) が返されます。 カーソルが開か*なかったときにSQL_CLOSE*オプションを指定して**SQLFreeStmt**を呼び出すことは、カーソル ライブラリでサポートされています。
