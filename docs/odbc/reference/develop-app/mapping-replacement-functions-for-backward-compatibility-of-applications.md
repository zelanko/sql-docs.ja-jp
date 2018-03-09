---
title: "アプリ - ODBC の互換性のための置換関数のマッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping replacement functions [ODBC]
- upgrading applications [ODBC], mapping replacement functions
- compatibility [ODBC], mapping replacement functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], mapping replacement functions
- application upgrades [ODBC], mapping replacement functions
- backward compatibility [ODBC], mapping replacement functions
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c93ea22e03f401580a968dacb1ca15910c7eb44b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>アプリケーションの旧バージョンとの互換性のための置換関数のマップ
ODBC 3*.x* ODBC 3 での作業アプリケーション*.x*ドライバー マネージャーは、ODBC 2 に対して動作します*。x*ドライバー限り、新しい機能は使用されません。 重複している両方の機能および動作の変更を行う方法に影響するただしを ODBC 3 です。*x* ODBC 2 にアプリケーションが動作します*。x*ドライバー。 ODBC 2 を使用場合します。*x*ドライバー、ドライバー マネージャーは、次の ODBC 3 にマップします*。x*関数で、1 つまたは複数の ODBC 2 が置き換えられます*。x*関数は、対応する ODBC 2 にします*。x*関数。  
  
|ODBC 3 です。*x*関数|ODBC 2 です。*x*関数|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**、 **SQLAllocConnect**、または**SQLAllocStmt**|  
|**SQLBulkOperations**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**、 **SQLFreeConnect**、または**SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**SQLGetDiagRec**|**SQLError**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [要求されている属性に応じて、1] の他の処置を実行しても可能性があります。  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 これをドライバー マネージャーは、マップ**SQLAllocEnv**、 **SQLAllocConnect**、または**SQLAllocStmt** をクリックします。 次の呼び出しに**SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 ドライバー マネージャーでは、次を実行すると、(概念、エラー チェックなし) のマッピング。  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 これをドライバー マネージャーは、マップ**SQLSetPos**です。 次の呼び出しに**SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 次の一連の手順で決定されます。  
  
1.  ドライバー マネージャーを呼び出す操作の引数が SQL_ADD の場合は、 **SQLSetPos**次のようにします。  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  操作の引数が SQL_ADD でない場合は、ドライバーは SQLSTATE HY092 を返します (無効な属性またはオプション識別子)。  
  
3.  アプリケーションが呼び出しの間 SQL_ATTR_ROW_STATUS_PTR を変更しようとしたかどうかは**SQLFetch**または**SQLFetchScroll**と**SQLBulkOperations**、ドライバー マネージャーはSQLSTATE HY011 を返す (属性はここで設定することはできません)。  
  
4.  操作の引数が SQL_ADD の場合は、アプリケーションを呼び出す必要があります**SQLBindCol**を挿入するデータをバインドします。 呼び出すことができません**SQLSetDescField**または**SQLSetDescRec**を挿入するデータをバインドします。  
  
5.  操作の引数は、SQL_ADD いて、挿入される行の数が、現在の行セット サイズと同じ**SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の行の数を設定するに呼び出せる必要があります呼び出しの前に挿入された**SQLBulkOperations**です。 前の行セットのサイズに戻すには、アプリケーションが前に SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定する必要があります**SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**と呼びます。  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 これをドライバー マネージャーは、マップ**SQLColAttributes**です。 次の呼び出しに**SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 次の一連の手順で決定されます。  
  
1.  場合*FieldIdentifier*は、次のいずれか。  
  
     SQL_DESC_PRECISION、SQL_DESC_SCALE、SQL_DESC_LENGTH、SQL_DESC_OCTET_LENGTH、SQL_DESC_UNNAMED、SQL_DESC_BASE_COLUMN_NAME、SQL_DESC_LITERAL_PREFIX、SQL_DESC_LITERAL_SUFFIX、または SQL_DESC_LOCAL_TYPE_NAME  
  
     ドライバー マネージャーは、SQLSTATE HY091 の SQL_ERROR が返されます (無効な記述子フィールド識別子)。 このセクションのそれ以降のルールは適用されません。  
  
