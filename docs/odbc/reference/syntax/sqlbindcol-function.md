---
title: 関数を実行する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindCol
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90bb1c1aa4dbfa2614f689faa47eb0c41a6cecd6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298742"
---
# <a name="sqlbindcol-function"></a>SQLBindCol 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLBindCol**は、アプリケーションデータバッファーを結果セット内の列にバインドします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLBindCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *ColumnNumber*  
 [入力]バインドする結果セット列の番号。 列は 0 から始まる列の順序を上げる番号が付けられます。 ブックマークを使用しない場合、つまり、SQL_ATTR_USE_BOOKMARKSステートメント属性はSQL_UB_OFFに設定され、列番号は 1 から始まります。  
  
 *Targettype*  
 [入力]\**バッファー*の C データ型の識別子です。 **SQLFetch 、SQLFetchScroll** **、SQLBulkOperations**、**SQLFetchScroll**または**SQLSetPos**を使用してデータ ソースからデータを取得する場合、ドライバーはデータをこの型に変換します。**SQLBulkOperations**または**SQLSetPos**を使用してデータ ソースにデータを送信する場合、ドライバーはこの型からデータを変換します。 有効な C データ型と型識別子の一覧については、「付録 D:[データ型」の「C データ型](../../../odbc/reference/appendixes/c-data-types.md)」セクションを参照してください。  
  
 引数*TargetType*が間隔データ型の場合、ARD のSQL_DESC_DATETIME_INTERVAL_PRECISIONフィールドとSQL_DESC_PRECISIONフィールドで設定されているデフォルトの間隔先行精度 (2) とデフォルトの間隔秒精度 (6) がデータにそれぞれ使用されます。 引数*TargetType*がSQL_C_NUMERIC場合、ARD のSQL_DESC_PRECISIONフィールドとSQL_DESC_SCALE フィールドに設定されている既定の精度 (ドライバー定義) と既定のスケール (0) がデータに使用されます。 デフォルトの精度または位取りが適切でない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**の呼び出しによって適切な記述子フィールドを明示的に設定する必要があります。  
  
 拡張 C データ型を指定することもできます。 詳細については[、「ODBC での C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)」を参照してください。  
  
 *ターゲット値Ptr*  
 [遅延入出力]列にバインドするデータ バッファーへのポインター。 **このバッファーに**データ**を**返します。 **操作が**SQL_FETCH_BY_BOOKMARKされている場合は、このバッファーにデータ*を*返します。*操作*がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKのときに、このバッファーからデータを取得します。 **操作が**SQL_REFRESHされると、このバッファーにデータ*Operation*が返されます。*操作*がSQL_UPDATEされている場合、このバッファーからデータを取得します。  
  
 *TargetValuePtr*が null ポインターの場合、ドライバーは、列のデータ バッファーをアンバインドします。 アプリケーションは、SQL_UNBIND オプションを指定して**SQLFreeStmt**を呼び出すことによって、すべての列のバインドを解除できます。 **SQLBindCol**の呼び出しで *、引数 TargetValuePtr*が null *StrLen_or_IndPtr*ポインターが有効な値である場合、アプリケーションは列のデータ バッファーをアンバインドできますが、列にバインドされた長さ/インジケーター バッファーを持つことができます。  
  
 *BufferLength*  
 [入力]バイト単位の\**ターゲット値Ptr*バッファーの長さ。  
  
 ドライバーは、文字やバイナリ データなどの可変長データを\*返すときに *、TargetValuePtr*バッファーの末尾を超えて書き込みを回避するのには *、BufferLength*を使用します。 ドライバーは、文字データを\**TargetValuePtr*に返すときに、null 終端文字をカウントすることに注意してください。 \*したがって *、TargetValuePtr*には null 終端文字用の領域が含まれている必要があります。  
  
 ドライバーは、整数や日付構造体などの固定長データを返す場合、ドライバーは無視*BufferLength、* バッファーは、データを保持するのに十分な大きさであると仮定します。 したがって、アプリケーションが固定長データに十分な大きさのバッファーを割り当てることが重要であるか、ドライバーがバッファーの末尾を過ぎて書き込みます。  
  
 **バッファー長**が 0 未満の場合は、*バッファー長*が 0 未満の場合は、SQLSTATE HY090 (無効な文字列またはバッファー長) を返します。 *BufferLength* ただし *、TargetType が*文字型を指定する場合、アプリケーションは *、バッファー長*を 0 に設定しないでください。  
  
 *StrLen_or_IndPtr*  
 [遅延入出力]列にバインドする長さ/インジケーター バッファーへのポインター。 **このバッファーに**値**を返します**。 **オペレーションが**SQL_ADD、SQL_UPDATE_BY_BOOKMARK、またはSQL_DELETE_BY_BOOKMARKの場合、このバッファーから値を取得*します*。 **操作が**SQL_FETCH_BY_BOOKMARK場合、このバッファーに値を返*します*。 **操作**がSQL_REFRESH場合は、このバッファーに値*Operation*を返します。*操作*がSQL_UPDATEのときに、このバッファーから値を取得します。  
  
 **SQL フェッチ** **、SQL フェッチスクロール** **、SQLBulk 操作**、および**SQLSetPos**は、長さ/インジケーター バッファーに次の値を返すことができます。  
  
