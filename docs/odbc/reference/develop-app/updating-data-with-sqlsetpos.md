---
title: "SQLSetPos によるデータの更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb89d4a2220c487f2e126b50ecf8cbedd20857cc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data-with-sqlsetpos"></a>SQLSetPos によるデータの更新
アプリケーションの更新または削除を含む行セットの任意の行**SQLSetPos**です。 呼び出す**SQLSetPos**便利な代替手段を作成して SQL ステートメントを実行します。 これにより、odbc データ ソースが配置されている SQL ステートメントをサポートしていない場合でも、位置指定更新をサポートできます。 関数呼び出しを使用してデータベースの完全なアクセスを実現するためのパラダイムの一部です。  
  
 **SQLSetPos**現在の行セットに対して演算を行いへの呼び出し後にのみ使用できます**SQLFetchScroll**です。 アプリケーションは、更新、削除、または挿入するには、行の数を指定し、ドライバーは、行セットのバッファーからその行の新しいデータを取得します。 **SQLSetPos**現在の行として指定した行を指定するか、データ ソースから行セット内の特定の行を更新するにも使用できます。  
  
 行セットのサイズの設定への呼び出しによって**SQLSetStmtAttr**で、*属性*引数 sql_attr_row_array_size を指定します。 **SQLSetPos**への呼び出し後にのみ、ただし、新しい行セットのサイズを使用して**SQLFetch**または**SQLFetchScroll**です。 たとえば、行セットのサイズを変更すると、 **SQLSetPos**が呼び出されたし、 **SQLFetch**または**SQLFetchScroll**が呼び出されるを呼び出すと**SQLSetPos**中に古い行セットのサイズを使用して**SQLFetch**または**SQLFetchScroll**で新しい行セット サイズを使用します。  
  
 行セット内の先頭行の行番号は 1 です。 *RowNumber*引数**SQLSetPos** ; 行セット内の行を識別する必要がありますは、その値は、1 から最後にフェッチした行の数までの間でなければなりません (可能性もありますより小さい行セット サイズ)。 場合*RowNumber*が 0 の場合、操作は、行セット内のすべての行に適用されます。  
  
 Sql、リレーショナル データベースとほとんどの対話が行われるため**SQLSetPos**広くサポートされていません。 ただし、ドライバー簡単にエミュレートできますそれを作成して実行して、**更新**または**削除**ステートメントです。  
  
 どのような操作を決定する**SQLSetPos**サポートされており、アプリケーションが呼び出す**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_CURSOR_ATTRIBUTES1 情報オプション (カーソルの種類) によって異なります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLSetPos で行セット内の行を更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [SQLSetPos を含む行セット内の行を削除します。](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)

