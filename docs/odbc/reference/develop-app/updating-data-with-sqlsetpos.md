---
title: SQL セットポスを使用してデータを更新する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16476a1e1007905f34ec2e70ce6032eb8d81fe7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286162"
---
# <a name="updating-data-with-sqlsetpos"></a>SQLSetPos によるデータの更新
アプリケーションは **、 SQLSetPos**を使用して行セット内の任意の行を更新または削除できます。 **SQLSetPos**を呼び出すことは、SQL ステートメントの構築と実行に代わる便利な方法です。 ODBC ドライバーは、データ ソースが位置指定 SQL ステートメントをサポートしていない場合でも、位置指定更新をサポートします。 これは、関数呼び出しによって完全なデータベース アクセスを実現するためのパラダイムの一部です。  
  
 **SQLSetPos**は現在の行セットに対して動作し **、SQLFetchScroll**を呼び出した後にのみ使用できます。 アプリケーションは、更新、削除、または挿入する行の数を指定し、ドライバーは、行セット バッファーからその行の新しいデータを取得します。 **SQLSetPos**を使用して、指定した行を現在の行として指定したり、データ ソースから行セット内の特定の行を更新することもできます。  
  
 行セットのサイズは、*属性*引数がSQL_ATTR_ROW_ARRAY_SIZEの**SQLSetStmtAttr**の呼び出しによって設定されます。 **ただし、SQL フェッチ**または SQL**フェッチ**スクロールの呼び出しの後にのみ、新しい行セット サイズが使用**されます**。 たとえば、行セットのサイズが変更された場合 **、SQLSetPos**が呼び出され **、SQL フェッチ**または**SQL フェッチスクロール**が呼び出され、SQLFetch または**SQLFetchScroll**が新しい行セット サイズを使用している間 **、SQLSetPos**の呼び出しでは古い行セット サイズが使用されます。 **SQLFetchScroll**  
  
 行セット内の先頭行の行番号は 1 です。 **SQLSetPos**の*行番号*引数は、行セット内の行を識別する必要があります。つまり、値は 1 から最後にフェッチされた行数 (行セットサイズより小さい値) の範囲内になければなりません。 *RowNumber が*0 の場合、この操作は行セット内のすべての行に適用されます。  
  
 リレーショナル データベースとの対話のほとんどは SQL を使用して行われるため **、SQLSetPos**は広くサポートされていません。 ただし、ドライバーは **、UPDATE**または**DELETE**ステートメントを構築して実行することで、簡単にエミュレートできます。  
  
 **SQLSetPos**がサポートする操作を決定するために、アプリケーションは**SQLGetInfo**を呼び出し、(カーソルの種類に応じて) SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1情報オプションを使用します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLSetPos による行セットの行の更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [SQLSetPos による行セットの行の削除](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
