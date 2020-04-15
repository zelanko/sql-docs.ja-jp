---
title: SQLGetData を使用して出力パラメータを取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c96a3f9fc81d081ce16fe8e75746aafe8962fd0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294592"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>SQLGetData を使用した出力パラメーターの取得
ODBC 3.8 より前のアプリケーションは、バインドされた出力バッファーを持つクエリの出力パラメーターのみを取得でいました。 ただし、パラメーター値のサイズが非常に大きい場合 (大きなイメージなど) 非常に大きなバッファーを割り当てるのが困難です。 ODBC 3.8 では、出力パラメータをパーツで取得する新しい方法が導入されています。 アプリケーションは、大きなパラメーター値を取得するために、小さなバッファーを使用して**SQLGetData**を複数回呼び出すことができます。 これは、大きな列データを取得する場合と似ています。  
  
 部分で取得する出力パラメーターまたは入出力パラメーターをバインドするには、SQL_PARAM_OUTPUT_STREAMまたはSQL_PARAM_INPUT_OUTPUT_STREAMに設定された*InputOutputType*引数を指定して**SQLBindParameter**を呼び出します。 SQL_PARAM_INPUT_OUTPUT_STREAMを使用すると、アプリケーションは**SQLPutData**を使用してパラメーターにデータを入力し **、SQLGetData**を使用して出力パラメーターを取得できます。 入力データは、事前割り当てバッファーにバインドするのではなく **、SQLPutData**を使用して、実行時データ (DAE) 形式にする必要があります。  
  
 この機能は、ODBC 3.8 アプリケーションまたは再コンパイルされた ODBC 3.x および ODBC 2.x アプリケーションで使用でき、これらのアプリケーションには **、SQLGetData**および ODBC 3.8 ドライバー マネージャーを使用して出力パラメーターを取得できる ODBC 3.8 ドライバーが必要です。 古いアプリケーションで新しい ODBC 機能を使用できるようにする方法については、「[互換性マトリックス](../../../odbc/reference/develop-app/compatibility-matrix.md)」を参照してください。  
  
## <a name="usage-example"></a>使用例  
 たとえば、両方のパラメータがSQL_PARAM_OUTPUT_STREAMとしてバインドされ、ストアド プロシージャが結果セットを返さないストアド プロシージャ **{CALL sp_f(?,?)} を**実行することを検討してください (このトピックの後半で、より複雑なシナリオが見つかるでしょう)。  
  
1.  各パラメーターに対 SQL_PARAM_OUTPUT_STREAMして、パラメーター番号、データへのポインター、またはアプリケーションが入力パラメーターをバインドするために使用する構造体へのポインターなど、トークン*に設定された* *InputOutputType*を指定して**SQLBindParameter**を呼び出します。 この例では、パラメーター序数をトークンとして使用します。  
  
2.  **クエリを実行**するには、次の操作を**行います**。 SQL_PARAM_DATA_AVAILABLE返され、ストリーム出力パラメーターが取得可能であることを示します。  
  
3.  **SQLParamData**を呼び出して、取得可能なパラメーターを取得します。 **SQLParamData**は、**最初**に使用可能なパラメーターのトークンを持つSQL_PARAM_DATA_AVAILABLEを返します。 トークンは *、ValuePtrPtr*が指すバッファーに返されます。  
  
4.  引数*Col*_or\_を使用して**SQLGetData**を呼び出*Param_Num*パラメーター序数に設定され、最初に使用可能なパラメーターのデータを取得します。 **SQLGetData**が SQL_SUCCESS_WITH_INFOおよび SQLState 01004 (データの切り捨て) を返し、クライアントとサーバーの両方で型が可変長である場合、最初に使用可能なパラメーターから取得するデータが増えます。 SQL_SUCCESSを返すか、別の**SQLState**でSQL_SUCCESS_WITH_INFOするまで **、SQLGetData**を呼び出し続けることができます。  
  
5.  ステップ 3 とステップ 4 を繰り返して、現在のパラメーターを取得します。  
  
6.  もう一度呼び出**します**。 SQL_PARAM_DATA_AVAILABLE以外の何かを返す場合、取得するストリームパラメータデータはもうありません。  
  
