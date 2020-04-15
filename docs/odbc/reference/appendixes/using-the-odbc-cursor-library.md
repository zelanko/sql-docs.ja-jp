---
title: ODBC カーソル ライブラリの使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], using cursor library
- cursor library [ODBC], using cursor library
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c740ed78de51684eac38ad0c54ab2224986018d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301403"
---
# <a name="using-the-odbc-cursor-library"></a>ODBC カーソル ライブラリの使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソル ライブラリを使用するには、アプリケーションを次の手順に従います。  
  
1.  特定の接続でのカーソル ライブラリの使用方法を指定するには、SQL_ATTR_ODBC_CURSORSの*属性*を指定して**SQLSetConnectAttr**を呼び出します。 カーソル ライブラリは常に (SQL_CUR_USE_ODBC)、ドライバーがスクロール可能なカーソルをサポートしていない場合 (SQL_CUR_USE_IF_NEEDED)、または使用しない (SQL_CUR_USE_DRIVER) 場合にのみ使用できます。  
  
2.  **データ ソースに接続するには、SQL****接続****、SQL ドライバー接続**、または呼び出しを呼び出します。  
  
3.  **SQLSetStmtAttr**を呼び出して、カーソルの種類 (SQL_ATTR_CURSOR_TYPE)、同時実行 (SQL_ATTR_CONCURRENCY)、および行セット のサイズ (SQL_ATTR_ROW_ARRAY_SIZE) を指定します。 カーソル ライブラリは、前方のみのカーソルと静的カーソルをサポートします。 前方のみのカーソルは読み取り専用である必要がありますが、静的カーソルは読み取り専用にすることも、値を比較するオプティミスティック同時実行制御を使用することもできます。  
  
4.  1 つ以上の行セット バッファーを割り当て **、SQLBindCol**を 1 回以上呼び出して、これらのバッファーを結果セット列にバインドします。  
  
5.  **SELECT**ステートメントまたはプロシージャを実行するか、カタログ関数を呼び出して結果セットを生成します。 アプリケーションが位置指定更新ステートメントを実行する場合は、結果セットを生成するために**SELECT FOR UPDATE**ステートメントを実行する必要があります。  
  
6.  **SQLFetch**または**SQLFetchScroll を**呼び出して、結果セットをスクロールします。  
  
 アプリケーションは、行セット バッファーのデータ値を変更できます。 カーソル ライブラリのキャッシュのデータで行セット バッファーを更新するには、アプリケーションは、引数 FetchOrientation を SQL_FETCH_RELATIVE に設定し *、FetchOffset*引数を 0 に設定して**SQLFetchScroll**を呼び出します。 *FetchOrientation*  
  
 非バインド列からデータを取得するために、アプリケーションは**SQLSetPos**を呼び出して、目的の行にカーソルを置きます。 次に **、SQLGetData**を呼び出してデータを取得します。  
  
 データ ソースから取得された行数を調べるには、アプリケーションは**SQLRowCount**を呼び出します。