2.  ドライバー マネージャー SQL_COLUMN_COUNT、SQL_COLUMN_NAME、またはマップ SQL_COLUMN_NULLABLE SQL_DESC_COUNT、SQL_DESC_NAME、または SQL_DESC_NULLABLE、それぞれします。 (ODBC 2*.x*ドライバーのみをサポートする必要 SQL_COLUMN_COUNT SQL_COLUMN_NAME、や SQL_COLUMN_NULLABLE いない SQL_DESC_COUNT、SQL_DESC_NAME、and、SQL_DESC_NULLABLE)。SQLColAttribute への呼び出しにマップされます。  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  他のすべての*FieldIdentifier*値が渡されるを介して、ドライバーで**SQLColAttribute**にマップされている**SQLColAttributes**上記のようにします。  
  
4.  場合*BufferLength*が 0 の場合、ドライバー マネージャーは、SQLSTATE HY090 の SQL_ERROR を返します。 より小さい (無効な文字列長またはバッファー長)。 このセクションのそれ以降のルールは適用されません。  
  
5.  場合*FieldIdentifier* SQL_DESC_CONCISE_TYPE は、返された型は、簡潔な datetime データ型、戻り値は、日付、時刻、およびタイムスタンプのコードについては、ドライバー マネージャー マップします。  
  
6.  ドライバー マネージャーが表示するために必要なチェックを実行するかどうか SQLSTATE HY010 (関数のシーケンス エラー) のニーズが発生します。 ドライバー マネージャーが SQL_ERROR と SQLSTATE HY010 を返すため場合、(関数のシーケンス エラーです)。 このセクションのそれ以降のルールは適用されません。  
  
## <a name="sqlendtran"></a>SQLEndTran  
 これをドライバー マネージャーは、マップ**SQLTransact**です。 次の呼び出しに**SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 ドライバー マネージャーでは、次を実行すると、(概念、エラー チェックなし) のマッピング。  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 これをドライバー マネージャーは、マップ**SQLExtendedFetch**で、 *FetchOrientation* SQL_FETCH_NEXT の引数。 次の呼び出しに**SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 ドライバー マネージャーの呼び出し元になります**SQLExtendedFetch**、次のようにします。  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 この呼び出しで、 *pcRow*引数がアプリケーションへの呼び出しを使用してに SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で設定された値に設定されている**SQLSetStmtAttr**です。  
  
> [!NOTE]  
>  アプリケーションを呼び出すと**SQLSetStmtAttr**状態配列を指す SQL_ATTR_ROW_STATUS_PTR を設定するドライバー マネージャーは、ポインターをキャッシュします。 *RowStatusArray* null ポインターと同じにすることができます。  
  
 ドライバーがサポートしていない場合**SQLExtendedFetch**と、カーソル ライブラリが読み込まれ、ドライバー マネージャーが、カーソル ライブラリを使用して**SQLExtendedFetch**にマップする**SQLFetch**に**SQLExtendedFetch**です。 ドライバーがサポートしていない場合**SQLExtendedFetch**カーソル ライブラリが読み込まれていないと、ドライバー マネージャーへの呼び出しに渡します**SQLFetch**からドライバーにします。 アプリケーションを呼び出す場合**SQLSetStmtAttr** SQL_ATTR_ROW_STATUS_PTR を設定するドライバー マネージャーにより、配列が作成されます。 アプリケーションを呼び出す場合**SQLSetStmtAttr** SQL_ATTR_ROWS_FETCHED_PTR を設定するには、ドライバー マネージャーでは、1 がこのフィールドを設定します。  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 これをドライバー マネージャーは、マップ**SQLExtendedFetch**です。 次の呼び出しに**SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 次の一連の手順で決定されます。  
  