7.  **SQLMoreResults**を呼び出して、SQL_NO_DATAを返すまで次のパラメーター セットを処理します。 ステートメント属性 SQL_ATTR_PARAMSET_SIZEが 1 に設定されている場合 **、SQLMoreResults**は、この例ではSQL_NO_DATAを返します。 それ以外の場合 **、SQLMoreResults**はSQL_PARAM_DATA_AVAILABLEを返し、次のパラメーター セットで取得できるストリーム出力パラメーターがあることを示します。  
  
 DAE 入力パラメーターと同様に **、SQLBindParameter**の引数*ParameterValuePtr*で使用されるトークン (手順 1) は、必要に応じて、パラメーターの序数とアプリケーション固有の情報を含むアプリケーション データ構造体を指すポインターにすることができます。  
  
 ストリーム出力または入力/出力パラメーターが返される順序は、ドライバー固有であり、常にクエリで指定された順序と同じではない可能性があります。  
  
 アプリケーションが手順 4 で**SQLGetData**を呼び出さない場合、パラメーター値は破棄されます。 同様に、すべてのパラメーター値が SQLGetData によって読み取られる前にアプリケーションが**SQLParamData**を呼び出した場合、値の残りの部分は破棄され、アプリケーションは次のパラメーターを処理できます。 **SQLGetData**  
  
 ストリーム出力パラメーターがすべて処理される前にアプリケーションが**SQLMoreResults**を呼び出した場合 **(SQLParamData**は引き続きSQL_PARAM_DATA_AVAILABLEを返します)、残りのパラメーターはすべて破棄されます。 同様に、すべてのパラメーター値が**SQLGetData**によって読み取られる前にアプリケーションが**SQLMoreResults**を呼び出した場合、残りの値と残りのすべてのパラメーターは破棄され、アプリケーションは次のパラメーター・セットの処理を続行できます。  
  
 アプリケーションでは **、SQLBindParameter**と**SQLGetData**の両方で C データ型を指定できることに注意してください。 **SQLGetData**で指定された C データ型は **、SQLGetData**で指定された C データ型がSQL_APD_TYPEしない限り **、SQLBindParameter**で指定された C データ型をオーバーライドします。  
  
 出力パラメーターのデータ型が BLOB の場合は、ストリーム出力パラメーターの方が便利ですが、この機能は任意のデータ型でも使用できます。 ストリーム出力パラメーターでサポートされるデータ型は、ドライバーで指定されます。  
  
 処理するパラメーターSQL_PARAM_INPUT_OUTPUT_STREAMがある場合は、**最初**にSQL_NEED_DATA返**されます。** アプリケーションは、DAE パラメーター・データを送信するために**SQLParamData**および**SQLPutData**を呼び出すことができます。 すべての DAE 入力パラメーターが処理されると **、SQLParamData**はSQL_PARAM_DATA_AVAILABLEを返して、ストリーム出力パラメーターが使用可能であることを示します。  
  
 ストリーム出力パラメーターとバインドされた出力パラメーターを処理する場合、ドライバーは、出力パラメーターを処理する順序を決定します。 したがって、出力パラメーターがバッファーにバインドされている場合 **(SQLBindParameter**パラメーター *InputOutputType*がSQL_PARAM_INPUT_OUTPUT またはSQL_PARAM_OUTPUTに設定されている場合)、SQLParamData がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返すまで、バッファーにデータが設定されないことがあります。 **SQLParamData** アプリケーションは、すべてのストリーム出力パラメーターが処理された後に **、SQLParamData**がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返した後にのみ、バインドバッファーを読み取る必要があります。  
  
 データ ソースは、ストリーム出力パラメーターに加えて、警告と結果セットを返すことができます。 一般に、警告と結果セットは **、 SQLMoreResults**を呼び出すことによってストリーム出力パラメーターとは別に処理されます。 ストリーム出力パラメータを処理する前に、警告と結果セットを処理します。  
  
 次の表では、サーバーに送信される 1 つのコマンドのさまざまなシナリオと、アプリケーションの動作について説明します。  
  
