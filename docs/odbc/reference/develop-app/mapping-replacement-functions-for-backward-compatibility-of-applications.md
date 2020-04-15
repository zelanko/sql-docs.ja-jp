---
title: アプリケーションの互換性のための代替関数のマッピング - ODBC |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping replacement functions [ODBC]
- upgrading applications [ODBC], mapping replacement functions
- compatibility [ODBC], mapping replacement functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], mapping replacement functions
- application upgrades [ODBC], mapping replacement functions
- backward compatibility [ODBC], mapping replacement functions
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18669fe9b6edbd39859166e382ad18d1b04a99a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301092"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>アプリケーションの旧バージョンとの互換性のためのマッピング置換関数
ODBC *3.x*ドライバー マネージャーを使用して動作する ODBC *3.x*アプリケーションは、新しい機能が使用されていない限り、ODBC *2.x*ドライバーに対して動作します。 ただし、重複した機能と動作の変更は、ODBC *2.x*ドライバでの ODBC *3.x*アプリケーションの動作に影響を与えます。 ODBC *2.x*ドライバーを操作する場合、ドライバー マネージャーは、ODBC *2.x*関数を 1 つ以上置き換えた次の ODBC *3.x*関数を対応する ODBC *2.x*関数にマップします。  
  
|ODBC *3.x*関数|ODBC *2.x*関数|  
|-------------------------|-------------------------|  
|**ハンドル**|**SQLAllocEnv** **、SQLAllocConnect**、または**SQLAllocStmt**|  
|**オペレーション**|**SQLSetPos**|  
|**SQLColAttribute**|**属性**|  
|**SQLEndTran**|**トランスアクト**|  
|**SQLFetch**|**フェッチ**|  
|**SQLFetchScroll**|**フェッチ**|  
|**SQLFreeHandle**|**SQLフリーエンバ、SQL****フリーコネクト**、または**SQLフリーストマウント**|  
|**SQLGetConnectAttr**|**オプションを指定します。**|  
|**SQLGetDiagRec**|**エラー**|  
|**SQLGetStmtAttr**|**オプション**[1]|  
|**SQLSetConnectAttr**|**オプションを指定します。**|  
|**SQLSetStmtAttr**|**オプション**[1]|  
  
 [1] 要求される属性によっては、他のアクションも実行される場合があります。  
  
## <a name="sqlallochandle"></a>ハンドル  
 ドライバー マネージャーは、必要に応じて**これを SQLAllocEnv** **、SQLAllocConnect**、または**SQLAllocStmt**にマップします。 次の呼び出しを**呼**び出します。  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 ドライバー マネージャーは、次の (概念、エラー チェックなし) マッピングを実行します。  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>オペレーション  
 ドライバー マネージャーは **、SQLSetPos**にマップします。 次の呼び出し**を実行します**。  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  操作の引数がSQL_ADD場合、ドライバー マネージャーは、次のように**SQLSetPos**を呼び出します。  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Operation 引数がSQL_ADDされない場合、ドライバーは SQLSTATE HY092 (無効な属性/オプション識別子) を返します。  
  
3.  アプリケーションが SQLFetch または**SQLFetchScroll**と**SQLBulkOperations**の呼び出しの間のSQL_ATTR_ROW_STATUS_PTRを変更しようとすると、ドライバー マネージャーは SQLSTATE HY011 (属性を設定できません) を返します。 **SQLFetchScroll**  
  
4.  Operation 引数がSQL_ADD場合、アプリケーションは**SQLBindCol**を呼び出して、挿入するデータをバインドする必要があります。 挿入するデータ**をバインドするために、SQLSetDescField**または**SQLSetDescRec**を呼び出すことはできません。  
  