1.  アプリケーションを呼び出すと**SQLSetStmtAttr**状態配列を指す SQL_ATTR_ROW_STATUS_PTR (これは、IRD の SQL_DESC_ARRAY_STATUS_PTR フィールドを設定) を設定するドライバー マネージャーはこのポインターをキャッシュします。 このポインターを使用できます*RowStatusArray*です。 それ以外の場合、使用すると、 *RowStatusArray* null ポインターになります。 場合、 *RowStatusArray*引数が null ポインターに設定されて、ドライバー マネージャーが行状態配列を生成します。  
  
2.  場合*FetchOrientation*は SQL_FETCH_NEXT、SQL_FETCH_PRIOR、SQL_FETCH_ABSOLUTE、SQL_FETCH_RELATIVE、SQL_FETCH_FIRST、SQL_FETCH_LAST、sql_fetch_bookmark を指定してのいずれか、ドライバー マネージャーが SQL_ERROR と SQLSTATE を返しますHY106 (フェッチの範囲外の型)。 このセクションのそれ以降のルールは適用されません。  
  
3.  場合:  
  
-   場合*FetchOrientation*等しく sql_fetch_bookmark を指定して、。  
  
    -   場合**SQLSetStmtAttr** SQL_ATTR_FETCH_BOOKMARK_PTR の値を設定してから、以前のバージョンが呼び出された*bmk ファイルを削除*SQL_DESC_FETCH_BOOKMARK_PTR ポインターの逆参照によって取得される値を指定します。  
  
    -   それ以外の場合、SQLSTATE HY111 で SQL_ERROR を返します (無効なブックマーク値)。 このセクションのそれ以降のルールは適用されません。  
  
     ドライバー マネージャーを呼び出し**SQLExtendedFetch**、次のようにします。  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   それ以外の場合、ドライバー マネージャーを呼び出す**SQLExtendedFetch**、次のようにします。  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     これらの呼び出しで、 *pcRow*引数がアプリケーションへの呼び出しを使用してに SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で設定された値に設定されている**SQLSetStmtAttr**です。  
  
-   SQL_ROWSET_SIZE SQL_ATTR_ROW_ARRAY_SIZE がマップされます。  
  
-   場合*rc*が SQL_SUCCESS または SQL_SUCCESS_WITH_INFO に等しい場合は*FetchOrientation* SQL_FETCH_BOOKMARK と等しいと*FetchOffset*と等しくないを 0 にし、ドライバーは、警告、SQLSTATE 01S10 がポストされます (しようとブックマークのオフセットでフェッチ、オフセット値は無視されます)、および、sql_success_with_info が返されます。  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 これをドライバー マネージャーは、マップ**SQLFreeEnv**、 **SQLFreeConnect**、または**SQLFreeStmt**に応じて。 次の呼び出しに**SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 ドライバー マネージャーでは、次を実行すると、(概念、エラー チェックなし) のマッピング。  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 これをドライバー マネージャーは、マップ**SQLGetConnectOption**です。 次の呼び出しに**SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 次の一連の手順で決定されます。  
  
1.  場合*属性*ドライバーの定義済みの接続やステートメント属性ではないと、ODBC 2 で定義されている属性ではありません*。x*、ドライバー マネージャーで SQLSTATE HY092 の SQL_ERROR が返されます (無効な属性またはオプション識別子)。 ここでそれ以降のルールは適用されません。  
  
2.  場合*属性*SQL_ATTR_AUTO_IPD または SQL_ATTR_METADATA_ID、SQLSTATE HY092 の SQL_ERROR ドライバー マネージャーを返します (無効な属性またはオプション識別子)。  
  
3.  ドライバー マネージャーがかどうかを必要なチェックを実行 SQLSTATE 08003 (接続が開かれていません)、または含む SQLSTATE HY010 (関数のシーケンス エラー) を発生させる必要があります。 場合は、ドライバー マネージャーは SQL_ERROR を返し、該当するエラー メッセージをポストします。 このセクションのそれ以降のルールは適用されません。  
  
