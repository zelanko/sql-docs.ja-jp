---
title: '付録 A: ODBC エラー コード |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error codes [ODBC]
- SQLSTATE [ODBC]
- error codes [ODBC], SQLSTATE
ms.assetid: c06902e4-721d-42e2-b818-05f0e18e4ce0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af288cf9f0564f6fe0dbef14f66143667120c656
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307523"
---
# <a name="appendix-a-odbc-error-codes"></a>付録 A: ODBC エラー コード
このトピックでは、ODBC 3 の SQLSTATE 値について説明します。*x .* ODBC 3 の詳細については、次の参照を参照してください。*x* SQLSTATE 値については[、「SQLSTATE マッピング](../../../odbc/reference/develop-app/sqlstate-mappings.md)」を参照してください。  
  
 **SQLGetDiagRec**または**SQLGetDiagField は**、オープン グループ*データ管理: 構造化照会言語 (SQL)、バージョン 2* (1995 年 3 月) で定義されている SQLSTATE 値を返します。 SQLSTATE 値は、5 文字を含む文字列です。 次の表は、ドライバーが**SQLGetDiagRec**に対して返すことができる SQLSTATE 値を示しています。  
  
 SQLSTATE に返される文字ストリング値は、2 文字のクラス値とそれに続く 3 文字のサブクラス値で構成されます。 クラス値 "01" は警告を示し、SQL_SUCCESS_WITH_INFOの戻りコードを伴います。 クラス "IM" 以外のクラス値はエラーを示し、SQL_ERRORの戻り値が伴います。 クラス "IM" は、ODBC 自体の実装から派生した警告とエラーに固有のものです。 どのクラスのサブクラス値 「000」も、その SQLSTATE にサブクラスがないことを示します。 クラス値とサブクラス値の割り当ては、SQL-92 で定義されます。  
  
> [!NOTE]  
>  関数の正常な実行は、通常はSQL_SUCCESSの戻り値で示されますが、SQLSTATE 00000 も成功を示します。  
  
