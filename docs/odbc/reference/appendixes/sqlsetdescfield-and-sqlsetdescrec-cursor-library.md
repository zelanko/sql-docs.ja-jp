---
title: "Sqlsetdescfield によると SQLSetDescRec (カーソル ライブラリ) |Microsoft ドキュメント"
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
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0589474986fcd4014a7856d5233e3e0eb35c6f9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>Sqlsetdescfield によると SQLSetDescRec (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでの使用について説明します、 **SQLSetDescField**と**SQLSetDescRec**カーソル ライブラリ内の関数。 これらの関数の概要については、次を参照してください。 [SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)と[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)です。  
  
 カーソル ライブラリを実行**SQLSetDescField**ブックマーク列に対して設定を呼び出す際、フィールドの値を取得します。  
  
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
  
 カーソル ライブラリへの呼び出しを実行する**SQLSetDescRec**ブックマーク列にします。  
  
 ODBC 2 を使用場合します。*x*ドライバー、カーソル ライブラリで SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長) と**SQLSetDescField**または**SQLSetDescRec** SQL_DESC_OCTET_ を設定するために呼び出されるブックマークのレコード、ARD を 4 に等しくない値の長さフィールドです。 ODBC 3 を使用するときに*.x*ドライバー、カーソル ライブラリにより、バッファーのサイズを変更します。  
  
 カーソル ライブラリ実行**SQLSetDescField** SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_BIND_TYPE、SQL_DESC_ROW_ARRAY_SIZE、または SQL_DESC_ROW_STATUS_PTR フィールドの値を返す呼び出されたとき。 これらのフィールドは、ブックマークの行だけでなく、任意の行に対して返されますことができます。  
  
 カーソル ライブラリは実行されません**SQLSetDescField**に記載されているフィールド以外の任意の記述子フィールドを変更します。 アプリケーションを呼び出す場合**SQLSetDescField**カーソル ライブラリが読み込まれているを他のフィールドを設定する呼び出しに渡されるドライバー。  
  
 カーソル ライブラリは、アプリケーション行記述子の任意の行の SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドの動的な変更をサポートしています (呼び出しの後に**SQLExtendedFetch**、 **SQLFetch**、または**SQLFetchScroll**)。 SQL_DESC_OCTET_LENGTH_PTR フィールドは、列の長バッファーをバインド解除するだけの null ポインターを変更できます。  
  
 カーソル ライブラリでは、カーソルが開いているときに APD または ARD SQL_DESC_BIND_TYPE フィールドを変更することはできません。 カーソルが閉じられた後にのみ、および新しいカーソルが開かれる前に、SQL_DESC_BIND_TYPE フィールドを変更できます。 カーソル ライブラリが、カーソルが開いているときに変更をサポートする唯一の記述子フィールドは SQL_DESC_ARRAY_STATUS_PTR、SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR、および SQL_DESC_ROWS_PROCESSED_PTR。  
  
 カーソル ライブラリが後 ARD の SQL_DESC_COUNT フィールドの変更をサポートしていない**SQLExtendedFetch**または**SQLFetchScroll**が呼び出されて、カーソルが閉じられた前にします。