4.  ドライバー マネージャー呼び出し**SQLGetConnectOption**次のようにします。  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     なお、 *BufferLength*と*StringLengthPtr*は無視されます。  
  
## <a name="sqlgetdata"></a>SQLGetData  
 ODBC 3 時にします。*x* ODBC 2 作業アプリケーション*.x*ドライバー呼び出し**SQLGetData**で、 *ColumnNumber*引数には 0、ODBC 3*.x*ドライバー マネージャーでは、これをマップへの呼び出しに**SQLGetStmtOption**で、*オプション*属性 SQL_GET_BOOKMARK に設定します。  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 これをドライバー マネージャーは、マップ**SQLGetStmtOption**です。 次の呼び出しに**SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 次の一連の手順で決定されます。  
  
1.  場合*属性*ドライバーの定義済みの接続やステートメント属性ではないと、ODBC 2 で定義されている属性ではありません*。x*、ドライバー マネージャーで SQLSTATE HY092 の SQL_ERROR が返されます (無効な属性またはオプション識別子)。 ここでそれ以降のルールは適用されません。  
  
2.  場合*属性*は、次のいずれか。  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     ドライバー マネージャーで SQLSTATE HY092 の SQL_ERROR が返されます (無効な属性またはオプション識別子)。 このセクションのそれ以降のルールは適用されません。  
  
3.  ドライバー マネージャーが表示するために必要なチェックを実行するかどうか SQLSTATE HY010 (関数のシーケンス エラー) のニーズが発生します。 ドライバー マネージャーが SQL_ERROR と SQLSTATE HY010 を返すため場合、(関数のシーケンス エラーです)。 このセクションのそれ以降のルールは適用されません。  
  
4.  場合*属性*SQL_ATTR_ROWS_FETCHED_PTR、内部のドライバー マネージャーの変数へのポインターをドライバー マネージャー返す等しく*クロウズ*が使用またはへの呼び出しで使用することが**SQLExtendedFetch**です。 このセクションのそれ以降のルールは適用されません。  
  
5.  場合*属性*と等しい SQL_DESC_FETCH_BOOKMARK_PTR には、ドライバー マネージャーの呼び出し中にキャッシュされている必要がある適切のポインターを返します。 **SQLSetStmtAttr**です。  
  
6.  場合*属性*と等しい SQL_ATTR_ROW_STATUS_PTR には、ドライバー マネージャーの呼び出し中にキャッシュされている必要がある適切のポインターを返します。 **SQLSetStmtAttr**です。  
  
7.  ドライバー マネージャー呼び出し**SQLGetStmtOption**次のようにします。  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     ここで*hstmt*、 *fOption*、および*pvParam*の値に設定されます*StatementHandle*、*属性*、および*ValuePtr*、それぞれします。 *BufferLength*と*StringLengthPtr*は無視されます。  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 これをドライバー マネージャーは、マップ**SQLSetConnectOption**です。 次の呼び出しに**SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 次の一連の手順で決定されます。  
  
1.  場合*属性*ドライバーの定義済みの接続やステートメント属性ではないと、ODBC 2 で定義されている属性ではありません*。x*、ドライバー マネージャーで SQLSTATE HY092 の SQL_ERROR が返されます (無効な属性またはオプション識別子)。 ここでそれ以降のルールは適用されません。  
  
2.  場合*属性*SQL_ATTR_AUTO_IPD、ドライバー マネージャーを返しますで SQLSTATE HY092 の SQL_ERROR が (無効な属性またはオプション識別子)。  
  