-   返されるデータの長さ  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 アプリケーションは **、SQLBulk オペレーション**または**SQLSetPos**で使用する長さ/インジケーター バッファーに次の値を配置できます。  
  
-   送信されるデータの長さ  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   SQL_LEN_DATA_AT_EXECマクロの結果  
  
-   SQL_COLUMN_IGNORE  
  
 インジケーター バッファーと長さのバッファーが別々のバッファーの場合、インジケーター バッファーはSQL_NULL_DATAのみを返すことができますが、長さバッファーは他のすべての値を返すことができます。  
  
 詳細については、「 [SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQL フェッチ関数](../../../odbc/reference/syntax/sqlfetch-function.md)、 [SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)、および[長さ/インジケーター値の使用](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)」を参照してください。  
  
 *StrLen_or_IndPtr*がヌル・ポインターの場合、長さも標識値も使用されません。 これは、データをフェッチするときにエラーになり、データが NULL です。  
  
 アプリケーションが 64 ビット オペレーティング システムで実行される場合は[、「ODBC 64](../../../odbc/reference/odbc-64-bit-information.md)ビット情報」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLBindCol**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLBindCol**によって返される SQLSTATE 値を一覧表示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|(DM)*引数が*0 で *、TargetType*引数がSQL_C_BOOKMARKまたはSQL_C_VARBOOKMARKされていません。|  