5.  引数 Operation がSQL_ADDされ、挿入する行数が現在の行セット サイズと同じでない場合は **、SQLBulkOperations**を呼び出す前に、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を挿入する行数に設定するために**呼**び出す必要があります。 前の行セット サイズに戻すには、**アプリケーションは、SQLFetch 、SQLFetchScroll**、**SQLFetchScroll**または**SQLSetPos**が呼び出される前に、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定する必要があります。  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 ドライバー マネージャーは**SQLCol 属性**にマップします。 次の呼び出しを**SQLCol 属性に対**して行います。  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  *フィールド識別子*が次のいずれかである場合:  
  
     SQL_DESC_PRECISION、SQL_DESC_SCALE、SQL_DESC_LENGTH、SQL_DESC_OCTET_LENGTH、SQL_DESC_UNNAMED、SQL_DESC_BASE_COLUMN_NAME、SQL_DESC_LITERAL_PREFIX、SQL_DESC_LITERAL_SUFFIX、またはSQL_DESC_LOCAL_TYPE_NAME  
  
     ドライバー マネージャーは、SQLSTATE HY091 (無効な記述子フィールド識別子) とSQL_ERRORを返します。 このセクションのこれ以降の規則は適用されません。  
  
2.  ドライバー マネージャーは、SQL_DESC_COUNT、SQL_DESC_NAME、またはSQL_DESC_NULLABLEにそれぞれSQL_COLUMN_COUNT、SQL_COLUMN_NAME、またはSQL_COLUMN_NULLABLEをマップします。 (ODBC *2.x*ドライバは、SQL_COLUMN_COUNT、SQL_COLUMN_NAME、SQL_COLUMN_NULLABLEのみをサポートし、SQL_DESC_COUNT、SQL_DESC_NAME、SQL_DESC_NULLABLEをサポートする必要はありません。SQLCol 属性の呼び出しは、次の値にマップされます。  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  他のすべての*フィールド識別子*の値は、前述のように**SQLCol 属性**にマップされた**SQLCol 属性**を使用して、ドライバーに渡されます。  
  
4.  *BufferLength*が 0 より小さい場合、ドライバー マネージャーは SQLSTATE HY090 (無効な文字列またはバッファーの長さ) とSQL_ERRORを返します。 このセクションのこれ以降の規則は適用されません。  
  
5.  *FieldIdentifier*がSQL_DESC_CONCISE_TYPEされ、返される型が簡潔な日時データ型の場合、ドライバー マネージャーは、日付、時刻、およびタイムスタンプのコードの戻り値をマップします。  
  
6.  ドライバー マネージャーは、SQLSTATE HY010 (関数シーケンス エラー) を発生させる必要があるかどうかを確認するために必要なチェックを実行します。 その場合、ドライバー マネージャーは、SQL_ERRORと SQLSTATE HY010 (関数シーケンス エラー) を返します。 このセクションのこれ以降の規則は適用されません。  
  
## <a name="sqlendtran"></a>SQLEndTran  
 ドライバー マネージャーは、これを**SQLTransact**にマップします。 次の呼び出し**は、SQLEndTran に対して行われます**。  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 ドライバー マネージャーは、次の (概念、エラー チェックなし) マッピングを実行します。  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 ドライバー マネージャーは、SQL_FETCH_NEXTの*フェッチオリエンテーション*引数を使用して**SQLExtendedFetch**にこれをマップします。 次の呼び出しは **、SQLFetch**に対して行われます。  
  
```  
SQLFetch (StatementHandle);  
```  
  
 ドライバー マネージャーは、次のように**SQLExtendedFetch**を呼び出します。  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 この呼び出しでは、*引数 pcRow*が **、アプリケーションが SQLSetStmtAttr**の呼び出しを通じて SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性を設定する値に設定されます。  
  
> [!NOTE]  
>  アプリケーションが**SQLSetStmtAttr**を呼び出して、SQL_ATTR_ROW_STATUS_PTRを状態の配列を指す設定すると、ドライバー マネージャーはポインターをキャッシュします。 *行の状態配列*は、null ポインターに等しいことができます。  
  
 ドライバーが**SQLExtendedFetch**をサポートしていないし、カーソル ライブラリが読み込まれている場合、ドライバー マネージャーは、SQLFetch に**SQLFetch**をマップするのには、カーソル ライブラリの**SQLExtendedFetch**を使用します。 **SQLExtendedFetch** ドライバーが**SQLExtendedFetch**をサポートしていないし、カーソル ライブラリが読み込まれていない場合、ドライバー マネージャーは、ドライバーに**SQLFetch**に呼び出しを渡します。 アプリケーションが SQL_ATTR_ROW_STATUS_PTRを設定するために**SQLSetStmtAttr**を呼び出す場合、ドライバー マネージャーは、配列が設定されていることを確認します。 アプリケーションが**SQLSetStmtAttr**を呼び出してSQL_ATTR_ROWS_FETCHED_PTR設定する場合、ドライバー マネージャーはこのフィールドを 1 に設定します。  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 ドライバー マネージャーは **、これを SQLExtendedFetch**にマップします。 次の呼び出し**は、次の**呼び出しです。  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  アプリケーションが**SQLSetStmtAttr**を呼び出して、状態配列を指すSQL_ATTR_ROW_STATUS_PTR (IRD のSQL_DESC_ARRAY_STATUS_PTR フィールドを設定する) を設定すると、ドライバー マネージャーはこのポインターをキャッシュします。 このポインターを*行状態配列に*します。それ以外の場合は *、RowStatusArray*を null ポインターと等しくします。 引数*RowStatusArray*が null ポインターに設定されている場合、ドライバー マネージャーは、行の状態の配列を生成します。  
  
2.  *FetchOrientation*がSQL_FETCH_NEXT、SQL_FETCH_PRIOR、SQL_FETCH_ABSOLUTE、SQL_FETCH_RELATIVE、SQL_FETCH_FIRST、SQL_FETCH_LAST、またはSQL_FETCH_BOOKMARKの 1 つではない場合、ドライバー マネージャーは、SQL_ERRORと SQLSTATE HY106 (フェッチの種類が範囲外) を返します。 このセクションのこれ以降の規則は適用されません。  
  
3.  大文字と小文字の区別:  
  
-   *フェッチオリエンテーション*がSQL_FETCH_BOOKMARKと等しい場合は、次のようになります。  
  
    -   SQL_ATTR_FETCH_BOOKMARK_PTRの値を設定するために**SQLSetStmtAttr**が呼び出された場合は、ポインタを逆参照して取得した値を*Bmk*にSQL_DESC_FETCH_BOOKMARK_PTR。  
  
    -   それ以外の場合は、SQLSTATE HY111 (無効なブックマーク値) を指定してSQL_ERRORを返します。 このセクションのこれ以降の規則は適用されません。  
  
     ドライバー マネージャーは、次のように**SQLExtendedFetch**を呼び出すようになりました。  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   それ以外の場合、ドライバー マネージャーは次のように**SQLExtendedFetch**を呼び出します。  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     これらの呼び出しでは、*引数 pcRow*が設定され、アプリケーションが**SQLSetStmtAttr**の呼び出しを通じて SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性を設定する値が設定されます。  
  
-   SQL_ATTR_ROW_ARRAY_SIZEはSQL_ROWSET_SIZEにマップされます。  
  
-   *rc*がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOと等しく *、FetchOrientation*が SQL_FETCH_BOOKMARK と等しく *、FetchOffset*が 0 でない場合、ドライバー マネージャーは警告 SQLSTATE 01S10 (ブックマーク オフセットによるフェッチ試行、オフセット値が無視されます) をポストし、SQL_SUCCESS_WITH_INFOを返します。  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 ドライバー マネージャーは、必要に応じて**これを SQLFreeEnv** **、SQLFreeConnect**、または**SQLFreeStmt**にマップします。 次の呼び出しを**SQL フリーハンドルに対して行います**。  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 ドライバー マネージャーは、次の (概念、エラー チェックなし) マッピングを実行します。  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 ドライバー マネージャーは、これを**SQLGetConnect オプション**にマップします。 次の呼び出し**を呼**び出します。  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  *属性*がドライバ定義の接続またはステートメント属性ではなく、ODBC *2.x*で定義された属性でない場合、ドライバ マネージャは SQLSTATE HY092 (無効な属性/オプション識別子) でSQL_ERRORを返します。 このセクションでは、これ以上のルールは適用されません。  
  
2.  *属性*がSQL_ATTR_AUTO_IPDまたはSQL_ATTR_METADATA_IDに等しい場合、ドライバー マネージャーは SQLSTATE HY092 (無効な属性/オプション識別子) とSQL_ERRORを返します。  
  
3.  ドライバー マネージャーは、SQLSTATE 08003 (接続が開いていない) または SQLSTATE HY010 (関数シーケンス エラー) を発生する必要があるかどうかを確認するために必要なチェックを実行します。 その場合、ドライバー マネージャーはSQL_ERRORを返し、適切なエラー メッセージをポストします。 このセクションのこれ以降の規則は適用されません。  
  
4.  ドライバー マネージャーは、次のように**SQLGetConnect オプション**を呼び出します。  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     *バッファー長*と*文字列長Ptr*は無視されることに注意してください。  
  
## <a name="sqlgetdata"></a>SQLGetData  
 ODBC *2.x*ドライバーを処理する ODBC *3.x*アプリケーションが *、引数 ColumnNumber*を 0 に設定して**SQLGetData**を呼び出すと、ODBC *3.x*ドライバー マネージャーは、*オプション*属性を SQL_GET_BOOKMARK に設定した**SQLGetStmtOption**の呼び出しにマップします。  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 ドライバー マネージャーは、これを**SQLGetStmt オプション**にマップします。 次の呼び**出しを**呼び出します。  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  *属性*がドライバ定義の接続またはステートメント属性ではなく、ODBC *2.x*で定義された属性でない場合、ドライバ マネージャは SQLSTATE HY092 (無効な属性/オプション識別子) でSQL_ERRORを返します。 このセクションでは、これ以上のルールは適用されません。  
  
2.  *属性*が次のいずれかである場合:  
  
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
  
     ドライバー マネージャーは、SQLSTATE HY092 (無効な属性/オプション識別子) とSQL_ERRORを返します。 このセクションのこれ以降の規則は適用されません。  
  
3.  ドライバー マネージャーは、SQLSTATE HY010 (関数シーケンス エラー) を発生させる必要があるかどうかを確認するために必要なチェックを実行します。 その場合、ドライバー マネージャーは、SQL_ERRORと SQLSTATE HY010 (関数シーケンス エラー) を返します。 このセクションのこれ以降の規則は適用されません。  
  
4.  *属性*がSQL_ATTR_ROWS_FETCHED_PTRに等しい場合、ドライバー マネージャーは **、使用または SQLExtendedFetch**の呼び出しで使用する内部ドライバー マネージャー変数*cRow*へのポインターを返します。 このセクションのこれ以降の規則は適用されません。  
  
5.  *属性*が SQL_DESC_FETCH_BOOKMARK_PTR に等しい場合、ドライバー マネージャーは**SQLSetStmtAttr**の呼び出し中にキャッシュしていた適切なポインターを返します。  
  
6.  *属性*がSQL_ATTR_ROW_STATUS_PTRに等しい場合、ドライバー マネージャーは**SQLSetStmtAttr**の呼び出し中にキャッシュしていた適切なポインターを返します。  
  
7.  ドライバー マネージャーは、次のように**SQLGetStmt オプション**を呼び出します。  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     ここで *、hstmt*、 *fOption*、および*pvParam*は、それぞれ*ステートメントハンドル*、*属性*、*および ValuePtr*の値に設定されます。 *バッファ長*と*文字列長Ptr*は無視されます。  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 ドライバー マネージャーは、これを**SQLSetConnect オプション**にマップします。 次の呼び出しを**呼**び出します。  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  *属性*がドライバ定義の接続またはステートメント属性ではなく、ODBC *2.x*で定義された属性でない場合、ドライバ マネージャは SQLSTATE HY092 (無効な属性/オプション識別子) でSQL_ERRORを返します。 このセクションでは、これ以上のルールは適用されません。  
  
2.  *属性*がSQL_ATTR_AUTO_IPDに等しい場合、ドライバー マネージャーは SQLSTATE HY092 (無効な属性/オプション識別子) とSQL_ERRORを返します。  
  
3.  ドライバー マネージャーは、SQLSTATE 08003 (接続が開いていない) または SQLSTATE HY010 (関数シーケンス エラー) を発生させる必要があるかどうかを確認するために必要なチェックを実行します。 これらのエラーのいずれかを発生する必要がある場合、ドライバー マネージャーはSQL_ERRORを返し、適切なエラー メッセージをポストします。 このセクションのこれ以降の規則は適用されません。  
  
4.  ドライバー マネージャーは、次のように**SQLSetConnect オプション**を呼び出します。  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     ここで *、 hdbc*、 *fOption*、および*vParam*は、それぞれ*接続ハンドル*、*属性*、*および ValuePtr*の値に設定されます。 *無視*されます。  
  
> [!NOTE]  
>  接続レベルでステートメント属性を設定する機能は廃止されました。 ODBC *3.x*アプリケーションでは、ステートメント属性を接続レベルで設定しないでください。  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 ドライバー マネージャーは、これを**SQLSetStmt オプション**にマップします。 次の呼び出しを**呼**び出します。  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 次の手順のシーケンスが発生します。  
  
1.  *属性*がドライバ定義の接続またはステートメント属性ではなく、ODBC *2.x*で定義された属性でない場合、ドライバ マネージャは SQLSTATE HY092 (無効な属性/オプション識別子) でSQL_ERRORを返します。 このセクションでは、これ以上のルールは適用されません。  
  
2.  *属性*が次のいずれかである場合:  
  
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
  
     ドライバー マネージャーは、SQLSTATE HY092 (無効な属性/オプション識別子) とSQL_ERRORを返します。 このセクションのこれ以降の規則は適用されません。  
  
3.  ドライバー マネージャーは、SQLSTATE HY010 (関数シーケンス エラー) を発生させる必要があるかどうかを確認するために必要なチェックを実行します。 その場合、ドライバー マネージャーは、SQL_ERRORと SQLSTATE HY010 (関数シーケンス エラー) を返します。 このセクションのこれ以降の規則は適用されません。  
  
4.  *Attribute*がSQL_ATTR_PARAMSET_SIZEまたはSQL_ATTR_PARAMS_PROCESSED_PTRの場合は、このトピックの「パラメーター配列を処理するためのマッピング」を参照してください。 このセクションのこれ以降の規則は適用されません。  
  
5.  *属性*がSQL_ATTR_ROWS_FETCHED_PTRに等しい場合、ドライバー マネージャーは、後で**SQLFetchScroll**で使用するためのポインター値をキャッシュします。  
  
6.  *属性*がSQL_ATTR_ROW_STATUS_PTRに等しい場合、ドライバー マネージャーは、後で**SQLFetchScroll**または**SQLSetPos**で使用するためのポインター値をキャッシュします。 このセクションのこれ以降の規則は適用されません。  
  
7.  *属性*がSQL_ATTR_FETCH_BOOKMARK_PTRに等しい場合、ドライバー マネージャーは*ValuePtr*をキャッシュし、後で**SQLFetchScroll**の呼び出しでキャッシュされた値を使用します。 このセクションのこれ以降の規則は適用されません。  
  
8.  ドライバー マネージャーは、次のように**SQLSetStmt オプション**を呼び出します。  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     ここで *、hstmt*、 *fOption*、および*vParam*は、それぞれ*ステートメントハンドル*、*属性*、*および ValuePtr*の値に設定されます。 引数*は*無視されます。  
  
     ODBC *2.x*ドライバーが文字ストリング、ドライバー固有のステートメント・オプションをサポートしている場合、ODBC *3.x*アプリケーションは**SQLSetStmtOption**を呼び出してこれらのオプションを設定する必要があります。  
  
## <a name="mappings-for-handling-parameter-arrays"></a>パラメータ配列を処理するためのマッピング  
 アプリケーションが呼び出す場合:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 ドライバー マネージャーの呼び出し:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 ドライバー マネージャーは、後で、アプリケーションがSQL_ATTR_PARAMS_PROCESSED_PTRを取得する**SQLGetStmtAttr**を呼び出すときに、この変数へのポインターを返します。 ドライバー マネージャーは、ステートメント ハンドルが準備済みまたは割り当てられた状態に返されるまで、この内部変数を変更できません。  
  
 ODBC *3.x*アプリケーションは、APD にSQL_DESC_ARRAY_SIZE フィールドを明示的に設定していない場合でも **、SQLGetStmtAttr**を呼び出してSQL_ATTR_PARAMS_PROCESSED_PTRの値を取得できます。 このような状況は、たとえば **、SQLExecute**がSQL_NEED_DATAを返すときに処理されるパラメーターの現在の行をチェックする汎用ルーチンがアプリケーションにある場合に発生する可能性があります。 このルーチンは、SQL_DESC_ARRAY_SIZEが 1 であるか、1 より大きいかに関係なく呼び出されます。 これを考慮するために、ドライバー マネージャーは、アプリケーションが APD のSQL_DESC_ARRAY_SIZE フィールドを設定する**SQLSetStmtAttr**を呼び出したかどうかに関係なく、この内部変数を定義する必要があります。 SQL_DESC_ARRAY_SIZEが設定されていない場合、ドライバー マネージャーは**SQLExecDirect**または**SQLExecute**から戻る前に、この変数に値 1 が含まれていることを確認する必要があります。  
  
## <a name="error-handling"></a>エラー処理  
 ODBC *3.x*では、呼び出し SQLFetch または**SQLFetchScroll**は IRD のSQL_DESC_ARRAY_STATUS_PTRを設定し、特定の診断レコードのSQL_DIAG_ROW_NUMBER フィールドには、このレコードが関係する行セットの行の番号が含まれています。 **SQLFetchScroll** これを使用して、アプリケーションはエラー メッセージを指定された行位置に関連付けることができます。  
  
 ODBC *2.x*ドライバは、この機能を提供できません。 ただし、SQLSTATE 01S01 (行内エラー) ではエラーの境界が提供されます。 ODBC *2.x*ドライバに対して実行しているときに**SQLFetch**または**SQLFetchScroll**を使用している ODBC *3.x*アプリケーションは、この事実を認識する必要があります。 また、このようなアプリケーションは、実際にSQL_DIAG_ROW_NUMBER フィールドを取得する**SQLGetDiagField**を呼び出すことができないことにも注意してください。 ODBC *2.x*ドライバーを使用する ODBC *3.x*アプリケーションは、SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE、SQL_DIAG_RETURNCODE、またはSQL_DIAG_SQLSTATEの*DiagIdentifier*引数を指定して**のみ SQLGetDiagField**を呼び出すことができるでしょう。 ODBC *3.x*ドライバー マネージャーは、ODBC *2.x*ドライバーを操作するときに診断データの構造を保持しますが、ODBC *2.x*ドライバーは、これらの 4 つのフィールドのみを返します。  
  
 ODBC *2.x*アプリケーションが ODBC *2.x*ドライバを使用して動作している場合、操作によってドライバ マネージャから複数のエラーが返される場合、ODBC 3.x ドライバ マネージャによって ODBC *2.x*ドライバ マネージャで異なるエラーが返されることがあります。 *2.x*  
  
## <a name="mappings-for-bookmark-operations"></a>ブックマーク操作のマッピング  
 ODBC *3.x*ドライバー マネージャーは、ODBC *2.x*ドライバーを操作する ODBC *3.x*アプリケーションがブックマーク操作を実行するときに、次のマッピングを実行します。  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 ODBC *2.x*ドライバーを使用して動作する ODBC *3.x*アプリケーションが、SQL_C_VARBOOKMARKに等しい*fCType*を持つ列 0 にバインドする**SQLBindCol**を呼び出すと、ODBC *3.x*ドライバー マネージャーは *、BufferLength*引数が 4 未満か 4 より大きいかどうかを確認し、その場合は SQLSTATE HY090 (無効な文字列またはバッファーの長さ) を返します。 引数*BufferLength*が 4 に等しい場合、ドライバー マネージャーは、ドライバーで、*ドライバーで、SQL_C_BOOKMARK fCType*を置き換えた後**SQLBindCol**を呼び出します。  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 ODBC *2.x*ドライバーを使用して動作する ODBC *3.x*アプリケーションが *、引数 ColumnNumber*を 0 に設定して**SQLColAttribute**を呼び出すと、ドライバー マネージャーは、次の表に示す*フィールド識別子*の値を返します。  
  
|*FieldIdentifier*|[値]|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (空の文字列)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|返される値と同じ**値**|  
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
|SQL_DESC_UNNAMED|SQL_UNNAMED|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 ODBC *2.x*ドライバーを処理する ODBC *3.x*アプリケーションが引数*ColumnNumber*を 0 に設定して**SQLDescribeCol**を呼び出すと、ドライバー マネージャーは、次の表に示す値を返します。  
  
|バッファー|[値]|  
|------------|-----------|  
|ColumnName|"" (空の文字列)|  
|*名前の長さのPtr|0|  
|*データ型Ptr|SQL_BINARY|  
|*列サイズプター|4|  
|*10 進数桁数Ptr|0|  
|*Null 可能なPtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 ODBC *2.x*ドライバーを使用して動作する ODBC *3.x*アプリケーションが、ブックマークを取得するために**SQLGetData**に次の呼び出しを行うとします。  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 呼び出しは、次のように、SQL_GET_BOOKMARKの*fOption*を使用して**SQLGetStmtOption**にマップされます。  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 ここで *、hstmt*と*pvParam*はそれぞれ*ステートメントハンドル*と*ターゲット値Ptr*の値に設定されます。 ブックマークは *、pvParam* (*TargetValuePtr*) 引数が指すバッファに返されます。 **SQLGetData**の呼び出しで*StrLen_or_IndPtr*引数が指すバッファー内の値は 4 に設定されます。  
  
 このマッピングは **、SQLGetData**の呼び出し前に**SQLFetch**が呼び出され、ODBC *2.x*ドライバーが**SQLExtendedFetch**をサポートしていなかった場合を考慮する必要があります。 この場合 **、SQLFetch**は ODBC *2.x*ドライバーに渡され、その場合、ブックマークの取得はサポートされていません。  
  
 **SQLGetData**は、ODBC *2.x*ドライバーで複数回呼び出してブックマークを取得できないため *、BufferLength*引数を 4 未満に設定し *、ColumnNumber*引数を 0 に設定すると **、SQLSTATE** HY090 (無効な文字列またはバッファー長) が返されます。 ただし **、SQLGetData を**複数回呼び出して、同じブックマークを取得できます。  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 ODBC *2.x*ドライバーを使用して動作する ODBC *3.x*アプリケーションが**SQLSetStmtAttr**を呼び出してSQL_ATTR_USE_BOOKMARKS属性を SQL_UB_VARIABLE に設定すると、ドライバー マネージャーは、基になる ODBC *2.x*ドライバーでSQL_UB_ON属性を設定します。