3.  ドライバー マネージャーが表示するために必要なチェックを実行するかどうか SQLSTATE 08003 (接続が開かれていません)、または含む SQLSTATE HY010 (関数のシーケンス エラー) の必要性が発生します。 これらのエラーのいずれかをする必要がある場合、ドライバー マネージャーは SQL_ERROR を返し、該当するエラー メッセージをポストします。 このセクションのそれ以降のルールは適用されません。  
  
4.  ドライバー マネージャー呼び出し**SQLSetConnectOption**次のようにします。  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     ここで*hdbc*、 *fOption*、および*vParam*の値に設定されます*ConnectionHandle*、*属性*、および*ValuePtr*、それぞれします。 *StringLengthPtr*は無視されます。  
  
> [!NOTE]  
>  接続レベルのステートメント属性を設定する機能は廃止されました。 ODBC 3 接続レベルのステートメント属性を設定しないで必要があります。*x*アプリケーションです。  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 これをドライバー マネージャーは、マップ**SQLSetStmtOption**です。 次の呼び出しに**SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 次の一連の手順で決定されます。  
  
1.  場合*属性*ドライバーの定義済みの接続やステートメント属性ではないと、ODBC 2 で定義されている属性ではありません*。x*、ドライバー マネージャーで SQLSTATE HY092 の SQL_ERROR が返されます (無効な属性またはオプション識別子)。 ここでそれ以降のルールは適用されません。  
  
2.  場合*属性*は、次のいずれか。  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     ドライバー マネージャーで SQLSTATE HY092 の SQL_ERROR が返されます (無効な属性またはオプション識別子)。 このセクションのそれ以降のルールは適用されません。  
  
3.  ドライバー マネージャーを表示するために必要なチェックを実行するかどうかを発生させる SQLSTATE HY010 (関数のシーケンス エラー) が必要です。 ドライバー マネージャーが SQL_ERROR と SQLSTATE HY010 を返すため場合、(関数のシーケンス エラーです)。 このセクションのそれ以降のルールは適用されません。  
  
4.  場合*属性*は、このトピックの「SQL_ATTR_PARAMSET_SIZE または SQL_ATTR_PARAMS_PROCESSED_PTR に一致する「のマッピングの処理、パラメーター配列」セクションを参照してください。 このセクションのそれ以降のルールは適用されません。  
  
5.  場合*属性*が SQL_ATTR_ROWS_FETCHED_PTR、ポインターの値を後で使用できるドライバー マネージャーのキャッシュに等しい**SQLFetchScroll**です。  
  
6.  場合*属性*が SQL_ATTR_ROW_STATUS_PTR、ポインターの値を後で使用できるドライバー マネージャーのキャッシュに等しい**SQLFetchScroll**または**SQLSetPos**です。 このセクションのそれ以降のルールは適用されません。  
  
7.  場合*属性*が SQL_ATTR_FETCH_BOOKMARK_PTR、ドライバー マネージャーのキャッシュに等しい*ValuePtr*への呼び出しの後で、キャッシュされた値が使用**SQLFetchScroll**です。 このセクションのそれ以降のルールは適用されません。  
  
8.  ドライバー マネージャー呼び出し**SQLSetStmtOption**次のようにします。  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     ここで*hstmt*、 *fOption*、および*vParam*の値に設定されます*StatementHandle*、*属性*、および*ValuePtr*、それぞれします。 *StringLength*引数は無視されます。  
  
     ODBC 2 場合。*x*ドライバーは、ODBC 3 文字の文字列、ドライバー固有のステートメントのオプションをサポートしています*。x*アプリケーションを呼び出す必要があります**SQLSetStmtOption**をこれらのオプションを設定します。  
  