|07009|記述子インデックスが無効です|引数*ColumnNumber*に指定された値が、結果セット内の列の最大数を超えました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|無効なアプリケーション バッファ タイプ|引数*TargetType*は有効なデータ型でもSQL_C_DEFAULTでもありませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLBindCol**が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength*に指定された値が 0 より小さかった。<br /><br /> (DM) ドライバは ODBC 2 です。*x*ドライバー *、ColumnNumber*引数が 0 に設定され、引数*BufferLength*に指定された値が 4 に等しくありません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバーまたはデータ ソースは、*引数の引数*と対応する列のドライバー固有の SQL データ型の組み合わせで指定された変換をサポートしていません。<br /><br /> 引数*ColumnNumber*は 0 であり、ドライバーはブックマークをサポートしていません。<br /><br /> ドライバーは ODBC 2 のみをサポートします。*x*と引数*TargetType*は、次のいずれかでした。<br /><br /> SQL_C_SBIGINTSQL_C_UBIGINTSQL_C_NUMERIC<br /><br /> 「付録 D: データ型」の[C データ型](../../../odbc/reference/appendixes/c-data-types.md)にリストされている間隔 C データ型。<br /><br /> ドライバーは、3.50 より前の ODBC バージョンのみをサポートし、引数*TargetType*がSQL_C_GUIDされました。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 **SQLBindCol**は、結果セット内*の列を*アプリケーションのデータ バッファーおよび長さ/インジケーター バッファーに関連付ける (バインド) するために使用されます。 アプリケーションが SQLFetch 、 **SQLFetchScroll**、または**SQLFetchScroll****SQLSetPos**を呼び出してデータをフェッチすると、ドライバーは指定されたバッファー内のバインドされた列のデータを返します。詳細については、「 [SQL フェッチ関数](../../../odbc/reference/syntax/sqlfetch-function.md)」を参照してください。 アプリケーションが**SQLBulkOperations**を呼び出して行を更新または挿入する場合、または行を更新する**SQLSetPos、** ドライバーは、指定されたバッファーからバインドされた列のデータを取得します。詳細については、「 [SQL バルク操作関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)または[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。 バインディングの詳細については、「[結果の取得 (基本)](../../../odbc/reference/develop-app/retrieving-results-basic.md)」を参照してください。  
  
 列からデータを取得するために列をバインドする必要はありません。 アプリケーションは、列からデータを取得する**SQLGetData**を呼び出すこともできます。 行の一部の列をバインドし、他の列に対して**SQLGetData**を呼び出す場合もありますが、これにはいくつかの制限があります。 詳細については、「 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)」を参照してください。  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>列のバインド、バインド解除、および再バインド  
 結果セットからデータをフェッチした後でも、列はいつでもバインド、バインド解除、または再バインドできます。 新しいバインディングは、バインディングを使用する関数が次回呼び出されると有効になります。 たとえば、アプリケーションが結果セット内の列をバインドし **、SQLFetch**を呼び出すとします。 ドライバーは、バインドされたバッファー内のデータを返します。 ここで、アプリケーションが列を別のバッファー セットにバインドするとします。 ドライバーは、新しくバインドされたバッファーにフェッチされた行のデータを配置しません。 代わりに **、SQLFetch**が再度呼び出されるまで待機し、次の行のデータを新しくバインドされたバッファーに配置します。  
  
> [!NOTE]  
>  列を列 0 にバインドする前に、ステートメント属性SQL_ATTR_USE_BOOKMARKSは必ず設定する必要があります。 これは必須ではありませんが、強くお勧めします。  
  
## <a name="binding-columns"></a>バインディング列  
 列をバインドするには、アプリケーションは**SQLBindCol**を呼び出し、列番号、データ・バッファーのタイプ、アドレス、および長さ、および長さ/インジケーター・バッファーのアドレスを渡します。 これらのアドレスの使用方法については、このセクションの「バッファ アドレス」を参照してください。 列のバインドの詳細については、「 [SQLBindCol の使用](../../../odbc/reference/develop-app/using-sqlbindcol.md)」を参照してください。  
  
 これらのバッファーの使用は据え置かれます。つまり、アプリケーションは**SQLBindCol**でバインドしますが、ドライバーは他の関数 (SQLBulkOperations、SQLFetch、SQLFetchScroll 、または**SQLBulkOperations****SQLFetch****SQLSetPos)** からアクセスします。 **SQLFetchScroll** バインドが有効である限り **、SQLBindCol**で指定されたポインターが有効であることを確認するのは、アプリケーションの役割です。 アプリケーションがこれらのポインターを無効にすることを許可する場合 (バッファーを解放するなど) し、それらを有効と想定する関数を呼び出す場合、結果は未定義になります。 詳細については、「[遅延バッファー](../../../odbc/reference/develop-app/deferred-buffers.md)」を参照してください。  
  
 バインディングは、新しいバインディングに置き換えられるか、列がバインド解除されるか、またはステートメントが解放されるまで有効です。  
  
