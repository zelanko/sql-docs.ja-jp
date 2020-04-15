---
title: SQLBindCol (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c29909a96f147a0f5ebc2140a68072dfe544255
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305473"
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLBindCol**関数の使用について説明します。 **SQLBindCol**の一般的な情報については、「 [SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)」を参照してください。  
  
 アプリケーションは、カーソル ライブラリに 1 つ以上のバッファを割り当てて、現在の行セットを返します。 **SQLBindCol を**1 回以上呼び出して、これらのバッファーを結果セットにバインドします。  
  
 アプリケーションは、バインド列の C データ型、列サイズ、および 10 進数の数字が同じである限り **、SQLExtendedFetch** **、SQLFetch**、または**SQLFetchScroll**を呼び出した後に、結果セット列を再バインドするために**SQLBindCol**を呼び出すことができます。 アプリケーションは、列を別のアドレスに再バインドするためにカーソルをクローズする必要はありません。  
  
 カーソル ライブラリでは、バインド オフセットを使用するSQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の設定がサポートされています。 ( この再バインドを行うために**SQLBindCol**を呼び出す必要はありません) 。カーソル ライブラリが ODBC *3.x*ドライバと共に使用される場合 **、SQLFetch**が呼び出されたときにバインド オフセットは使用されません。 SQLFetch が**SQLExtendedFetch**にマップされるため **、SQLFetch**が ODBC *2.x*ドライバーで使用されるときに**SQLFetch**が呼び出される場合、バインド オフセットが使用されます。  
  
 カーソル ライブラリは、ブックマーク列をバインドする**SQLBindCol**の呼び出しをサポートしています。  
  
 ODBC *2.x*ドライバーを操作する場合 **、SQLBindCol**が呼び出されたときに、カーソル ライブラリは SQLSTATE HY090 (無効な文字列またはバッファーの長さ) を返し、ブックマーク列のバッファー長を 4 に等しくない値に設定します。 ODBC *3.x*ドライバを使用する場合、カーソル ライブラリはバッファを任意のサイズにできます。
