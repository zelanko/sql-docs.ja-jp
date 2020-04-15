---
title: SQL セットポス (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Cursor Library
ms.assetid: 574399c3-2bb2-4d19-829c-7c77bd82858d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c46ef88075a5adbd96138d7d1f03c26712f7ea1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300512"
---
# <a name="sqlsetpos-cursor-library"></a>SQLSetPos (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLSetPos**関数の使用について説明します。 **SQLSetPos**の一般的な情報については、「 [SQL セットポス関数](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
 カーソル ライブラリでは **、SQLSetPos**の*操作*引数に対してのみSQL_POSITION操作がサポートされています。 この引数は、*引数 LockType*に対してのみSQL_LOCK_NO_CHANGE値をサポートします。  
  
 ドライバーは、一括操作をサポートしていない場合、カーソル ライブラリは **、SQLSetPos**が 0 に等しい*行番号*と呼び出されたときに SQLSTATE HYC00 (ドライバーが不可能) を返します。 このドライバの動作はお勧めしません。  
  
 カーソル ライブラリは**SQLSetPos**の呼び出しでSQL_UPDATEおよびSQL_DELETE操作をサポートしていません。 カーソル ライブラリは、バインドされた各列のキャッシュに格納されている値を列挙する WHERE 句を使用して、検索された更新または削除ステートメントを作成することにより、位置指定更新または SQL ステートメントの削除を実装します。 詳細については、「[位置指定更新ステートメントおよび削除ステートメントの処理](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)」を参照してください。  
  
 ドライバーが静的カーソルをサポートしていない場合、カーソル ライブラリを使用するアプリケーションは **、SQLFetch**ではなく **、SQLExtendedFetch**または**SQLFetchScroll**によってフェッチされた行セットでのみ**SQLSetPos**を呼び出す必要があります。 カーソル ライブラリは、ドライバーで (行セットのサイズ 1) の SQLFetch の繰り返し呼び出しを行うことによって**SQLExtendedFetch**と**SQLFetchScroll**を実装します。 **SQLFetch** カーソル ライブラリは、呼び出しを**SQLFetch**に渡しますが、一方で、ドライバーに渡します。 ドライバーが静的カーソルをサポートしていない場合に**SQLFetch**によってフェッチされた複数行セットで**SQLSetPos**が呼び出された場合 **、SQLSetPos**は前方のみのカーソルで動作しないため、呼び出しは失敗します。 これは、アプリケーションが正常に**SQLSetStmtAttr**を呼び出してSQL_ATTR_CURSOR_TYPEをSQL_CURSOR_STATICに設定した場合でも発生します。