## <a name="unbinding-columns"></a>列のバインド解除  
 1 つの列のバインドを解除するには、アプリケーションは *、列番号をその*列の番号に設定して**SQLBindCol**を呼び出し *、TargetValuePtr を*null ポインターに設定します。 *列番号が*非バインド列を参照している場合でも **、SQL_SUCCESS**が返されます。  
  
 すべての列のバインドを解除するには、アプリケーションは*fOption を*SQL_UNBIND に設定して**SQLFreeStmt**を呼び出します。 これは、ARD のSQL_DESC_COUNT フィールドをゼロに設定することによっても実現できます。  
  
## <a name="rebinding-columns"></a>列の再バインド  
 アプリケーションは、バインディングを変更するために、次の 2 つの操作のいずれかを実行できます。  
  
-   **SQLBindCol**を呼び出して、既にバインドされている列の新しいバインドを指定します。 ドライバーは、古いバインドを新しいバインドで上書きします。  
  
-   **SQLBindCol**へのバインディング呼び出しで指定されたバッファー アドレスに追加するオフセットを指定します。 詳細については、次の「バインド オフセット」を参照してください。  
  
## <a name="binding-offsets"></a>バインド オフセット  
 バインディング オフセットは、データおよび長さ/インジケーター バッファーのアドレスに追加される値です *(TargetValuePtr*と*StrLen_or_IndPtr*引数で指定されている) が逆参照される前にします。 オフセットを使用する場合、バインドはアプリケーションのバッファーのレイアウト方法の「テンプレート」であり、アプリケーションはオフセットを変更することによってこの 「テンプレート」をメモリの別の領域に移動できます。 各バインディングの各アドレスに同じオフセットが追加されるため、異なる列のバッファー間の相対オフセットは、バッファーの各セット内で同じである必要があります。 これは、行方向のバインドを使用する場合は常に当てはまります。列方向のバインドを使用する場合、アプリケーションは、この値を true にするために、バッファーを慎重にレイアウトする必要があります。  
  
 バインド オフセットを使用すると、基本的には**SQLBindCol**を呼び出して列を再バインドするのと同じ効果があります。 違いは **、SQLBindCol**への新しい呼び出しは、データ バッファーと長さ/インジケーター バッファーの新しいアドレスを指定しますが、バインド オフセットの使用は、アドレスを変更せず、単にそれらにオフセットを追加します。 アプリケーションは、必要なときにいつでも新しいオフセットを指定でき、このオフセットは常に元のバインドされたアドレスに追加されます。 特に、オフセットが 0 に設定されている場合、またはステートメント属性が null ポインターに設定されている場合、ドライバーは、元のバインドされたアドレスを使用します。  
  
 バインディング・オフセットを指定するために、アプリケーションは SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性を SQLINTEGER バッファーのアドレスに設定します。 アプリケーションは、バインディングを使用する関数を呼び出す前に、このバッファーにオフセットをバイト単位で格納します。 使用するバッファーのアドレスを決定するには、ドライバーは、バインド内のアドレスにオフセットを追加します。 アドレスとオフセットの合計は有効なアドレスである必要がありますが、オフセットを追加するアドレスは有効である必要はありません。 バインド オフセットの使用方法の詳細については、このセクションの「バッファー アドレス」を参照してください。  
  
## <a name="binding-arrays"></a>配列のバインド  
 行セットのサイズ (SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値) が 1 より大きい場合、アプリケーションは単一バッファーではなくバッファーの配列をバインドします。 詳細については、「ブロック[カーソル](../../../odbc/reference/develop-app/block-cursors.md)」を参照してください。  
  
 アプリケーションは、次の 2 つの方法で配列をバインドできます。  
  
-   配列を各列にバインドします。 各データ構造 (配列) には単一列のデータが含まれているため、これは*列方向のバインド*と呼ばれます。  
  
-   行全体のデータを保持し、これらの構造体の配列をバインドする構造体を定義します。 各データ構造には 1 つの行のデータが含まれているため、これは*行方向のバインド*と呼ばれます。  
  
 バッファーの各配列には、行セットのサイズと同じ数の要素が必要です。  
  
