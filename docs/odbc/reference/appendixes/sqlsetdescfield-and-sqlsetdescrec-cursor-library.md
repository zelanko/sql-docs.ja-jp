---
title: SQL セット・デズフィールドと SQL セット・デズレック (カーソル・ライブラリー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b85eb84cdf48a1c2a441b8994076a9023d254f2d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300552"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField および SQLSetDescRec (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLSetDescField**関数と**SQLSetDescRec**関数の使用について説明します。 これらの関数の一般的な情報については、「 [SQLSetDesc フィールド関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)」および[「 関数の設定 」](../../../odbc/reference/syntax/sqlsetdescrec-function.md)を参照してください。  
  
 カーソル ライブラリは、ブックマーク列に設定されたフィールドの値を返すために呼び出されたときに**SQLSetDescField**を実行します。  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 カーソル ライブラリは、ブックマーク列に対する**SQLSetDescRec**の呼び出しを実行します。  
  
 ODBC *2.x*ドライバーを使用する場合、カーソル ライブラリは **、SQLSetDescField**または**SQLSetDescRec**が呼び出されたときに SQLSTATE HY090 (無効な文字列またはバッファーの長さ) を返し、ARD のブックマーク レコードのSQL_DESC_OCTET_LENGTHフィールドを 4 と等しくない値に設定します。 ODBC *3.x*ドライバを使用する場合、カーソル ライブラリはバッファを任意のサイズにできます。  
  
 カーソル ライブラリは、SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_BIND_TYPE、SQL_DESC_ROW_ARRAY_SIZE、またはSQL_DESC_ROW_STATUS_PTRフィールドの値を返すために呼び出されたときに**SQLSetDescField**を実行します。 これらのフィールドは、ブックマーク行だけでなく、任意の行に対して返すことができます。  
  
 カーソル ライブラリは **、SQLSetDescField**を実行して、前述のフィールド以外の記述子フィールドを変更しません。 アプリケーションが**SQLSetDescField**を呼び出して、カーソル ライブラリが読み込まれている間に他のフィールドを設定すると、呼び出しがドライバーに渡されます。  
  
 カーソル ライブラリでは、アプリケーション行記述子の任意の行のSQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRフィールドを動的に変更できます **(SQLExtendedFetch** **、SQLFetch、** または**SQLFetchScroll**を呼び出した後)。 SQL_DESC_OCTET_LENGTH_PTRフィールドは、列の長さバッファーをバインド解除する場合にのみ、ヌル・ポインターに変更できます。  
  
 カーソル ライブラリは、カーソルがオープンされているときに APD または ARD のSQL_DESC_BIND_TYPE フィールドの変更をサポートしていません。 SQL_DESC_BIND_TYPEフィールドは、カーソルがクローズされた後、新しいカーソルがオープンされる前にのみ変更できます。 カーソルがオープンしているときにカーソルライブラリが変更をサポートする記述子フィールドは、SQL_DESC_ARRAY_STATUS_PTR、SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR、およびSQL_DESC_ROWS_PROCESSED_PTRだけです。  
  
 カーソル ライブラリでは **、SQLExtendedFetch**または**SQLFetchScroll**が呼び出された後、およびカーソルが閉じられる前に、ARD のSQL_DESC_COUNT フィールドの変更はサポートされていません。
