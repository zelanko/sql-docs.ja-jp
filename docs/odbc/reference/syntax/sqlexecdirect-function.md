---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExecDirect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExecDirect
helpviewer_keywords:
- SQLExecDirect function [ODBC]
ms.assetid: 985fcee1-f204-425c-bdd1-deb0e7d7bbd9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5739e397467deb684a4cd6c7b13a507f30b53fa7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286112"
---
# <a name="sqlexecdirect-function"></a>SQLExecDirect 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLExecDirect は**、パラメータがステートメント内に存在する場合は、パラメータ マーカー変数の現在の値を使用して、準備可能なステートメントを実行します。 **SQLExecDirect**は、1 回の実行に対して SQL ステートメントを送信する最も高速な方法です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLExecDirect(  
     SQLHSTMT     StatementHandle,  
     SQLCHAR *    StatementText,  
     SQLINTEGER   TextLength);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *ステートメントテキスト*  
 [入力]実行される SQL ステートメント。  
  
 *TextLength*  
 [入力]**文字のテキスト*の長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、SQL_NO_DATA、SQL_INVALID_HANDLE、またはSQL_PARAM_DATA_AVAILABLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLExecDirect が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec***を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLExecDirect**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01001|カーソル操作の競合|\**ステートメントテキストに*位置指定更新ステートメントまたは削除ステートメントが含まれていて、更新または削除された行が 1 行も含まれていません。 (複数の行に対する更新の詳細については **、SQLSetStmtAttr**のSQL_ATTR_SIMULATE_CURSOR*属性*の説明を参照してください。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01003|セット関数で削除された NULL 値|引数*の StatementText*にはセット関数 **(AVG、MAX、MIN**など) が含まれていましたが **、COUNT**セット関数は含まれておらず、関数が適用される前に NULL 引数値が削除されました。 **MAX** **MIN** (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|入力/出力パラメータまたは出力パラメータに対して返される文字列データまたはバイナリデータは、非ブランク文字または NULL 以外のバイナリデータの切り捨てになります。 文字列値の場合は、右に切り捨てられます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01006|特権が取り消されない|\**ステートメントテキストに* **REVOKE**ステートメントが含まれていて、ユーザーに指定された特権がありません。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01007|特権が付与されていません|ステートメントテキストは**GRANT**ステートメントであり、指定された特権をユーザーに与えることができませんでした。 * \**|  
|01S02|オプション値が変更されました|指定されたステートメント属性は、実装の動作条件のために無効であったため、同様の値が一時的に置換されました。 (**SQLGetStmtAttr**を呼び出して、一時的に置換された値が何であるかを判別できます。代替値は *、ステートメント ハンドル*に対して有効であり、カーソルが閉じられるまでは、ステートメント属性が以前の値に戻ります。 変更できるステートメント属性は次のとおりです。<br /><br /> SQL_ SQL_ ATTR_MAX_ROWS SQL_ SQL_ ATTR_KEYSET_SIZE ATTR_CURSOR_TYPE SQL_ATTR_CONCURRENCYSQL_SQL_SQL_ATTR_SIMULATE_CURSORATTR_QUERY_TIMEOUTATTR_MAX_LENGTHATTR_MAX_LENGTHATTR_MAX_LENGTHATTR_MAX_LENGTHSQL_SQL_<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S07|分数切り捨て|入力/出力または出力パラメーターに返されるデータは、数値データ型の小数部分が切り捨てられたか、時刻、タイム・スタンプ、または間隔のデータ・タイプの時間コンポーネントの小数部分が切り捨てられたために切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07002|COUNT フィールドが正しくありません|**SQLBindParameter**で指定されたパラメーターの数が\**、ステートメント テキスト*に含まれる SQL ステートメント内のパラメーターの数より少ないです。<br /><br /> **パラメーター** *ValuePtr*を null ポインターに設定して呼び出された*StrLen_or_IndPtr、SQL_NULL_DATA*またはSQL_DATA_AT_EXECに設定されていない、*および入力出力型が*SQL_PARAM_OUTPUT に設定されていないので **、SQLBindParameter**で指定されたパラメーターの数が **ステートメント テキスト*に含まれる SQL ステートメントのパラメーター数を超えました。|  
|07006|制限付きデータ型属性違反|バインドされたパラメーターの**SQLBindParameter**の*値型*引数で識別されるデータ値を **、SQLBindParameter**の*引数 ParameterType*で識別されるデータ型に変換できませんでした。<br /><br /> SQL_PARAM_INPUT_OUTPUTまたはSQL_PARAM_OUTPUTとしてバインドされたパラメーターに対して返されたデータ値は **、SQLBindParameter**の引数*ValueType*で識別されるデータ型に変換できませんでした。<br /><br /> (1 つ以上の行のデータ値を変換できなかったが、1 つ以上の行が正常に返された場合、この関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07007|制限されたパラメーター値違反|SQL_PARAM_INPUT_OUTPUT_STREAMパラメーター型は、データをパーツで送受信するパラメーターにのみ使用されます。 このパラメーター型に対しては、入力バインド バッファーは使用できません。<br /><br /> このエラーは、パラメーターの型が\*SQL_PARAM_INPUT_OUTPUT、SQLBindParameter で指定された**SQLBindParameter***StrLen_or_IndPtr*がSQL_NULL_DATA、SQL_DEFAULT_PARAM、SQL_LEN_DATA_AT_EXEC(len)、またはSQL_DATA_AT_EXECと等しくない場合に発生します。|  
|07S01|既定のパラメーターの使用が無効です|**SQLBindParameter**で設定されたパラメーター値がSQL_DEFAULT_PARAMされ、対応するパラメーターに既定値が設定されていません。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|21S01|値リストが列リストと一致しません|\**ステートメントテキストに* **INSERT**ステートメントが含まれていて、挿入する値の数が、派生テーブルの度合いと一致しませんでした。|  
|21S02|派生テーブルの次数が列リストと一致しません|\**ステートメントテキストに* **CREATE VIEW**ステートメントが含まれ、非修飾列リスト (SQL ステートメントの列*ID*引数のビューに指定された列の数) に、SQL ステートメントの*query 指定*引数で定義された派生表の列数よりも多くの名前が含まれていました。|  
|22001|文字列データ、右切り捨て|列に文字またはバイナリ値を割り当てると、空白以外の文字データまたは NULL 以外のバイナリ データが切り捨てられます。|  
|22002|インジケーター変数が必要ですが、指定されていません|**SQLBindParameter**によって設定された*StrLen_or_IndPtr*が NULL ポインターである出力パラメーターに NULL データがバインドされました。|  
|22003|範囲外の数値|**ステートメントテキスト*には、バインドされた数値パラメータまたはリテラルを含む SQL ステートメントが含まれており、値によって、関連付けられたテーブル列に割り当てられると、数値の全体 (小数部ではなく) 部分が切り捨てられました。<br /><br /> 1 つ以上の入出力パラメーターまたは出力パラメーターの数値 (数値またはストリング) を戻すと、数値の全体 (小数部ではなく) 部分が切り捨てられる可能性があります。|  
|22007|日付/時刻形式が無効です|**ステートメントテキスト*には、日付、時刻、またはタイム・スタンプ構造をバインド・パラメーターとして含む SQL ステートメントが含まれており、パラメーターがそれぞれ無効な日付、時刻、またはタイム・スタンプでした。<br /><br /> 入力/出力または出力パラメーターが日付、時刻、またはタイム・スタンプ C の構造体にバインドされており、戻り値の値がそれぞれ無効な日付、時刻、またはタイム・スタンプでした。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|22008|日時フィールドのオーバーフロー|**ステートメントテキスト*には、計算時に無効な日付、時刻、またはタイムスタンプ構造が生成される、日付時刻式を含む SQL ステートメントが含まれていました。<br /><br /> 入力/出力パラメータまたは出力パラメータに対して計算された日時式の結果、無効な日付、時刻、またはタイムスタンプ C の構造体が生成されました。|  
|22012|ゼロ除算|**ステートメントテキストに*、0 による除算を引き起こした算術式を含む SQL ステートメントが含まれていました。<br /><br /> 入力/出力パラメータまたは出力パラメータで計算された算術式の結果、0 で除算されます。|  
|22015|間隔フィールドのオーバーフロー|ステートメントテキストには、間隔 SQL データ型に変換すると有効桁数が失われる正確な数値または間隔パラメータが含まれていました。 * \**<br /><br /> StatementText には、列内の数値データ型に変換しても数値データ型に表現されていない、複数のフィールドを持つ間隔パラメータが含まれていました。 * \**<br /><br /> ステートメントテキストには、間隔 SQL 型に割り当てられたパラメーター データが含まれており、間隔 SQL 型の C 型の値の表現はありませんでした。 * \**<br /><br /> 正確な数値または間隔の SQL タイプであった入出力パラメーターを、間隔 C タイプに割り当てると、有効桁数が失われました。<br /><br /> 入出力パラメーターまたは出力パラメーターがインターバル C 構造に割り当てられたとき、間隔データ構造内のデータの表現はありませんでした。|  
|22018|キャスト指定に無効な文字値|ステートメントテキストには、正確な数値または近似数値、日時、または間隔データ型の C 型が含まれていました。 * \** 列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。<br /><br /> 入出力パラメーターまたは入出力パラメーターが戻された場合、SQL タイプは、正確または近似数値、日時、または間隔データ・タイプでした。C 型はSQL_C_CHAR。列の値がバインドされた SQL 型の有効なリテラルではありません。|  
|22019|無効なエスケープ文字|\**StatementText*を含む SQL ステートメントに含まれている、**LIKE**の述語では、**エスケープ**で、**WHERE**句とエスケープの長さ次の文字**エスケープ**が 1 と等しくありません。|  
|22025|無効なエスケープ シーケンス|\**StatementText*を含む SQL ステートメントに含まれる"**LIKE** _パターン値_ **エスケープ** _エスケープ文字_"で、**WHERE**句、およびパターンの値のエスケープ文字の後の文字が「%」または「_」のいずれか。|  
|23000|整合性制約違反|**ステートメントテキストには*、パラメータまたはリテラルを含む SQL ステートメントが含まれていました。 関連付けられたテーブル列で NOT NULL として定義された列のパラメーター値が NULL であったか、一意の値のみを含む制約付きの列に重複値が指定されたか、その他の整合性制約に違反しました。|  
|24000|カーソル状態が無効|**カーソルは、SQL フェッチ**または SQL フェッチスクロールによって*ステートメント ハンドル*に配置**されました**。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScrollSQL_NO_DATA**返されていない場合、ドライバー ドライバー マネージャーが返す **、SQL_NO_DATA****返された**場合は、ドライバーによって返されます。 **SQLFetch**<br /><br /> カーソルは開かれていたが、*ステートメント ハンドル*に配置されていません。<br /><br /> **ステートメントText*に位置指定更新ステートメントまたは削除ステートメントが含まれており、カーソルは結果セットの開始前または結果セットの終了後に位置付けされました。|  
|34000|カーソル名が無効|**ステートメントText*に位置指定更新または削除ステートメントが含まれていて、実行されているステートメントによって参照されているカーソルが開かれていない。|  
|3D000|無効なカタログ名です|*ステートメント テキスト*で指定されたカタログ名が無効です。|  
|3F000|無効なスキーマ名です|*ステートメント テキスト*で指定されたスキーマ名が無効です。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|42000|構文エラーまたはアクセス違反|\**ステートメントテキストに*、修復できないか、構文エラーが含まれている SQL ステートメントが含まれていました。<br /><br /> ユーザーには、 **StatementText*に含まれる SQL ステートメントを実行する権限がありません。|  
|42S01|ベース テーブルまたはビューは既に存在します|\**ステートメント・テキストに* **CREATE TABLE**ステートメントまたは**CREATE VIEW**ステートメントが含まれ、指定された表名またはビュー名が既に存在します。|  
|42S02|ベース テーブルまたはビューが見つかりません|\**ステートメント・テキストに* **DROP TABLE**ステートメントまたは**DROP VIEW**ステートメントが含まれていて、指定された表名またはビュー名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **ALTER TABLE**ステートメントが含まれていますが、指定されたテーブル名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **CREATE VIEW**ステートメントが含まれていて、照会指定で定義された表名またはビュー名が存在しませんでした。<br /><br /> \**ステートメント テキストに* **CREATE INDEX**ステートメントが含まれていますが、指定されたテーブル名が存在しませんでした。<br /><br /> \**ステートメント・テキストに* **GRANT**ステートメントまたは**REVOKE**ステートメントが含まれていて、指定された表名またはビュー名が存在しませんでした。<br /><br /> \**ステートメント テキストに* **SELECT**ステートメントが含まれていますが、指定されたテーブル名またはビュー名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **DELETE**、**挿入**、または**UPDATE**ステートメントが含まれていて、指定されたテーブル名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **CREATE TABLE**ステートメントが含まれていて、制約で指定されたテーブル (作成中のテーブル以外のテーブルを参照) が存在しませんでした。<br /><br /> \**ステートメント・テキストに* **CREATE SCHEMA**ステートメントが含まれていて、指定された表名またはビュー名が存在しませんでした。|  
|42S11|インデックスは既に存在します|\**ステートメントテキストに* **CREATE INDEX**ステートメントが含まれていて、指定されたインデックス名が既に存在しています。<br /><br /> \**ステートメント・テキストに* **CREATE SCHEMA**ステートメントが含まれていて、指定された索引名が既に存在しています。|  
|42S12|インデックスが見つかりません|\**ステートメントテキストに* **DROP INDEX**ステートメントが含まれていますが、指定されたインデックス名が存在しませんでした。|  
|42S21|列は既に存在します|\**ステートメント・テキスト*に**ALTER TABLE**ステートメントが含まれていて **、ADD**文節で指定された列が固有でないか、または基本表内の既存の列を識別します。|  
|42S22|列が見つかりません|\**ステートメントテキストに* **CREATE INDEX**ステートメントが含まれていて、列リストに指定された 1 つ以上の列名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **GRANT**または**REVOKE**ステートメントが含まれていますが、指定された列名が存在しませんでした。<br /><br /> \**ステートメントテキストに***、SELECT**、**削除**、**挿入**、または**UPDATE**ステートメントが含まれていて、指定された列名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **CREATE TABLE**ステートメントが含まれていて、制約で指定された列 (作成中のテーブル以外のテーブルを参照) が存在しませんでした。<br /><br /> \**ステートメント・テキストに* **CREATE SCHEMA**ステートメントが含まれていますが、指定された列名が存在しませんでした。|  
|44000|WITH CHECK OPTION 違反|引数*の StatementText*には、表示されたテーブルに対して実行された**INSERT**ステートメント、または WITH CHECK **OPTION**を指定して作成されたビュー テーブルから派生したテーブルが含まれており、**その結果、INSERT**ステートメントの影響を受ける 1 つ以上の行が表示テーブルに存在しなくなります。<br /><br /> 引数*の StatementText*には、表示テーブルに対して実行された**UPDATE**ステートメント、または WITH **CHECK OPTION**を指定して作成されたビュー テーブルから派生したテーブルが含まれており **、UPDATE**ステートメントの影響を受ける 1 つ以上の行が表示テーブルに存在しなくなります。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|(DM) **ステートメントテキスト*はヌルポインタでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLExecDirect**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*TextLength*が 0 以下でしたが、SQL_NTSと等しくありません。<br /><br /> **SQLBindParameter**で設定されたパラメーター値が NULL ポインターであり、パラメーター長の値が 0、SQL_NULL_DATA、SQL_DATA_AT_EXEC、SQL_DEFAULT_PARAM、または SQL_LEN_DATA_AT_EXEC_OFFSET 以下の値でした。<br /><br /> **SQLBindParameter**で設定されたパラメーター値が NULL ポインターではありませんでした。C データ型がSQL_C_BINARYまたはSQL_C_CHAR。パラメータ長の値が 0 未満であったが、SQL_NTS、SQL_NULL_DATA、SQL_DATA_AT_EXEC、SQL_DEFAULT_PARAM、またはSQL_LEN_DATA_AT_EXEC_OFFSET以下の値ではありませんでした。<br /><br /> **SQLBindParameter**によってバインドされたパラメーター長の値がSQL_DATA_AT_EXECに設定されました。SQL 型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型です。**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報の種類は "Y" でした。|  
|HY105|無効なパラメータタイプ|**引数** *InputOutputType*に指定された値がSQL_PARAM_OUTPUTされ、パラメーターが入力パラメーターでした。|  
|HY109|カーソル位置が無効です|\**ステートメントテキストに*位置指定更新または削除ステートメントが含まれており、カーソルが削除された行またはフェッチできなかった行に **(SQLSetPos**または**SQLFetchScroll**によって) 配置されました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 アプリケーションは、データ ソースに SQL ステートメントを送信する**SQLExecDirect**を呼び出します。 直接実行の詳細については、「[直接](../../../odbc/reference/develop-app/direct-execution-odbc.md)実行」を参照してください。 ドライバーは、データ ソースで使用される SQL の形式を使用してステートメントを変更し、データ ソースに送信します。 特に、ドライバーは、SQL の特定の機能を定義するために使用されるエスケープ シーケンスを変更します。 エスケープ シーケンスの構文については[、「ODBC でのエスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」を参照してください。  
  
 アプリケーションは、SQL ステートメントに 1 つ以上のパラメーター・マーカーを組み込むことができます。 パラメーター・マーカーを組み込むために、アプリケーションは、SQL ステートメント内の適切な位置に疑問符 (?) を埋め込みます。 パラメータの詳細については、「[ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
 SQL ステートメントが**SELECT**ステートメントであり、アプリケーションが**SQLSetCursorName**という名前の場合、カーソルをステートメントに関連付ける場合、ドライバーは指定されたカーソルを使用します。 それ以外の場合、ドライバーはカーソル名を生成します。  
  
 データ ソースが手動コミット モード (明示的なトランザクション開始を必要とする) で、トランザクションがまだ開始されていない場合、ドライバーは SQL ステートメントを送信する前にトランザクションを開始します。 詳細については、「[手動コミット モード](../../../odbc/reference/develop-app/manual-commit-mode.md)」を参照してください。  
  
 アプリケーションが**SQLExecDirect**を使用して**COMMIT**ステートメントまたは**ROLLBACK**ステートメントを実行する場合、DBMS 製品間で相互運用することはできません。 トランザクションをコミットまたはロールバックするには、アプリケーションが**SQLEndTran**を呼び出します。  
  
 **SQLExecDirect が**実行時データ パラメーターを検出すると、SQL_NEED_DATA返されます。 アプリケーションは **、SQLParamData**と**SQLPutData**を使用してデータを送信します。 [「SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) [、SQLParamData、SQLPutData](../../../odbc/reference/syntax/sqlparamdata-function.md)、および[長いデータの送信](../../../odbc/reference/develop-app/sending-long-data.md)」を参照してください。 [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)  
  
 **SQLExecDirect**が、データ ソースの行に影響を与えない検索された更新、挿入、または削除ステートメントを実行すると **、SQLExecDirect**の呼び出しはSQL_NO_DATA返します。  
  
 SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きく、SQL ステートメントに少なくとも 1 つのパラメーター マーカーが含まれている場合 **、SQLExecDirect**は **、SQLBindParameter**の呼び出しで*引数 ParameterValuePointer*によって指される配列のパラメーター値のセットごとに SQL ステートメントを 1 回実行します。 詳細については、「[パラメータ値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)」を参照してください。  
  
 ブックマークが有効で、ブックマークをサポートできないクエリが実行された場合、ドライバーは、属性値を変更し、SQLSTATE 01S02 (オプション値が変更されました) を返すことによって、ブックマークをサポートする環境に強制する必要があります。 属性を変更できない場合、ドライバーは SQLSTATE HY024 (無効な属性値) を返す必要があります。  
  
> [!NOTE]  
>  接続プールを使用する場合、アプリケーションは、データベースまたはデータベースのコンテキストを変更する SQL ステートメントを実行してはな**USE**_database_りません。  
  
## <a name="code-example"></a>コード例  
 [「SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md) [、SQLGetData、](../../../odbc/reference/syntax/sqlgetdata-function.md)および[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|コミットまたはロールバック操作の実行|[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|カーソル名を返す|[SQLGetCursorName 関数](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|データ列の一部または全部をフェッチする|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|データを送信する次のパラメータを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|実行のためのステートメントの準備|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|実行時にパラメータデータを送信する|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
