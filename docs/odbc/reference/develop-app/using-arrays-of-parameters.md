---
title: パラメータの配列を使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 5a28be88-e171-4f5b-bf4d-543c4383c869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b584dc3d635e9fa8ce3228e4e89b0f24451fe165
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306803"
---
# <a name="using-arrays-of-parameters"></a>パラメーターの配列の使用
パラメーターの配列を使用するには、アプリケーションは、パラメーターのセットの数を指定するSQL_ATTR_PARAMSET_SIZEの*属性*引数を使用して**SQLSetStmtAttr**を呼び出します。 エラー セットを含む、処理されたパラメーターのセットの数をドライバーが返すことができる変数のアドレスを指定するSQL_ATTR_PARAMS_PROCESSED_PTRの*属性*引数を使用して**SQLSetStmtAttr**を呼び出します。 パラメータ値の各行のステータス情報を返す配列を指すSQL_ATTR_PARAM_STATUS_PTRの*属性*引数を指定して**SQLSetStmtAttr**を呼び出します。 ドライバーは、ステートメントに対して保持する構造体にこれらのアドレスを格納します。  
  
> [!NOTE]  
>  ODBC 2 で。*x、* パラメータに複数の値を指定するために**SQLParamOptions**が呼び出されました。 ODBC 3 で。*x*を呼び出すと **、SQLServerStmtAttr** **SQLSetStmtAttr**の呼び出しによって、SQL_ATTR_PARAMSET_SIZE属性とSQL_ATTR_PARAMS_PROCESSED_ARRAY属性を設定する呼び出しに置き換えられました。  
  
 ステートメントを実行する前に、アプリケーションはバインドされた各配列の各要素の値を設定します。 ステートメントが実行されると、ドライバーは、パラメーター値を取得し、データ ソースに送信する情報を使用します。可能な場合、ドライバーは配列としてこれらの値を送信する必要があります。 パラメーターの配列の使用は、データ ソースへの 1 回の呼び出しで配列内のすべてのパラメーターを使用して SQL ステートメントを実行することによって実装するのが最善ですが、この機能は、現在の DBMS では広く利用できません。 ただし、ドライバーは、SQL ステートメントを複数回実行して、それぞれ 1 つのパラメーター セットを使用して、それをシミュレートできます。  
  
 アプリケーションがパラメーターの配列を使用する前に、アプリケーションで使用されるドライバーによってサポートされていることを確認する必要があります。 この作業を実行する 2 つの方法があります。  
  
-   パラメーターの配列をサポートするために知られているドライバーのみを使用します。 アプリケーションは、これらのドライバーの名前をハードコードしたり、ユーザーにこれらのドライバーのみを使用するように指示することができます。 カスタム アプリケーションと垂直アプリケーションでは、一般に、限定されたドライバー セットを使用します。  
  
-   実行時にパラメータの配列がサポートされているかどうかを確認します。 ドライバーは、SQL_ATTR_PARAMSET_SIZE ステートメント属性を 1 より大きい値に設定できる場合は、パラメーターの配列をサポートします。 汎用アプリケーションと垂直アプリケーションは、通常、実行時にパラメータの配列をサポートするチェックを行います。  
  
 パラメータ化された実行で行数と結果セットを使用できるかどうかは、SQL_PARAM_ARRAY_ROW_COUNTSオプションとSQL_PARAM_ARRAY_SELECTSオプションを指定して**SQLGetInfo**を呼び出すことによって判断できます。 **INSERT、UPDATE**、および**DELETE**ステートメントの場合、SQL_PARAM_ARRAY_ROW_COUNTSオプションは、個々の行カウント (各パラメーター・セットごとに 1 つずつ) が使用可能かどうか (SQL_PARC_BATCH) か、または行カウントを 1 つにロールアップ (SQL_PARC_NO_BATCH) にするかを示します。 **UPDATE** **SELECT ステートメント**の場合、SQL_PARAM_ARRAY_SELECTS オプションは、パラメーターのセットごとに結果セットを使用できるかどうか (SQL_PAS_BATCH) か、1 つの結果セットだけが使用可能かどうか (SQL_PAS_NO_BATCH) を示します。 ドライバーがパラメーターの配列を使用して実行する結果セットを生成するステートメントを許可しない場合、SQL_PARAM_ARRAY_SELECTSはSQL_PAS_NO_SELECTを返します。 これらのステートメントでパラメーターを使用するデータ ソース固有のものであり、ODBC SQL 文法に従わないため、パラメーターの配列を他の種類のステートメントで使用できるかどうかは、データ ソース固有です。  
  
 SQL_ATTR_PARAM_OPERATION_PTR ステートメント属性によって指される配列を使用して、パラメーターの行を無視できます。 配列の要素がSQL_PARAM_IGNOREに設定されている場合、その要素に対応するパラメーターのセットは **、SQLExecute**または**SQLExecDirect**呼び出しから除外されます。 SQL_ATTR_PARAM_OPERATION_PTR属性が指す配列が割り当てられ、アプリケーションによって入力され、ドライバーによって読み取られます。 フェッチされた行が入力パラメータとして使用される場合、行ステータス配列の値をパラメータ操作配列で使用できます。  
  