|SQLSTATE|エラー|から返すことができます|  
|--------------|-----------|--------------------------|  
|01000|一般的な警告|以下を除くすべての ODBC 関数<br /><br /> **エラー**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|01001|カーソル操作の競合|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01002|切断エラー|**接続解除**|  
|01003|セット関数で削除された NULL 値|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|文字列データ(右切り捨て)|**SQLBrowseConnect**<br /><br /> **オペレーション**<br /><br /> **SQLColAttribute**<br /><br /> **データベースソース**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **アズ・ビジトル**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **を指定します。**<br /><br /> **SQL パラムデータ**<br /><br /> **SQLPutData**<br /><br /> **カーソルを設定します。**|  
|01006|特権が取り消されない|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|特権が付与されていません|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|無効な接続文字列属性|**SQLBrowseConnect**<br /><br /> **コネック**|  
|01S01|行内エラー|**オペレーション**<br /><br /> **フェッチ**<br /><br /> **SQLSetPos**|  
|01S02|オプション値が変更されました|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01S06|結果セットが最初の行セットを返す前にフェッチを試みる|**フェッチ**<br /><br /> **SQLFetchScroll**|  
|01S07|分数切り捨て|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01S08|ファイル DSN の保存中にエラーが発生しました|**SQLDriverConnect**|  
|01S09|無効なキーワード|**SQLDriverConnect**|  
|07001|パラメータの数が正しくありません|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|COUNT フィールドが正しくありません|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|準備済みステートメントは*カーソル指定ではありません。*|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|制限付きデータ型属性違反|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|07009|記述子インデックスが無効です|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **オペレーション**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **をクリックします。**|  
|07S01|既定のパラメーターの使用が無効です|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|クライアントが接続を確立できない|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|使用中の接続名|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|接続が開かない|**ハンドル**<br /><br /> **接続解除**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|サーバーは接続を拒否しました|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|トランザクション中の接続エラー|**SQLEndTran**|  
|08S01|通信リンクの障害|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **を使用する**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21S01|値リストが列リストと一致しません|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21S02|派生テーブルの次数が列リストと一致しません|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|22001|文字列データ(右切り捨て)|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetPos**|  
|22002|インジケーター変数が必要ですが、指定されていません|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|範囲外の数値|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22007|日付/時刻形式が無効です|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22008|日時フィールドのオーバーフロー|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **データ**<br /><br /> **SQLPutData**|  
|22012|ゼロ除算|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|間隔フィールドのオーバーフロー|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22018|キャスト指定に無効な文字値|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22019|無効なエスケープ文字|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|無効なエスケープ シーケンス|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|文字列データの長さが合致しません|**SQLParamData**|  
|23000|整合性制約違反|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|24000|カーソル状態が無効|**オペレーション**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **カーソルを設定します。**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|トランザクション状態が無効|**接続解除**|  
|25S01|トランザクションの状態|**SQLEndTran**|  
|25S02|トランザクションはアクティブです|**SQLEndTran**|  
|25S03|トランザクションがロールバックされる|**SQLEndTran**|  
|28000|無効な承認仕様|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|カーソル名が無効|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **カーソルを設定します。**|  
|3C000|カーソル名が重複しています|**カーソルを設定します。**|  
|3D000|無効なカタログ名です|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F000|無効なスキーマ名です|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|シリアル化の失敗|**オペレーション**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|整合性制約違反|**SQLEndTran**|  
|40003|ステートメントの完了が不明です|**オペレーション**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|構文エラーまたはアクセス違反|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|42S01|ベース テーブルまたはビューは既に存在します|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S02|ベース テーブルまたはビューが見つかりません|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S11|インデックスは既に存在します|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S12|インデックスが見つかりません|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S21|列は既に存在します|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S22|列が見つかりません|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|WITH CHECK OPTION 違反|**オペレーション**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY000|一般的なエラー|以下を除くすべての ODBC 関数<br /><br /> **エラー**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY001|メモリ割り当てエラー|以下を除くすべての ODBC 関数<br /><br /> **エラー**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY003|無効なアプリケーション バッファ タイプ|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|無効な SQL データ型|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|関連付けられたステートメントは準備されていません|**を使用する**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008|操作がキャンセルされました|非同期処理が可能なすべての ODBC 関数:<br /><br /> **SQLBrowseConnect**<br /><br /> **オペレーション**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **接続解除**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|無効な null ポインターの使用|**ハンドル**<br /><br /> **SQLBindParameter**<br /><br /> **オペレーション**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **カーソルを設定します。**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|関数シーケンス エラー|**ハンドル**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **オペレーション**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **を使用する**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **接続解除**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **カーソルを設定します。**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011|属性を今設定できません|**オペレーション**<br /><br /> **SQLParamData**<br /><br /> **をクリックします。**<br /><br /> **SQLSetStmtAttr**|  
|HY012|トランザクション操作コードが無効です|**SQLEndTran**|  
|HY013|メモリ管理エラー|以下を除くすべての ODBC 関数<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY014|ハンドル数の制限を超えた|**ハンドル**|  
|HY015|カーソル名がありません|**SQLGetCursorName**|  
|HY016|実装行記述子を変更できません|**を使用する**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|自動割り当て記述子ハンドルの無効な使用|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018|サーバーはキャンセル要求を拒否しました|**SQLCancel**|  
|HY019|文字以外のデータとバイナリ以外のデータを分割して送信|**SQLPutData**|  
|HY020|NULL 値を連結しようとしました。|**SQLPutData**|  
|HY021|記述子情報の不一致|**SQLBindParameter**<br /><br /> **を使用する**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|属性値が無効です|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090|無効な文字列またはバッファ長|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **オペレーション**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **データベースソース**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **カーソルを設定します。**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091|記述子フィールド ID が無効です|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092|属性/オプション識別子が無効です|**ハンドル**<br /><br /> **オペレーション**<br /><br /> **を使用する**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **アズ・ビジトル**<br /><br /> **データ**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY095|関数の種類が範囲外です|**SQLGetFunctions**|  
|HY096|無効な情報タイプ|**SQLGetInfo**|  
|HY097|列の種類が範囲外です|**SQLSpecialColumns**|  
|HY098|スコープの種類が範囲外です|**SQLSpecialColumns**|  
|HY099|Null 許容型が範囲外です|**SQLSpecialColumns**|  
|HY100|一意性オプションの種類が範囲外です|**SQLStatistics**|  
|HY101|精度オプションの種類が範囲外です|**SQLStatistics**|  
|HY103|無効な取得コード|**データベースソース**<br /><br /> **SQLDrivers**|  
|HY104|有効桁数または小数点以下桁数の値が無効です|**SQLBindParameter**|  
|HY105|無効なパラメータタイプ|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|フェッチタイプが範囲外です|**フェッチ**<br /><br /> **SQLFetchScroll**|  
|HY107|行の値が範囲外です|**フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLSetPos**|  
|HY109|カーソル位置が無効です|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY110|無効なドライバの完了|**SQLDriverConnect**|  
|HY111|ブックマーク値が無効です|**フェッチ**<br /><br /> **SQLFetchScroll**|  
|ハイク00|オプション機能が実装されていません|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **オペレーション**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **アズ・ビジトル**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|ヒュット00|タイムアウトに達しました|**SQLBrowseConnect**<br /><br /> **オペレーション**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **フェッチ**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|以下を除くすべての ODBC 関数<br /><br /> **SQLDrivers**<br /><br /> **データベースソース**<br /><br /> **アズ・ビジトル**<br /><br /> **SQLSetEnvAttr**|  
|IM001|ドライバはこの機能をサポートしていません|以下を除くすべての ODBC 関数<br /><br /> **ハンドル**<br /><br /> **データベースソース**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|データ ソース名が見つからず、既定のドライバが指定されていません|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|指定されたドライバを読み込めませんでした|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|SQL_HANDLE_ENVでドライバーの**SQLAllocHandle**が失敗しました|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|SQL_HANDLE_DBCでドライバーの**SQLAllocHandle**が失敗しました|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|ドライバーの**SQL セットコネクトツールに**失敗しました|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|データ ソースまたはドライバが指定されていません。ダイアログは禁止されています|**SQLDriverConnect**|  
|IM008|ダイアログが失敗しました|**SQLDriverConnect**|  
|IM009|変換 DLL を読み込めません|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|データ ソース名が長すぎます|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|ドライバ名が長すぎます|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|DRIVER キーワード構文エラー|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|トレース ファイル エラー|すべての ODBC 関数。|  
|IM014|ファイル DSN の名前が無効です|**SQLDriverConnect**|  
|IM015|ファイル データ ソースが壊れています|**SQLDriverConnect**|