|シナリオ|SQL 実行または SQLExecDirect からの戻り値|次の作業|  
|--------------|---------------------------------------------------|---------------------|  
|データにはストリーム出力パラメーターのみが含まれます。|SQL_PARAM_DATA_AVAILABLE|ストリーミング出力パラメーターを取得するには **、SQLParamData**と**SQLGetData**を使用します。|  
|データには結果セットとストリーム出力パラメータが含まれます。|SQL_SUCCESS|**SQL バインドと SQLGet**データを使用して結果セットを取得**します**。<br /><br /> ストリーム出力パラメーターの処理を開始するには **、SQLMoreResults**を呼び出します。 SQL_PARAM_DATA_AVAILABLE返すはずです。<br /><br /> ストリーミング出力パラメーターを取得するには **、SQLParamData**と**SQLGetData**を使用します。|  
|データには警告メッセージとストリーム出力パラメータが含まれています|SQL_SUCCESS_WITH_INFO|警告メッセージを処理するには **、SQLGetDiagRec**と**SQLGetDiagField**を使用します。<br /><br /> ストリーム出力パラメーターの処理を開始するには **、SQLMoreResults**を呼び出します。 SQL_PARAM_DATA_AVAILABLE返すはずです。<br /><br /> ストリーミング出力パラメーターを取得するには **、SQLParamData**と**SQLGetData**を使用します。|  
|データには警告メッセージ、結果セット、ストリーム出力パラメータが含まれます。|SQL_SUCCESS_WITH_INFO|警告メッセージを処理するには **、SQLGetDiagRec**と**SQLGetDiagField**を使用します。 次に **、SQLMoreResults**を呼び出して、結果セットの処理を開始します。<br /><br /> **SQL バインドと SQLGet**データを使用して結果セットを取得**します**。<br /><br /> ストリーム出力パラメーターの処理を開始するには **、SQLMoreResults**を呼び出します。 **結果は**SQL_PARAM_DATA_AVAILABLE返す必要があります。<br /><br /> ストリーミング出力パラメーターを取得するには **、SQLParamData**と**SQLGetData**を使用します。|  
|DAE 入力パラメーターを使用した照会 (例えば、ストリーム入出力 (DAE) パラメーター|SQL NEED_DATA|DAE 入力パラメーター データを送信するには **、SQLParamData**と**SQLPutData**を呼び出します。<br /><br /> すべての DAE 入力パラメーターが処理された後 **、SQLParamData**は **、SQL 実行**および**SQLExecDirect**が返すことができる任意の戻りコードを返すことができます。 このテーブルのケースを適用できます。<br /><br /> 戻りコードがSQL_PARAM_DATA_AVAILABLE場合は、ストリーム出力パラメーターを使用できます。 アプリケーションは、この表の最初の行で説明されているように、ストリーミング出力パラメーターのトークンを取得するために **、SQLParamData**を再度呼び出す必要があります。<br /><br /> 戻りコードがSQL_SUCCESS場合は、処理する結果セットがあるか、処理が完了します。<br /><br /> 戻りコードがSQL_SUCCESS_WITH_INFO場合は、処理する警告メッセージが表示されます。|  
  
 アプリケーション**が**次の**SQLExecDirect**リストにない関数を呼び出すと、SQL_PARAM_DATA_AVAILABLE**が返**されます。  
  
-   **SQLAlloc ハンドル** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQL データ**ソースの SQL ドライバー  
  
-   **SQLGetInfo** / **関数を取得します。**  
  
-   **SQLGetConnectAttr** / **SQL 接続を行** / **SQLGetDescField** / **SQLGetDescRec**う  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField**フィールドを**取得します。**  /   
  
-   **SQLCancel**  
  
-   **(** ステートメント ハンドルを持つ) ハンドルを処理します。  
  
-   **SQLFreeStmt** (オプション = SQL_CLOSE、SQL_DROP、またはSQL_UNBINDを使用)  
  
-   **SQLCloseCursor**  
  
-   **接続解除**  
  
-   **SQL フリーハンドル**(ハンドルタイプ = SQL_HANDLE_STMTを持つ)  
  
-   **SQLGetStmtAttr**  
  
 アプリケーションは、引き続き**SQLSetDescField**または**SQLSetDescRec**を使用してバインディング情報を設定できます。 フィールド マッピングは変更されません。 ただし、記述子の内部のフィールドは、新しい値を返す場合があります。 たとえば、SQL_DESC_PARAMETER_TYPEはSQL_PARAM_INPUT_OUTPUT_STREAMまたはSQL_PARAM_OUTPUT_STREAMを返す場合があります。  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>使用シナリオ: 結果セットから部品内のイメージを取得する  
 **SQLGetData**を使用すると、イメージに関する 1 行のメタデータを含む結果セットがストアド プロシージャから返され、大きな出力パラメータでイメージが返された場合に、データを一部に取得できます。  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>使用シナリオ: ストリーム入出力パラメーターとしてラージ・オブジェクトを送信および受信する  
 **SQLGetData**を使用すると、ストアド プロシージャが大きなオブジェクトを入力/出力パラメータとして渡し、データベースとの間で値をストリーミングするときに、データを一部で取得および送信できます。 メモリ内のすべてのデータを格納する必要はありません。  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>参照  
 [ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)