## <a name="mappings-for-handling-parameter-arrays"></a>パラメーター配列を処理するためのマッピング  
 アプリケーションを呼び出すとします。  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 ドライバー マネージャーを呼び出します。  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 ドライバー マネージャーがアプリケーションを呼び出すとき、この変数にポインターが後でを返します**SQLGetStmtAttr** SQL_ATTR_PARAMS_PROCESSED_PTR を取得します。 ドライバー マネージャーは、準備済みまたは割り当て済みの状態には、ステートメント ハンドルが返されるまで、この内部変数を変更できません。  
  
 ODBC 3 です。*x*アプリケーションが呼び出すことができます**SQLGetStmtAttr** APD の SQL_DESC_ARRAY_SIZE フィールドを明示的に設定しない場合でも、SQL_ATTR_PARAMS_PROCESSED_PTR の値を取得します。 この状況で発生、たとえば、アプリケーションが現在のパラメーターの「行」をチェックする汎用ルーチンときに処理されている**SQLExecute** SQL_NEED_DATA を返します。 このルーチンが呼び出されるかどうか、SQL_DESC_ARRAY_SIZE 1 が 1 より大きいか。 呼び出されたが、アプリケーションの有無にかかわらず、この内部変数を定義する必要があります、ドライバー マネージャーするために、 **SQLSetStmtAttr** APD の SQL_DESC_ARRAY_SIZE フィールドを設定します。 ドライバー マネージャーが、この変数にはから戻る前に、値 1 が含まれているかどうかを確認 SQL_DESC_ARRAY_SIZE が設定されていない場合**SQLExecDirect**または**SQLExecute**です。  
  
## <a name="error-handling"></a>エラー処理  
 ODBC 3 です。*x*、呼び出し元**SQLFetch**または**SQLFetchScroll** SQL_DESC_ARRAY_STATUS_PTR、IRD と特定の診断レコードの SQL_DIAG_ROW_NUMBER フィールドの追加このレコードに関連する行セットの行の数が含まれています。 これを使用して、アプリケーションは特定の行の位置と、エラー メッセージを関連付けることができます。  
  
 ODBC 2 です。*x*ドライバーをこの機能を提供することはできません。 ただし、SQLSTATE 01S01 でエラー境界を提供する (行でエラー)。 ODBC 3 です。*x*を使用しているアプリケーション**SQLFetch**または**SQLFetchScroll** ODBC 2 を通過するときにします*。x*ドライバーは、この事実に注意する必要があります。 このようなアプリケーションが呼び出すことができるなることにも注意してください**SQLGetDiagField**を実際にはこのまま SQL_DIAG_ROW_NUMBER フィールドを取得します。 ODBC 3 です。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーが呼び出すできる**SQLGetDiagField**でのみ、 *DiagIdentifier* SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE、SQL_DIAG_RETURNCODE、または SQL_DIAG_ の引数SQLSTATE。 ODBC 3*.x*ドライバー マネージャーは、ODBC 2 を使用する場合に、診断データの構造を保持します*。x*ドライバーが、ODBC 2 *。x*ドライバーが 4 つのフィールドのみを返します。  
  
 ODBC 2 時にします。*x* ODBC 2 を利用するアプリケーション*。x*ドライバー、ドライバー マネージャーによって返される複数のエラーが発生することができます、操作の場合さまざまなエラーで返される可能性 ODBC 3*.x*よりも ODBC 2 でのドライバー マネージャー *。x*ドライバー マネージャー。  
  
## <a name="mappings-for-bookmark-operations"></a>ブックマークの操作のマッピング  
 ODBC 3*.x*ドライバー マネージャーは、ODBC 3 時に、次のマッピングを実行します*。x* ODBC 2 を使用するアプリケーション*。x*ドライバーは、ブックマークの操作を実行します。  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 ODBC 3 時にします。*x* ODBC 2 を使用するアプリケーション*。x*ドライバー呼び出し**SQLBindCol**列 0 にバインドする*fCType* SQL_C_VARBOOKMARK、ODBC 3 に等しい*.x*ドライバー マネージャーが確認するにはかどうか、 *BufferLength*引数が 4 より小さいか、4 よりも大きいと、場合は、SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長)。 場合、 *BufferLength*引数が 4 に等しい場合、ドライバー マネージャーを呼び出す**SQLBindCol**に置き換えた後に、ドライバーで*fCType* SQL_C_BOOKMARK とします。  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 ODBC 3 時にします。*x* ODBC 2 を使用するアプリケーション*。x*ドライバー呼び出し**SQLColAttribute**で、 *ColumnNumber*引数は、0 に設定されて、ドライバー マネージャーを返します、 *FieldIdentifier*値次の表に一覧表示されます。  
  