## <a name="error-processing"></a>エラー処理  
 ステートメントの実行中にエラーが発生した場合、実行関数はエラーを返し、行番号変数にエラーが含まれている行の番号を設定します。 エラー セットを除くすべての行が実行されるのか、エラー セットの前 (後ではなく) すべての行が実行されるのかは、データ ソース固有です。 このドライバは、パラメータのセットを処理するため、SQL_ATTR_PARAMS_PROCESSED_PTRステートメント属性で指定されたバッファを、現在処理中の行の数に設定します。 エラー セット以外のすべてのセットが実行された場合、ドライバーは、すべての行が処理された後、このバッファーをSQL_ATTR_PARAMSET_SIZEに設定します。  
  
 SQL_ATTR_PARAM_STATUS_PTRステートメント属性が設定されている場合 **、SQLExecute**または**SQLExecDirect**は、パラメーターの各セットの状態を提供する*パラメーターの状態配列*を返します。 パラメーターの状態の配列は、アプリケーションによって割り当てられ、ドライバーによって入力されます。 この要素は、SQL ステートメントがパラメーターの行に対して正常に実行されたかどうか、またはパラメーターのセットの処理中にエラーが発生したかどうかを示します。 エラーが発生した場合、ドライバーは、パラメーターの状態配列に対応する値をSQL_PARAM_ERRORに設定し、SQL_SUCCESS_WITH_INFOを返します。 アプリケーションは、ステータス配列をチェックして、処理された行を特定できます。 行番号を使用すると、アプリケーションはエラーを訂正し、処理を再開することができます。  
  
 パラメーターの状態配列の使用方法は、 **SQLGetInfo**の呼び出しによって返されるSQL_PARAM_ARRAY_ROW_COUNTS オプションとSQL_PARAM_ARRAY_SELECTS オプションによって決まります。 **INSERT、UPDATE**、および**DELETE**ステートメントの場合、SQL_PARC_NO_BATCH SQL_PARAM_ARRAY_ROW_COUNTSに対してSQL_PARC_BATCHが返された場合は、パラメーター状況配列に状況情報が入力されます 。 **UPDATE** **SELECT**ステートメントの場合、パラメーターの状態配列は、SQL_PAS_BATCHがSQL_PARAM_ARRAY_SELECTに対して返される場合に、SQL_PAS_NO_BATCHまたはSQL_PAS_NO_SELECTが返される場合には、入力されます。  
  
## <a name="data-at-execution-parameters"></a>実行時データパラメーター  
 長さ/標識配列内のいずれかの値がSQL_DATA_AT_EXEC、または*SQL_LEN_DATA_AT_EXEC(length)* マクロの結果である場合、それらの値のデータは通常の方法で**SQLPutData**と共に送信されます。 このプロセスの次の側面は、容易に明らかではないので、特別なコメントを負担します。  
  
-   ドライバーは、SQL_NEED_DATAを返すときに、データを必要とする行に行番号変数のアドレスを設定する必要があります。 単一値の場合と同様に、アプリケーションは、ドライバーがパラメーターの単一のセット内のパラメーター値を要求する順序について任意の仮定を行うことはできません。 実行時データ パラメータの実行でエラーが発生した場合、SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性で指定されたバッファーは、エラーが発生した行の番号に設定され、SQL_ATTR_PARAM_STATUS_PTR ステートメント属性で指定された行状態配列の行の状態がSQL_PARAM_ERRORに設定され、SQLExecute、SQLExecDirect、SQLParamData **SQLExecute**、または**SQLExecDirect** **SQLPutData**への呼び出しがSQL_ERROR返します。 **SQLParamData** このバッファーの内容は **、SQL 実行、SQLExecDirect**、または**SQLParamData**がSQL_STILL_EXECUTINGを返す場合は未定義です。 **SQLExecDirect**  
  
-   ドライバーは、実行時のデータ パラメーターの**SQLBindParameter**の引数*のパラメーター*の値を解釈しないため、アプリケーションが配列へのポインターを提供する場合 **、SQLParamData**は抽出し、アプリケーションにこの配列の要素を返しません。 代わりに、アプリケーションが指定したスカラー値を返します。 これは **、SQLParamData**によって返される値が、アプリケーションがデータを送信する必要のあるパラメーターを指定するのに十分ではないことを意味します。また、アプリケーションは現在の行番号も考慮する必要があります。  
  
     パラメーター配列の一部の要素のみが実行時のデータ パラメーターである場合、アプリケーションは、すべてのパラメーターの要素を含む*ParameterValuePtr*の配列のアドレスを渡す必要があります。 この配列は、実行時データパラメーターではないパラメーターに対して、通常解釈されます。 実行時のデータ パラメーターの場合 **、SQLParamData**がアプリケーションに提供する値は、通常、この機会にドライバーが要求しているデータを識別するために使用できる値は、常に配列のアドレスです。
