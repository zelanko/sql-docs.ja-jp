---
title: データを更新する場合は、SQLBulk オペレーション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b96e3a43b8385910e4260cf51dea7e4ff508200
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298486"
---
# <a name="updating-data-with-sqlbulkoperations"></a>SQLBulkOperations によるデータの更新
アプリケーションは **、 SQLBulkOperations**を呼び出して、データ ソースの基になるテーブルに対して一括更新、削除、フェッチ、または挿入操作を実行できます。 **SQLBulk オペレーションを**呼び出すことは、SQL ステートメントの作成と実行に代わる便利な方法です。 ODBC ドライバーは、データ ソースが位置指定 SQL ステートメントをサポートしていない場合でも、位置指定更新をサポートします。 これは、関数呼び出しによって完全なデータベース アクセスを実現するためのパラダイムの一部です。  
  
 **SQLBulkOperations は**現在の行セットを操作し、SQLFetch または**SQLFetchScroll**を呼び出した後にのみ使用できます。 **SQLFetchScroll** アプリケーションは、ブックマークをキャッシュすることによって更新、削除、または更新する行を指定します。 ドライバーは、更新する行の新しいデータ、または基になるテーブルに挿入する新しいデータを、行セット バッファーから取得します。  
  
 **SQLBulkOperations**で使用される行セット のサイズは *、SQL_ATTR_ROW_ARRAY_SIZEの属性*引数を使用して**SQLSetStmtAttr**の呼び出しによって設定されます。 **SQLSetPos**とは異なり **、SQLFetch**または**SQLFetchScroll**の呼び出し後にのみ新しい行セット サイズを使用する**SQLBulkOperations は****、SQLSetStmtAttr**の呼び出し後に新しい行セット サイズを使用します。  
  
 リレーショナル データベースとの対話のほとんどは SQL を使用して行われるため **、SQLBulkOperations は**広くサポートされていません。 ただし、ドライバは **、UPDATE** **、DELETE、** または**INSERT**ステートメントを作成して実行することで、簡単にエミュレートできます。  
  
 **SQLBulkOperation が**サポートする操作を決定するために、アプリケーションは 、(カーソルの種類に応じて) SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1情報オプションを使用して**SQLGetInfo**を呼び出します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLBulkOperations を使ったブックマークによる行の更新](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [SQLBulkOperations を使ったブックマークによる行の削除](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [SQLBulkOperations による行の挿入](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [SQLBulkOperations による行のフェッチ](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