|*FieldIdentifier*|値|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (空の文字列)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|によって返されるのと同じ値**SQLNumResultCols**|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|  
|SQL_DESC_DISPLAY_SIZE|8|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|  
|SQL_DESC_LABEL|"" (空の文字列)|  
|SQL_DESC_LENGTH|0|  
|SQL_DESC_LITERAL_PREFIX|"" (空の文字列)|  
|SQL_DESC_LITERAL_SUFFIX|"" (空の文字列)|  
|SQL_DESC_LOCAL_TYPE_NAME|"" (空の文字列)|  
|SQL_DESC_NAME|"" (空の文字列)|  
|SQL_DESC_NULLABLE|SQL_NO_NULLS|  
|SQL_DESC_OCTET_LENGTH|4|  
|SQL_DESC_PRECISION|4|  
|SQL_DESC_SCALE|0|  
|SQL_DESC_SCHEMA_NAME|"" (空の文字列)|  
|SQL_DESC_SEARCHABLE|SQL_PRED_NONE|  
|SQL_DESC_TABLE_NAME|"" (空の文字列)|  
|SQL_DESC_TYPE|SQL_BINARY|  
|SQL_DESC_TYPE_NAME|"" (空の文字列)|  
|SQL_DESC_UNNAMED|とき|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 ODBC 3 時にします。*x* ODBC 2 を使用するアプリケーション*。x*ドライバー呼び出し**SQLDescribeCol**で、 *ColumnNumber*引数を 0 に設定、ドライバー マネージャーが次の表に示された値を返します。  
  
|バッファー|値|  
|------------|-----------|  
|[ColumnName]|"" (空の文字列)|  
|* NameLengthPtr|0|  
|* DataTypePtr|SQL_BINARY|  
|* ColumnSizePtr|4|  
|* DecimalDigitsPtr|0|  
|* NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 ODBC 3 時にします。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーにより、次の呼び出しに**SQLGetData**ブックマークを取得します。  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 呼び出しがマップされている**SQLGetStmtOption**で、 *fOption*の次のように、SQL_GET_BOOKMARK:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 ここで*hstmt*と*pvParam*内の値に設定されて*StatementHandle*と*TargetValuePtr*、それぞれします。 ブックマークが指すバッファーに返されます、 *pvParam* (*TargetValuePtr*) 引数。 バッファー内の値を指す、 *StrLen_or_IndPtr*への呼び出しで引数**SQLGetData**が 4 に設定します。  
  
 このマッピングは、ケースのアカウントに必要な**SQLFetch**を呼び出す前に呼び出された**SQLGetData**と ODBC 2 *。x*ドライバーがサポートされていませんでした**SQLExtendedFetch**です。 この場合、 **SQLFetch**を通じて、ODBC 2 に渡される*。x*ドライバー、ケースのブックマークの取得はサポートされていません。  
  
 **SQLGetData** ODBC 2 で複数回を呼び出すことができません*。x*呼び出すので、部分内のブックマークを取得するドライバー **SQLGetData**で、 *BufferLength*引数が 4 未満の値に設定され、 *ColumnNumber*引数を 0 に設定するには、SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長)。 **SQLGetData**ただし、同じブックマークを取得する複数回呼び出します。  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 ODBC 3 時にします。*x* ODBC 2 を使用するアプリケーション*。x*ドライバー呼び出し**SQLSetStmtAttr** SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS 属性を設定するにドライバー マネージャーが、基になる ODBC 2 で SQL_UB_ON に属性を設定します*。x*ドライバー。
