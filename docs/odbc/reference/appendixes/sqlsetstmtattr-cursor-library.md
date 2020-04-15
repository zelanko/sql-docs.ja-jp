---
title: SQL セットストムタット (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bdd9b3b559d5cc78a0d44f5280aae347bc8996a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300492"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLSetStmtAttr**関数の使用について説明します。 **一**般的な情報については、 SQL[セットStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)を参照してください。  
  
 カーソル ライブラリは **、SQLSetStmtAttr**を使用して次のステートメント属性をサポートします。  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 カーソル ライブラリでは、SQL_ATTR_CURSOR_TYPE ステートメント属性のSQL_CURSOR_FORWARD_ONLY値とSQL_CURSOR_STATIC値のみがサポートされます。  
  
 前方専用カーソルの場合、カーソル・ライブラリーは、SQL_ATTR_CONCURRENCYステートメント属性のSQL_CONCUR_READ_ONLY値をサポートします。 静的カーソルの場合、カーソル ライブラリは、SQL_ATTR_CONCURRENCY ステートメント属性のSQL_CONCUR_READ_ONLY値とSQL_CONCUR_VALUES値をサポートします。  
  
 カーソル ライブラリでは、SQL_ATTR_SIMULATE_CURSOR ステートメント属性のSQL_SC_NON_UNIQUE値のみがサポートされます。  
  
 ODBC 仕様では、SQLFetch または**SQLFetchScroll**が呼び出された後に、SQL_ATTR_PARAM_BIND_TYPE**SQLFetchScroll**またはSQL_ATTR_ROW_BIND_TYPE属性を使用して**SQLSetStmtAttr**の呼び出しをサポートしていますが、カーソル ライブラリはサポートしていません。 カーソル ライブラリのバインディング タイプを変更する前に、アプリケーションはカーソルを閉じる必要があります。 カーソル・ライブラリーは、カーソルがオープンされているときに、SQL_ATTR_ROW_BIND_OFFSET_PTR、SQL_ATTR_PARAM_BIND_OFFSET_PTR、SQL_ATTR_ROWS_FETCHED_PTR、およびSQL_ATTR_PARAMS_PROCESSED_PTRステートメント属性の変更をサポートします。  
  
 アプリケーションは、カーソルが開いている間に行セットのサイズを変更するために、SQL_ATTR_ROW_ARRAY_SIZEの**属性**を指定して**SQLSetStmtAttr**を呼び出すことができます。 新しい行セットのサイズは、次に**SQLFetchScroll**または**SQLFetch**が呼び出された時点で有効になります。  
  
 カーソル ライブラリでは、SQL_ATTR_PARAM_BIND_OFFSET_PTRまたはSQL_ATTR_ROW_BIND_OFFSET_PTRステートメント属性を設定して、バインディング オフセットを有効にできます。 カーソル ライブラリが ODBC 2 で使用されている場合 **、SQLFetch**の呼び出しにバインディング オフセットは使用されません。*x*ドライバ。  
  
 カーソル ライブラリでは、SQL_ATTR_USE_BOOKMARKS ステートメント属性をSQL_UB_VARIABLEに設定できます。
