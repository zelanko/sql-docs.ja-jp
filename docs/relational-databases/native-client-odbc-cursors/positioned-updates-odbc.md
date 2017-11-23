---
title: "位置指定更新 (ODBC) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a77f61ebd66cf6bda10d8c59c61e5364208a66e9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="positioned-updates-odbc"></a>位置指定更新 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC では、カーソルで位置指定更新を実行するために、次の 2 とおりの方法をサポートします。  
  
-   **SQLSetPos**  
  
-   WHERE CURRENT OF 句  
  
 一般的な方法は、使用する**SQLSetPos**です。 次のオプションがあります。  
  
 SQL_POSITION  
 現在の行セットの特定行にカーソルを位置付けます。  
  
 SQL_REFRESH  
 カーソルが現在位置付けられている行から取り出した値で、結果セット列にバインドされているプログラム変数を更新します。  
  
 SQL_UPDATE  
 結果セット列にバインドされているプログラム変数に格納されている値で、カーソルの現在行を更新します。  
  
 SQL_DELETE  
 カーソルの現在行を削除します。  
  
 **SQLSetPos**設定サーバー カーソルを使用して、ステートメント ハンドル カーソル属性が設定されている任意のステートメントの結果で使用できます。 結果セットの列を、プログラム変数にバインドする必要があります。 アプリケーションは行のフェッチとすぐに呼び出して**SQLSetPos**(SQL_POSTION) に、行にカーソルを移動します。 その後、アプリケーションは SQLSetPos(SQL_DELETE) を呼び出して現在行を削除するか、新しいデータ値をバインドされているプログラム変数に移動し、SQLSetPos(SQL_UPDATE) を呼び出して現在行を更新します。  
  
 アプリケーションの更新または削除を含む行セットの任意の行**SQLSetPos**です。 呼び出す**SQLSetPos**便利な代替手段を作成して SQL ステートメントを実行します。 **SQLSetPos**現在の行セットに対して演算を行いへの呼び出し後にのみ使用できます[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)です。  
  
 行セットのサイズの設定への呼び出しによって[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)属性引数 sql_attr_row_array_size を指定します。 **SQLSetPos**しか呼び出しの後に、新しい行セットのサイズを使用して**SQLFetch**または**SQLFetchScroll**です。 たとえば、行セットのサイズを変更すると、 **SQLSetPos**が呼び出されたし、 **SQLFetch**または**SQLFetchScroll**と呼びます。 呼び出し**SQLSetPos**前の行セット サイズを使用してが**SQLFetch**または**SQLFetchScroll**で新しい行セット サイズを使用します。  
  
 行セット内の先頭行の行番号は 1 です。 RowNumber 引数**SQLSetPos** ; 行セット内の行を識別する必要がありますは、その値は、1 から最後にフェッチした行の数までの間でなければなりません。 この値には、行セット サイズよりも小さい値を指定できます。 RowNumber が 0 の場合、操作は行セット内のすべての行に適用されます。  
  
 削除操作**SQLSetPos**ようにデータ ソース テーブルの 1 つまたは複数の選択した行を削除します。 行を削除する**SQLSetPos**、アプリケーション呼び出し**SQLSetPos** Operation に SQL_DELETE、RowNumber、行の数を設定を削除するとします。 RowNumber が 0 の場合は、行セット内のすべての行が削除されます。  
  
 後に**SQLSetPos**削除された行は、現在の行とその状態は SQL_ROW_DELETED を返します。 呼び出しなど、追加の位置指定操作で、行は使用できません[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)または**SQLSetPos**です。  
  
 (RowNumber が 0 に等しい)、行セットのすべての行を削除すると、アプリケーションが使用できなくドライバーの更新操作のと同じように、行操作配列を使用して、特定の行を削除する**SQLSetPos**です。  
  
 削除対象の各行は、行セット内に存在する行でなければなりません。 フェッチによってアプリケーション バッファーが設定され、行の状態配列が維持されている場合は、これら各行位置の行の状態値が SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW であってはなりません。  
  
 位置指定更新は、UPDATE、DELETE、および INSERT の各ステートメントに WHERE CURRENT OF 句を使用することによっても実行できます。 ときに生成されますで現在のカーソル名 ODBC が必要な[SQLGetCursorName](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md)関数が呼び出されると、または呼び出すことで指定できる**SQLSetCursorName**です。 次に、ODBC アプリケーションで WHERE CURRENT OF 更新の実行に使用する一般的な手順を示します。  
  
-   呼び出す**SQLSetCursorName**ステートメント ハンドルのカーソル名を確立するためにします。  
  
-   FOR UPDATE OF 句を指定した SELECT ステートメントを作成し、実行します。  
  
-   呼び出す**SQLFetchScroll**を行セットを取得または**SQLFetch**行を取得します。  
  
-   呼び出す**SQLSetPos** (SQL_POSITION) に、行にカーソルを移動します。  
  
-   ビルドおよび設定カーソル名を使用して WHERE CURRENT OF 句を使用して、UPDATE ステートメントを実行**SQLSetCursorName**です。  
  
 呼び出すことも、 **SQLGetCursorName**呼び出す代わりに、SELECT ステートメントを実行した後**SQLSetCursorName** SELECT ステートメントを実行する前にします。 **SQLGetCursorName**を使用してカーソル名を設定しない場合は、ODBC によって割り当てられた既定のカーソル名を返します**SQLSetCursorName**です。  
  
 **SQLSetPos**をお勧め WHERE CURRENT OF 経由でサーバー カーソルを使用しているときにします。 ODBC カーソル ライブラリで静的で更新可能なカーソルを使用している場合、カーソル ライブラリは、基になるテーブルのキー値を指定した WHERE 句を追加することで、WHERE CURRENT OF 更新を実装します。 テーブル内のキーが一意でない場合、意図しない更新が行われることがあります。  
  
## <a name="see-also"></a>参照  
 [使用してカーソル &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