> [!NOTE]  
>  アプリケーションは、アラインメントが有効であることを確認する必要があります。 配置に関する考慮事項の詳細については、「[位置合わせ](../../../odbc/reference/develop-app/alignment.md)」を参照してください。  
  
## <a name="column-wise-binding"></a>列方向のバインド  
 列方向のバインドでは、アプリケーションは、各列に個別のデータと長さ/インジケーター配列をバインドします。  
  
 列方向のバインディングを使用するには、アプリケーションは最初に SQL_ATTR_ROW_BIND_TYPE ステートメント属性を SQL_BIND_BY_COLUMN に設定します。 (これがデフォルトです。バインドする各列に対して、アプリケーションは次の手順を実行します。  
  
1.  データ バッファー配列を割り当てます。  
  
2.  長さ/インジケーター バッファーの配列を割り当てます。  
  
    > [!NOTE]  
    >  列方向のバインディングを使用するときにアプリケーションが記述子に直接書き込む場合は、長さデータと標識データに別々の配列を使用できます。  
  
3.  次の引数を指定して**SQLBindCol**を呼び出します。  
  
    -   *ターゲット型*は、データ バッファー配列内の 1 つの要素の型です。  
  
    -   *ターゲット値Ptr*は、データ バッファー配列のアドレスです。  
  
    -   *バッファー長*は、データ バッファー配列内の 1 つの要素のサイズです。 *引数 BufferLength*は、データが固定長データの場合は無視されます。  
  
    -   *StrLen_or_IndPtr*は長さ/インジケーター配列のアドレスです。  
  
 この情報の使用方法の詳細については、このセクションの「バッファ アドレス」を参照してください。 列方向のバインドの詳細については、「[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)」を参照してください。  
  
## <a name="row-wise-binding"></a>行方向のバインド  
 行方向のバインドでは、アプリケーションは、バインドする各列のデータと長さ/インジケーター バッファーを含む構造体を定義します。  
  
 行方向のバインドを使用するには、アプリケーションは次の手順を実行します。  
  
1.  データの単一行 (データと長さ/インジケーター バッファーの両方を含む) を保持する構造体を定義し、これらの構造体の配列を割り当てます。  
  
    > [!NOTE]  
    >  行方向のバインドが使用されているときにアプリケーションが記述子に直接書き込む場合は、長さデータと標識データに別々のフィールドを使用できます。  
  
2.  SQL_ATTR_ROW_BIND_TYPEステートメント属性を、単一行のデータを含む構造体のサイズ、または結果列がバインドされるバッファーのインスタンスのサイズに設定します。 長さには、バインドされたすべての列のスペース、および構造体またはバッファーの埋め込みスペースを含めて、バインドされた列のアドレスが指定された長さでインクリメントされるときに、結果が次の行の同じ列の先頭を指していることを確認する必要があります。 ANSI C で*sizeof*演算子を使用する場合、この動作は保証されます。  
  
3.  バインドする各列について、次の引数を指定して**SQLBindCol**を呼び出します。  
  
    -   *ターゲット型*は、列にバインドされるデータ バッファー メンバーの型です。  
  
    -   *TargetValuePtr*は、最初の配列要素内のデータ バッファー メンバーのアドレスです。  
  
    -   *バッファー長*は、データ バッファー メンバーのサイズです。  
  
    -   *StrLen_or_IndPtr*は、バインドされる長さ/標識メンバーのアドレスです。  
  
 この情報の使用方法の詳細については、このセクションの「バッファ アドレス」を参照してください。 列方向のバインドの詳細については、「[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)」を参照してください。  
  
## <a name="buffer-addresses"></a>バッファ アドレス  
 *バッファアドレス*は、データまたは長さ/インジケーターバッファの実際のアドレスです。 ドライバーは、バッファーに書き込む直前にバッファー アドレスを計算します (フェッチ時間中など)。 これは、次の数式から計算され *、TargetValuePtr*で指定されたアドレスと*StrLen_or_IndPtr*引数、バインド オフセット、および行番号が使用されます。  
  
 *バインド アドレス* + *バインド オフセット*+ (*行番号*- 1) x*要素サイズ*)  
  
 ここで、数式の変数は次の表に示すように定義されています。  
  
