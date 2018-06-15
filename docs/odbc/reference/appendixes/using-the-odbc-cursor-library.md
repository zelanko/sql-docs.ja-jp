---
title: ODBC カーソル ライブラリを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], using cursor library
- cursor library [ODBC], using cursor library
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b9a5e1a11b5e8ba12308aaed342d6cf30e688e56
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912017"
---
# <a name="using-the-odbc-cursor-library"></a>ODBC カーソル ライブラリを使用します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソル ライブラリ、アプリケーションを使用します。  
  
1.  呼び出し**SQLSetConnectAttr**で、*属性*SQL_ATTR_ODBC_CURSORS カーソル ライブラリを特定の接続で使用する方法を指定するのです。 カーソル ライブラリは常にすることができます (SQL_CUR_USE_ODBC) を使用する、ドライバーがスクロール可能なカーソル (SQL_CUR_USE_IF_NEEDED) をサポートしていない場合にのみ使用または (SQL_CUR_USE_DRIVER) が使用されていません。  
  
2.  呼び出し**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**データ ソースに接続します。  
  
3.  呼び出し**SQLSetStmtAttr** (SQL_ATTR_CURSOR_TYPE) のカーソルの種類、同時実行 (SQL_ATTR_CONCURRENCY)、および行セット サイズ (SQL_ATTR_ROW_ARRAY_SIZE) を指定します。 カーソル ライブラリは、順方向専用カーソルと静的カーソルをサポートします。 順方向専用カーソルは、静的カーソルは読み取り専用または値を比較するオプティミスティック同時実行制御を使用できるときに、読み取り専用でなければなりません。  
  
4.  1 つ以上の行セットのバッファーと呼び出しを割り当てます**SQLBindCol**結果セット列にこれらのバッファーをバインドする 1 つ以上の時間。  
  
5.  実行によって結果セットが生成されます、**選択**ステートメントまたはプロシージャ、またはカタログ関数を呼び出すことによってです。 実行する場合は、アプリケーションは、位置指定更新ステートメントを実行は、**更新用に選択**結果セットを生成するステートメント。  
  
6.  呼び出し**SQLFetch**または**SQLFetchScroll** 1 回以上、結果セットの間をスクロールします。  
  
 アプリケーションでは、行セットのバッファー内のデータ値を変更できます。 アプリケーションが更新するには、カーソル ライブラリのキャッシュからデータを行セットのバッファーを呼び出す**SQLFetchScroll**で、 *FetchOrientation*引数 SQL_FETCH_RELATIVE に設定され、 *FetchOffset*引数を 0 に設定されています。  
  
 アプリケーションが、非バインド列からデータを取得する**SQLSetPos**に目的の行にカーソルを移動します。 呼び出して**SQLGetData**データを取得します。  
  
 アプリケーションの呼び出しをデータ ソースから取得された行の数を調べるには、する**SQLRowCount**です。
