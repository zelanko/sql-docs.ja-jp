---
title: 関数を設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 640b1e6947d67b92e2b7f8e623597e1d99d4a877
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299542"
---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **環境**の側面を制御する属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *環境ハンドル*  
 [入力]環境ハンドル。  
  
 *属性*  
 [入力]「コメント」にリストされている、設定する属性。  
  
 *ValuePtr*  
 [入力]*属性*に関連付ける値へのポインター。 *属性*の値に応じて*ValuePtr*は 32 ビット整数値になるか、NULL で終わる文字列を指します。  
  
 *文字列の長さ*  
 [入力]*ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は **ValuePtr*の長さになります。 文字列データの場合、この引数には文字列のバイト数を含める必要があります。  
  
 *ValuePtr*が整数の場合、*文字列長*は無視されます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetEnvAttr**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_ENVの*ハンドル型*と*環境ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は、通常 **、SQLSetEnvAttr**によって返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。 ドライバーが環境属性をサポートしていない場合、エラーは接続時間中にのみ返されます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|ドライバーは *、ValuePtr*で指定された値をサポートしておらず、同様の値を置き換えました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|Attribute 引数は、文字列値を必要とする環境属性を識別し *、ValuePtr*引数は null ポインターです。|  
|HY010|関数シーケンス エラー|(DM) 接続ハンドルが*環境ハンドル*に割り当て済みである。<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION**が設定されていない**SQLSetEnvAttr**と*属性*が**SQL_ATTR_ODBC_VERSION**に等しくありません。 **SQLAllocHandleStd**を使用している場合は **、SQL_ATTR_ODBC_VERSION**を明示的に設定する必要はありません。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY024|属性値が無効です|指定された*属性*値を指定すると *、ValuePtr*に無効な値が指定されました。|  
|HY090|無効な文字列またはバッファ長|*引数*が 0 未満でしたが、SQL_NTSされませんでした。|  
|HY092|属性/オプション識別子が無効です|(DM) 引数*属性*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|引数*Attribute*に指定された値は、ドライバーでサポートされている ODBC のバージョンの有効な ODBC 環境属性でしたが、ドライバーでサポートされていませんでした。<br /><br /> (DM)*属性*引数がSQL_ATTR_OUTPUT_NTSされ *、ValuePtr*がSQL_FALSEされました。|  
  
## <a name="comments"></a>説明  
 アプリケーションは、環境に接続ハンドルが割り当てられていない場合にのみ **、SQLSetEnvAttr**を呼び出すことができます。 環境に対してアプリケーションによって正常に設定されたすべての環境属性は、**環境で SQLFreeHandle**が呼び出されるまで保持されます。 ODBC *3.x*では、複数の環境ハンドルを同時に割り当てることができます。  
  
 *ValuePtr*を使用して設定される情報の形式は、指定された*属性*によって異なります。 **SQLSetEnvAttr**は、2 つの異なる形式の属性情報を受け取ります: NULL で終わる文字ストリングまたは 32 ビット整数値。 それぞれの形式は、属性の説明に記載されています。  
  
 ドライバー固有の環境属性はありません。  
  
 接続属性は **、SQLSetEnvAttr**の呼び出しでは設定できません。 これを行おうとすると、SQLSTATE HY092 (無効な属性/オプション識別子) が返されます。  
  
