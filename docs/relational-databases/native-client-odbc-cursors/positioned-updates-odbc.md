---
title: 位置指定更新 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52495f670986638cac02661240e349713424256e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305328"
---
# <a name="positioned-updates-odbc"></a>位置指定更新 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC では、カーソルで位置指定更新を実行するために、次の 2 とおりの方法をサポートします。  
  
-   **SQLSetPos**  
  
-   WHERE CURRENT OF 句  
  
 より一般的なアプローチは、 **SQLSetPos**を使用することです。 次のオプションがあります。  
  
 SQL_POSITION  
 現在の行セットの特定行にカーソルを位置付けます。  
  
 SQL_REFRESH  
 カーソルが現在位置付けられている行から取り出した値で、結果セット列にバインドされているプログラム変数を更新します。  
  
 SQL_UPDATE  
 結果セット列にバインドされているプログラム変数に格納されている値で、カーソルの現在行を更新します。  
  
 SQL_DELETE  
 カーソルの現在行を削除します。  
  
 **SQLSetPos**は、ステートメント ハンドルカーソル属性がサーバー カーソルを使用するように設定されている場合に、任意のステートメントの結果セットで使用できます。 結果セットの列を、プログラム変数にバインドする必要があります。 アプリケーションが行をフェッチすると、すぐに**SQLSetPos**(SQL_POSTION) を呼び出してカーソルを行に配置します。 その後、アプリケーションは SQLSetPos(SQL_DELETE) を呼び出して現在行を削除するか、新しいデータ値をバインドされているプログラム変数に移動し、SQLSetPos(SQL_UPDATE) を呼び出して現在行を更新します。  
  
 アプリケーションは **、 SQLSetPos**を使用して行セット内の任意の行を更新または削除できます。 **SQLSetPos**を呼び出すことは、SQL ステートメントの構築と実行に代わる便利な方法です。 **SQLSetPos**は現在の行セットに対して動作し[、SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)を呼び出した後にのみ使用できます。  
  
 行セットのサイズは、属性引数がSQL_ATTR_ROW_ARRAY_SIZEの[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)の呼び出しによって設定されます。 **新**しい行セット サイズを使用しますが **、SQL フェッチ**または**SQL フェッチスクロール**を呼び出した後に限り、 たとえば、行セットのサイズが変更された場合は **、SQLSetPos**が呼び出され、**その後、SQL フェッチ**または**SQL フェッチスクロール**が呼び出されます。 **SQLSetPos**の呼び出しでは、古い行セットのサイズが使用されますが **、SQLFetch**または**SQLFetchScroll**は新しい行セットのサイズを使用します。  
  
 行セット内の先頭行の行番号は 1 です。 **SQLSetPos**の行番号引数は、行セット内の行を識別する必要があります。つまり、値は 1 から最後にフェッチされた行数までの範囲内になければなりません。 この値には、行セット サイズよりも小さい値を指定できます。 RowNumber が 0 の場合、操作は行セット内のすべての行に適用されます。  
  
 **SQLSetPos**の削除操作により、データ ソースは、テーブルの 1 つまたは複数の選択された行を削除します。 **SQLSetPos**を使用して行を削除するには、アプリケーションは、操作をSQL_DELETEに設定し、削除する行の番号に設定された行番号を行番号で**SQLSetPos**を呼び出します。 RowNumber が 0 の場合は、行セット内のすべての行が削除されます。  
  
 **SQLSetPos**が戻った後、削除された行は現在の行になり、その状態はSQL_ROW_DELETED。 [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)や**SQLSetPos**の呼び出しなど、追加の位置指定操作では行を使用できません。  
  
 行セットのすべての行を削除する (RowNumber が 0) 場合、アプリケーションは **、SQLSetPos**の更新操作と同様に行操作配列を使用して、ドライバーが特定の行を削除することを防ぐことができます。  
  
 削除対象の各行は、行セット内に存在する行でなければなりません。 フェッチによってアプリケーション バッファーが設定され、行の状態配列が維持されている場合は、これら各行位置の行の状態値が SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW であってはなりません。  
  
 位置指定更新は、UPDATE、DELETE、および INSERT の各ステートメントに WHERE CURRENT OF 句を使用することによっても実行できます。 現在の OF には[、SQLGetCursorName](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md)関数が呼び出されたときに ODBC が生成するカーソル名、または**SQLSetCursorName**を呼び出して指定できるカーソル名が必要です。 次に、ODBC アプリケーションで WHERE CURRENT OF 更新の実行に使用する一般的な手順を示します。  
  
-   **SQLSetCursorName**を呼び出して、ステートメント ハンドルのカーソル名を設定します。  
  
-   FOR UPDATE OF 句を指定した SELECT ステートメントを作成し、実行します。  
  
-   行セットを取得するには**SQLFetchScroll**を呼び出すか、行を取得するための**SQLFetch を**呼び出します。  
  
-   カーソルを行に配置するには **、SQLSetPos** (SQL_POSITION) を呼び出します。  
  
-   カーソル名を**SQLSetCursorName**で設定して、WHERE CURRENT OF 句を使用して UPDATE ステートメントをビルドして実行します。  
  
 または、SELECT ステートメントを実行する前に **、SQLSetCursorName**を呼び出す代わりに、SELECT ステートメントを実行した後に**SQLGetCursorName**を呼び出す方法があります。 **SQLSetCursorName を**使用してカーソル名を設定しない場合は、ODBC によって割り当てられた既定のカーソル**名を**返します。  
  
 サーバー カーソルを使用する場合は、WHERE CURRENT OF よりも**SQLSetPos**が優先されます。 ODBC カーソル ライブラリで静的で更新可能なカーソルを使用している場合、カーソル ライブラリは、基になるテーブルのキー値を指定した WHERE 句を追加することで、WHERE CURRENT OF 更新を実装します。 テーブル内のキーが一意でない場合、意図しない更新が行われることがあります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
