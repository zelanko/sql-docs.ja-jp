---
title: SQLSetDescField および SQLSetDescRec (カーソル ライブラリ) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b390df48e676290696ae8080c8f671fd0e37bad8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727720"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField および SQLSetDescRec (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLSetDescField**と**SQLSetDescRec**カーソル ライブラリの関数。 これらの関数については、次を参照してください。 [SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)と[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)します。  
  
 カーソル ライブラリを実行します**SQLSetDescField**ブックマーク列の設定を呼び出す際、フィールドの値を返します。  
  
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
  
 カーソル ライブラリへの呼び出しを実行する**SQLSetDescRec**ブックマーク列。  
  
 ODBC 2 代表です。*x*ドライバー、カーソル ライブラリは、SQLSTATE HY090 を返します (無効な文字列長またはバッファー長) と**SQLSetDescField**または**SQLSetDescRec**が呼び出され、SQL_DESC_OCTET_ を設定するにはブックマークのレコードを ARD を 4 に等しくない値の長さフィールドです。 ODBC 3 は、使用する場合 *.x*ドライバー、カーソル ライブラリにより、バッファー サイズを変更します。  
  
 カーソル ライブラリを実行します**SQLSetDescField** SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_BIND_TYPE、SQL_DESC_ROW_ARRAY_SIZE、または SQL_DESC_ROW_STATUS_PTR フィールドの値を返すに呼び出されます。 これらのフィールドは、ブックマークの行だけでなく、任意の行に対して返されます。  
  
 カーソル ライブラリは実行されません**SQLSetDescField**に記載されているフィールド以外の任意の記述子フィールドを変更します。 アプリケーションを呼び出す場合**SQLSetDescField**をカーソル ライブラリの読み込み中には、他のフィールドに設定する呼び出しに渡されるドライバー。  
  
 カーソル ライブラリは、アプリケーションの行記述子のいずれかの行の SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドを動的に変更をサポートしています (呼び出しの後に**SQLExtendedFetch**、 **SQLFetch**、または**SQLFetchScroll**)。 SQL_DESC_OCTET_LENGTH_PTR フィールドは、列の長さのバッファーをバインド解除するには、のみ null ポインターを変更できます。  
  
 カーソル ライブラリでは、カーソルが開いているとき APD または ARD の SQL_DESC_BIND_TYPE フィールドを変更することはできません。 新しいカーソルが開かれる前に、カーソルが閉じられた後にのみ、SQL_DESC_BIND_TYPE フィールドを変更できます。 カーソルが開いているときに変更がカーソル ライブラリをサポートする唯一の記述子フィールドは SQL_DESC_ARRAY_STATUS_PTR、SQL_DESC_BIND_OFFSET_PTR、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR、および SQL_DESC_ROWS_PROCESSED_PTR。  
  
 カーソル ライブラリは、変更の後に ARD SQL_DESC_COUNT フィールドをサポートしていません**SQLExtendedFetch**または**SQLFetchScroll**が呼び出された、カーソルが閉じられた前にします。