|*属性*|*値の内容*|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|環境レベルでの接続プールを有効または無効にする 32 ビット SQLUINTEGER 値。 次の値が使用されます。<br /><br /> SQL_CP_OFF = 接続プールはオフになっています。 これは既定値です。<br /><br /> SQL_CP_ONE_PER_DRIVER = 各ドライバーに対して 1 つの接続プールがサポートされます。 プール内のすべての接続は、1 つのドライバーに関連付けられます。<br /><br /> SQL_CP_ONE_PER_HENV = 環境ごとに 1 つの接続プールがサポートされます。 プール内のすべての接続は、1 つの環境に関連付けられます。<br /><br /> SQL_CP_DRIVER_AWARE = ドライバーが使用可能な場合は、接続プール認識機能を使用します。 ドライバーが接続プールの認識をサポートしていない場合、SQL_CP_DRIVER_AWAREは無視され、SQL_CP_ONE_PER_HENVが使用されます。 詳細については、「[ドライバ対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。 一部のドライバーがサポートし、一部のドライバーが接続プールの認識をサポートしていない環境では、SQL_CP_DRIVER_AWAREサポートしているドライバーで接続プール認識機能を有効にすることができますが、接続プール認識機能をサポートしていないドライバーに対してSQL_CP_ONE_PER_HENVを設定するのと同じです。<br /><br /> 接続プールは **、SQLSetEnvAttr**を呼び出してSQL_ATTR_CONNECTION_POOLING属性をSQL_CP_ONE_PER_DRIVERまたはSQL_CP_ONE_PER_HENVに設定することで有効になります。 この呼び出しは、アプリケーションが接続プールを有効にする共有環境を割り当てる前に行う必要があります。 **SQLSetEnvAttr**の呼び出しで環境ハンドルが null に設定され、プロセス レベルの属性SQL_ATTR_CONNECTION_POOLING。 接続プールが有効になると、アプリケーションは *、引数を*SQL_HANDLE_ENV に設定した**SQLAllocHandle**を呼び出して、暗黙的な共有環境を割り当てます。<br /><br /> 接続プールが有効になり、アプリケーションに共有環境が選択された後、この属性を設定するときに**SQLSetEnvAttr**が NULL 環境ハンドルで呼び出されるため、その環境に対してSQL_ATTR_CONNECTION_POOLINGをリセットすることはできません。 共有環境で接続プールが既に有効になっているときにこの属性が設定されている場合、この属性は、その後に割り当てられた共有環境にのみ影響します。<br /><br /> 環境で接続プールを有効にすることもできます。 環境接続プールについては、次の点に注意してください。<br /><br /> - NULL ハンドルで接続プールを有効にすることは、プロセス レベルの属性です。 その後に割り当てられる環境は共有環境になり、プロセス・レベルの接続プール設定を継承します。<br />- 環境が割り当てられた後も、アプリケーションは接続プールの設定を変更できます。<br />- 環境接続プールが有効で、接続のドライバーがドライバー プールを使用する場合、環境プールが優先されます。<br /><br /> SQL_ATTR_CONNECTION_POOLINGは、ドライバー マネージャー内で実装されます。 ドライバーは、SQL_ATTR_CONNECTION_POOLINGを実装する必要はありません。 ODBC 2.0 および 3.0 アプリケーションでは、この環境属性を設定できます。<br /><br /> 詳細については、「 [ODBC Connection Pooling (ODBC 接続プール)](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)」を参照してください。|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|接続プールから接続を選択する方法を決定する 32 ビット SQLUINTEGER 値。 **SQLConnect**または**SQL ドライバ接続**が呼び出されると、ドライバー マネージャーは、プールから再利用される接続を決定します。 ドライバー マネージャーは、呼び出しの接続オプションと、アプリケーションによって設定された接続属性を、プール内の接続のキーワードと接続属性に一致させようとします。 この属性の値によって、一致条件の精度が決まります。<br /><br /> この属性の値を設定するには、次の値を使用します。<br /><br /> SQL_CP_STRICT_MATCH = 呼び出しの接続オプションと正確に一致する接続と、アプリケーションによって設定された接続属性のみが再利用されます。 これは既定値です。<br /><br /> SQL_CP_RELAXED_MATCH = 一致する接続文字列キーワードを持つ接続を使用できます。 キーワードは一致する必要がありますが、すべての接続属性が一致する必要はありません。<br /><br /> ドライバー マネージャーがプールされた接続への接続で一致を実行する方法の詳細については、 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。 接続プールの詳細については[、「ODBC 接続プール](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)」を参照してください。|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|特定の機能が ODBC *2.x*動作を示すか、ODBC *3.x*の動作を示すかを判断する 32 ビットの整数。 この属性の値を設定するには、次の値を使用します。<br /><br /> SQL_OV_ODBC3_80 = ドライバー マネージャーとドライバーは、次の ODBC 3.8 動作を示します。<br /><br /> - ドライバは、日付、時刻、タイムスタンプの ODBC *3.x*コードを返し、期待しています。<br />- SQL**エラー、SQLGetDiagField**、または**SQLGetDiagRec**が呼び出されると、ドライバーは ODBC *3.x* SQLSTATE コードを返**します**。<br />- **SQLTables**の呼び出しで引数*を*引数として指定すると、検索パターンを受け入れます。<br />- ドライバー マネージャーは、C データ型の拡張機能をサポートしています。 C データ型の機能拡張の詳細については[、「ODBC での C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)」を参照してください。<br /><br /> 詳細については[、「ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)」を参照してください。<br /><br /> SQL_OV_ODBC3 = ドライバー マネージャーとドライバーは、次の ODBC *3.x*の動作を示します。<br /><br /> - ドライバは、日付、時刻、タイムスタンプの ODBC *3.x*コードを返し、期待しています。<br />- SQL**エラー、SQLGetDiagField**、または**SQLGetDiagRec**が呼び出されると、ドライバーは ODBC *3.x* SQLSTATE コードを返**します**。<br />- **SQLTables**の呼び出しで引数*を*引数として指定すると、検索パターンを受け入れます。<br />- ドライバー マネージャーは、C データ型の拡張機能をサポートしていません。<br /><br /> SQL_OV_ODBC2 = ドライバー マネージャーとドライバーは、次の ODBC *2.x*の動作を示します。 これは、ODBC *3.x*ドライバを使用する ODBC *2.x*アプリケーションで特に便利です。<br /><br /> - ドライバは、日付、時刻、タイムスタンプに対して ODBC *2.x*コードを返し、期待しています。<br />- SQL**エラー、SQLGetDiagField**、または**SQLGetDiagRec**が呼び出されると、ドライバーは ODBC *2.x* SQLSTATE コードを返**します**。<br />- **SQLTables**の呼び出し*で引数を*引数として指定しても、検索パターンは受け付けりません。<br />- ドライバー マネージャーは、C データ型の拡張機能をサポートしていません。<br /><br /> アプリケーションは、SQLHENV 引数を持つ関数を呼び出す前に、この環境属性を設定する必要があります。 これらの環境フラグに対して追加の動作が存在するかどうかは、ドライバー固有です。<br /><br /> - 詳細については、「[アプリケーションの ODBC バージョン](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)と動作の[変更](../../../odbc/reference/develop-app/behavioral-changes.md)の宣言」を参照してください。|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|ドライバーが文字列データを返す方法を決定する 32 ビットの整数。 SQL_TRUE場合、ドライバーは文字列データ null で終了を返します。 SQL_FALSE場合、ドライバーは文字列データ null で終了を返しません。<br /><br /> この属性はデフォルトでSQL_TRUE。 SQL_TRUEに設定するための**SQLSetEnvAttr**の呼び出しはSQL_SUCCESSを返します。 SQL_FALSEに設定する**SQLSetEnvAttr**の呼び出しは、SQL_ERRORと SQLSTATE HYC00 (オプション機能が実装されていない) を返します。|  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|環境属性の設定を返す|[SQLGetEnvAttr 関数](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
