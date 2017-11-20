---
title: "SQLSetPos (カーソル ライブラリ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b195ca1dbb138b21fcf107150832288df8317196
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLSetPos**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLSetPos**を参照してください[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
 カーソル ライブラリ、SQL_POSITION 操作に対してのみをサポートしている、*操作*引数**SQLSetPos**です。 SQL_LOCK_NO_CHANGE 値のみがサポートしている、 *LockType*引数。  
  
 ドライバーが一括操作をサポートしていない場合、カーソル ライブラリは SQLSTATE HYC00 を返します (ドライバーは対応していない) 場合に**SQLSetPos**で呼び出された*RowNumber*を 0 に等しい。 このドライバーの動作は推奨されません。  
  
 カーソル ライブラリではサポートされない、SQL_UPDATE および SQL_DELETE 操作への呼び出し**SQLSetPos**です。 カーソル ライブラリの実装、位置指定更新または、検索結果を作成して SQL ステートメントを削除を更新またはバインドされた各列のキャッシュに格納された値を列挙する WHERE 句を伴うステートメントを削除します。 詳細については、次を参照してください。[配置されている更新プログラムの処理と削除ステートメント](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)です。  
  
 ドライバーが静的カーソルをサポートしていない場合、カーソル ライブラリを使用するアプリケーションを呼び出す必要があります**SQLSetPos**によってフェッチされた行セットでのみ**SQLExtendedFetch**または**SQLFetchScroll**ではなく**SQLFetch**です。 カーソル ライブラリを実装する**SQLExtendedFetch**と**SQLFetchScroll**の繰り返しを呼び出すことで**SQLFetch** (行セット サイズ 1) のドライバーにします。 カーソル ライブラリへの呼び出しに渡します**SQLFetch**で、もう一方、を通じてドライバーにします。 場合**SQLSetPos**によってフェッチされた行の行セットで呼び出される**SQLFetch**ドライバーが静的カーソルをサポートしていない呼び出しは失敗**SQLSetPos**は機能しません順方向専用カーソルを使用します。 これは、アプリケーションが正常に呼び出された場合でも発生**SQLSetStmtAttr**に設定する SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC で、ドライバーが静的カーソルをサポートしていない場合でも、カーソル ライブラリをサポートしています。

