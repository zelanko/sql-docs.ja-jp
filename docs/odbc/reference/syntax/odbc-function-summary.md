---
title: ODBC 関数の概要 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c10cc7880cf941a1490f963e21e8b44bc91db215
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298923"
---
# <a name="odbc-function-summary"></a>ODBC 関数の概要
次の表は、ODBC 関数をタスクの種類別にグループ化して一覧し、適合性の指定と各関数の目的の簡単な説明を示しています。 準拠指定の詳細については[、ODBC および標準 CLI を](../../../odbc/reference/odbc-and-the-standard-cli.md)参照してください。 各関数の構文とセマンティクスの詳細については[、「ODBC API リファレンス」を参照してください](../../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 アプリケーションは、ドライバーに関する準拠情報を取得するのに**は、SQLGetInfo**関数を呼び出すことができます。 ドライバーの特定の関数のサポートに関する情報を取得するには、アプリケーションは**SQLGetFunctions**を呼び出すことができます。  
  
|タスク|関数名|適合 性|目的|  
|----------|-------------------|-----------------|-------------|  
|データ ソースへの接続|[ハンドル](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|環境、接続、ステートメント、または記述子ハンドルを取得します。|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|データ ソース名、ユーザー ID、およびパスワードによって特定のドライバーに接続します。|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|接続文字列またはドライバー マネージャーとドライバーがユーザーの接続ダイアログ ボックスを表示する要求によって特定のドライバーに接続します。|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|連続したレベルの接続属性と有効な属性値を返します。 各接続属性に値が指定されている場合は、データ ソースに接続します。|  
|ドライバとデータ ソースに関する情報の取得|[データベースソース](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|使用可能なデータ ソースの一覧を返します。<br /><br /> インストールされているドライバとその属性の一覧を返します。|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|特定のドライバーとデータ ソースに関する情報を返します。|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|サポートされているドライバ関数を返します。|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|サポートされているデータ型に関する情報を返します。|  
|ドライバ属性の設定と取得|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|接続属性を設定します。<br /><br /> 接続属性の値を返します。|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|環境属性を設定します。|  
||[アズ・ビジトル](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|環境属性の値を返します。|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|ステートメント属性を設定します。|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|ステートメント属性の値を返します。|  
|記述子フィールドの設定と検索|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|単一の記述子フィールドの値を返します。<br /><br /> 複数の記述子フィールドの値を返します。|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|単一の記述子フィールドを設定します。|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|複数の記述子フィールドを設定します。|  
||[を使用する](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|記述子情報をある記述子ハンドルから別の記述子ハンドルにコピーします。|  
|SQL 要求の準備|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|後で実行できるように SQL ステートメントを準備します。|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|SQL ステートメント内のパラメーターにストレージを割り当てます。|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|ステートメント ハンドルに関連付けられたカーソル名を返します。|  
||[カーソルを設定します。](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|カーソル名を指定します。|  
||[スクロールオプション](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|カーソルの動作を制御するオプションを設定します。|  
|リクエストの送信|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|準備されたステートメントを実行します。<br /><br /> ステートメントを実行します。|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|ドライバーによって変換された SQL ステートメントのテキストを返します。|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|ステートメント内の特定のパラメーターの説明を返します。|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|ステートメント内のパラメーターの数を返します。|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|実行時にパラメータ データを指定するために **、SQLPutData**と組み合わせて使用されます。 (長いデータ値に役立ちます。|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|パラメータのデータ値の一部または全部を送信します。 (長いデータ値に役立ちます。|  
|結果と結果に関する情報の取得|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|挿入、更新、または削除要求によって影響を受ける行数を返します。<br /><br /> 結果セット内の列数を返します。|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|結果セット内の列を記述します。|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|結果セット内の列の属性を記述します。|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|結果列のストレージを割り当て、データ型を指定します。|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|複数の結果行を返します。|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|スクロール可能な結果行を返します。|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|結果セットの 1 行の 1 列の一部または全部を返します。 (長いデータ値に役立ちます。|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|フェッチされたデータブロック内にカーソルを配置し、アプリケーションが行セット内のデータを更新したり、結果セット内のデータを更新または削除したりできるようにします。|  
||[オペレーション](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|ブックマークによる更新、削除、およびフェッチを含む、一括挿入および一括ブックマーク操作を実行します。|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|使用可能な結果セットが他にもあるかどうかを判断し、使用可能な場合は、次の結果セットの処理を初期化します。|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|追加の診断情報 (診断データ構造の単一フィールド) を返します。|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|追加の診断情報 (診断データ構造の複数のフィールド) を返します。|  
|データ ソースのシステム テーブルに関する情報の取得 (カタログ関数)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> [グループを開く]|1 つ以上のテーブルの列と関連する権限のリストを返します。<br /><br /> 指定したテーブルの列名のリストを返します。|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|外部キーを構成する列名のリストを返します (指定したテーブルに存在する場合)。|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|テーブルの主キーを構成する列名のリストを返します。|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|指定されたプロシージャの結果セットを構成する列と、入力パラメーターと出力パラメーターの一覧を返します。|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|特定のデータ ソースに格納されているプロシージャ名の一覧を返します。|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|[グループを開く]|指定したテーブルの行を一意に識別する最適な列セット、またはトランザクションによって行の値が更新されたときに自動的に更新される列に関する情報を返します。|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|単一のテーブルに関する統計と、そのテーブルに関連付けられたインデックスのリストを返します。|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|テーブルの一覧と、各テーブルに関連付けられている権限を返します。|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|[グループを開く]|特定のデータ ソースに格納されているテーブル名の一覧を返します。|  
|ステートメントの終了|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|ステートメントの処理を終了し、保留中の結果を破棄し、必要に応じて、ステートメント・ハンドルに関連付けられたすべてのリソースを解放します。|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|ステートメント・ハンドルでオープンされたカーソルをクローズします。|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|ステートメントの処理をキャンセルします。|  
||[ハンドルを処理します。](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|ステートメントまたは接続の処理をキャンセルします。|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|トランザクションをコミットまたはロールバックします。|  
|接続の終了|[接続解除](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|接続を閉じます。<br /><br /> 環境、接続、ステートメント、または記述子ハンドルを解放します。|
