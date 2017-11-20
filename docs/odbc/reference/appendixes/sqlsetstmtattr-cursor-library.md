---
title: "SQLSetStmtAttr (カーソル ライブラリ) |Microsoft ドキュメント"
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
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d03483adc4a566d4691bb7687f231b41ca0b41bd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLSetStmtAttr**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLSetStmtAttr**を参照してください[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)です。  
  
 カーソル ライブラリで、次のステートメント属性をサポートしている**SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 カーソル ライブラリには、SQL_CURSOR_FORWARD_ONLY と SQL_CURSOR_STATIC SQL_ATTR_CURSOR_TYPE ステートメント属性の値のみがサポートしています。  
  
 順方向専用カーソルの場合は、カーソル ライブラリは、SQL_ATTR_CONCURRENCY ステートメント属性の SQL_CONCUR_READ_ONLY 値をサポートします。 静的カーソル、カーソル ライブラリでは、SQL_ATTR_CONCURRENCY ステートメント属性の値の SQL_CONCUR_READ_ONLY と SQL_CONCUR_VALUES 値をサポートしています。  
  
 カーソル ライブラリは、SQL_ATTR_SIMULATE_CURSOR ステートメント属性の SQL_SC_NON_UNIQUE 値のみをサポートします。  
  
 ODBC 仕様への呼び出しをサポートして**SQLSetStmtAttr**後 SQL_ATTR_PARAM_BIND_TYPE または SQL_ATTR_ROW_BIND_TYPE 属性を持つ**SQLFetch**または**SQLFetchScroll**が呼び出されると、カーソル ライブラリはありません。 カーソル ライブラリでバインドの種類を変更することができます、前に、アプリケーションは、カーソルを閉じる必要があります。 SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性と、カーソルが開いているをカーソル ライブラリが SQL_ATTR_ROW_BIND_OFFSET_PTR、SQL_ATTR_PARAM_BIND_OFFSET_PTR、SQL_ATTR_ROWS_FETCHED_PTR、変更をサポートします。  
  
 アプリケーションが呼び出すことができます**SQLSetStmtAttr**で、**属性**カーソルが開いている間、行セットのサイズを変更する sql_attr_row_array_size を指定します。 新しい行セットのサイズを反映次回**SQLFetchScroll**または**SQLFetch**と呼びます。  
  
 カーソル ライブラリでは、バインディングのオフセットを有効にする SQL_ATTR_PARAM_BIND_OFFSET_PTR または SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の設定をサポートします。 バインディングのオフセットは、呼び出しのためには使用されません**SQLFetch** ODBC 2 で、カーソル ライブラリを使用した場合*。x*ドライバー。  
  
 カーソル ライブラリでは、SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARKS ステートメント属性に設定をサポートします。