|変数|説明|  
|--------------|-----------------|  
|*バインド アドレス*|データ バッファーの場合は **、SQLBindCol**で*引数*を指定して指定したアドレス。<br /><br /> 長さ/インジケーター バッファーの場合は、 **SQLBindCol**で*StrLen_or_IndPtr*引数で指定されたアドレス。 詳細については、「記述子と SQLBindCol」セクションの「追加コメント」を参照してください。<br /><br /> バインドされたアドレスが 0 の場合、前の数式で計算されたアドレスが 0 以外の場合でも、データ値は返されません。|  
|*バインド オフセット*|行方向のバインディングが使用される場合、SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性で指定されたアドレスに格納される値。<br /><br /> 列方向のバインディングが使用されている場合、または SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の値が null ポインターの場合、*バインド オフセット*は 0 になります。|  
|*Row Number*|行セット内の行の 1 から数を返します。 単一行フェッチ (デフォルト) の場合、これは 1 です。|  
|*要素サイズ*|バインドされた配列内の要素のサイズ。<br /><br /> 列方向のバインディングが使用される場合、これは長さ/標識バッファーの**sizeof (SQLINTEGER)** です。 データ バッファーの場合、データ型が可変長の場合は**SQLBindCol**の*BufferLength*引数の値、データ型が固定長の場合はデータ型のサイズです。<br /><br /> 行方向のバインディングが使用される場合、これは、データバッファーと長さ/インジケーター・バッファーの両方に対する SQL_ATTR_ROW_BIND_TYPE ステートメント属性の値です。|  
  
## <a name="descriptors-and-sqlbindcol"></a>記述子と SQL バインド・コル  
 以下のセクションでは **、SQLBindCol**が記述子と対話する方法について説明します。  
  
> [!CAUTION]  
>  1 つのステートメントに対して**SQLBindCol**を呼び出すと、他のステートメントに影響を与える可能性があります。 これは、ステートメントに関連付けられた ARD が明示的に割り当てられ、他のステートメントにも関連付けられている場合に発生します。 **SQLBindCol**は記述子を変更するため、この記述子が関連付けられているすべてのステートメントに変更が適用されます。 これが必要な動作でない場合、アプリケーションは**SQLBindCol**を呼び出す前に、他のステートメントからこの記述子を切り離す必要があります。  
  
## <a name="argument-mappings"></a>引数マッピング  
 概念的には **、SQLBindCol**は次の手順を順番に実行します。  
  
1.  ARD ハンドルを取得するために**SQLGetStmtAttr**を呼び出します。  
  
2.  この記述子のSQL_DESC_COUNT フィールドを取得するために**SQLGetDescField**を呼び出し、引数*ColumnNumber*の値がSQL_DESC_COUNTの値を超えた場合は **、SQL_DESC_COUNT**の値を*列番号*に増やします。  
  
3.  次のフィールドに値を割り当てるには **、SQLSetDescField**を複数回呼び出します。  
  
    -   SQL_DESC_TYPEおよびSQL_DESC_CONCISE_TYPEを*TargetType*の値に設定しますが *、TargetType*が日時または間隔のサブタイプの簡潔な識別子の 1 つである場合、SQL_DESC_TYPEそれぞれ SQL_DATETIME またはSQL_INTERVAL に設定されます。SQL_DESC_CONCISE_TYPEを簡潔な識別子に設定します。SQL_DESC_DATETIME_INTERVAL_CODEに対応する日時または間隔のサブコードを設定します。  
  
    -   *TargetType*に応じて、1 つ以上のSQL_DESC_LENGTH、SQL_DESC_PRECISION、SQL_DESC_SCALE、およびSQL_DESC_DATETIME_INTERVAL_PRECISIONを設定します。  
  
    -   SQL_DESC_OCTET_LENGTHフィールドを*BufferLength*の値に設定します。  
  
    -   SQL_DESC_DATA_PTRフィールドを *[ターゲット値*] の値に設定します。  
  
    -   SQL_DESC_INDICATOR_PTR フィールドを*StrLen_or_Ind*の値に設定します。 (次の段落を参照してください。  
  
    -   SQL_DESC_OCTET_LENGTH_PTR フィールドを*StrLen_or_Ind*の値に設定します。 (次の段落を参照してください。  
  
 *StrLen_or_Ind*引数が参照する変数は、標識と長さの両方の情報に使用されます。 フェッチで列の null 値が検出された場合、その値はSQL_NULL_DATAこの変数に格納されます。それ以外の場合は、この変数にデータ長を格納します。 StrLen_or_Ind*として*null ポインターを渡すと、フェッチ操作がデータ長を返さないようになりますが、null 値を検出してSQL_NULL_DATAを返す方法がない場合は、フェッチは失敗します。  
  
 **SQLBindCol**の呼び出しが失敗した場合、ARD に設定される記述子フィールドの内容は未定義になり、ARD のSQL_DESC_COUNTフィールドの値は変更されません。  
  
## <a name="implicit-resetting-of-count-field"></a>COUNT フィールドの暗黙的なリセット  
 **SQL_DESC_COUNT**引数*ColumnNumber*の値がSQL_DESC_COUNTの値を増加させる場合にのみ、値を設定します。 *引数 TargetValuePtr*の値が null ポインターで、ColumnNumber*ColumnNumber*引数の値が SQL_DESC_COUNT (つまり、バインドが最大の列のバインドを解除する場合) と等しい場合、SQL_DESC_COUNTは、残りの最大のバインド列の番号に設定されます。  
  
## <a name="cautions-regarding-sql_default"></a>SQL_DEFAULTに関する注意事項  
 列データを正常に取得するには、アプリケーションバッファー内のデータの長さと開始点をアプリケーションが正しく判別する必要があります。 アプリケーションが明示的な*TargetType*を指定すると、アプリケーションの誤解が簡単に検出されます。 ただし、アプリケーションが SQL_DEFAULTの*TargetType*を指定すると、メタデータの変更から、またはコードを別の列に適用することによって、アプリケーションが意図するデータ型とは異なるデータ型の列に**SQLBindCol**を適用できます。 この場合、アプリケーションは、フェッチされた列データの開始または長さを常に決定しない場合があります。 報告されていないデータ エラーやメモリ違反が発生する可能性があります。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションが顧客テーブルで**SELECT**ステートメントを実行して、顧客 ID、名前、電話番号の結果セットを名前順に返します。 次に **、SQLBindCol**を呼び出して、データの列をローカル バッファーにバインドします。 最後に、アプリケーションは**SQLFetch**を使用してデータの各行をフェッチし、各顧客の名前、ID、および電話番号を出力します。  
  
 その他のコード例については、「 [SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md) [、SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md) [、SQL フェッチスクロール関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)、および[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
```cpp  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 60
  
void show_error() {  
   printf("error\n");  
}  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];  
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {   
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
                  // Bind columns 1, 2, and 3  
                  retcode = SQLBindCol(hstmt, 1, SQL_C_WCHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_WCHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_WCHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (int i=0 ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                     {
                        //replace wprintf with printf
                        //%S with %ls
                        //warning C4477: 'wprintf' : format string '%S' requires an argument of type 'char *'
                        //but variadic argument 2 has type 'SQLWCHAR *'
                        //wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                        printf("%d: %ls %ls %ls\n", i + 1, sCustID, szName, szPhone);  
                    }    
                     else  
                        break;  
                  }  
               }  
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLCancel(hstmt);  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 [「サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)」も参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ステートメントの列バッファーの解放|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|データ列の一部または全部をフェッチする|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|結果セット列の数を返す|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
