---
title: "SQLSetEnvAttr 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f99a9d8a572653be31e74cab00de918f1f51e16
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLSetEnvAttr**環境の側面を制御する属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *EnvironmentHandle*  
 [入力]環境ハンドルです。  
  
 *属性*  
 [入力]属性を設定すると、「コメント」に一覧表示  
  
 *ValuePtr*  
 [入力]関連付けられる値へのポインター*属性*です。 値に応じて*属性*、 *ValuePtr*は 32 ビット整数の値を指定または null で終わる文字列をポイントします。  
  
 *StringLength*  
 [入力]場合*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります **ValuePtr*です。 文字の文字列データでは、この引数は、文字列のバイト数を含める必要があります。  
  
 場合*ValuePtr*整数*StringLength*は無視されます。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetEnvAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_ENV と*処理*の*EnvironmentHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLSetEnvAttr**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。 ドライバーが環境属性をサポートしていない場合は接続時にのみ、エラーが返されます。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーがで指定された値をサポートしていません*ValuePtr*と同様の値を置換します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|属性引数が文字列値を必要とする環境属性を識別し、 *ValuePtr*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM) で、接続ハンドルを割り当てた*EnvironmentHandle*です。<br /><br /> (DM)**また**に設定されていない**SQLSetEnvAttr**と*属性*は等しくありません**また**です。 設定する必要はありません**また**を使用している場合は明示的に**SQLAllocHandleStd**です。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY024|無効な属性値|指定した*属性*値で、無効な値が指定されました*ValuePtr*です。|  
|HY090|文字列またはバッファーの長さが無効です。|*StringLength*引数が 0 未満の値が SQL_NTS ではありません。|  
|HY092|無効な属性またはオプション識別子|引数の指定された値 (DM)*属性*が ODBC ドライバーでサポートされているのバージョンは無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*ODBC 環境の有効な属性が ODBC のバージョンは、ドライバーでサポートされていますが、ドライバーによってサポートされていませんでした。<br /><br /> (DM)、*属性*引数が SQL_ATTR_OUTPUT_NTS、および*ValuePtr* SQL_FALSE がします。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLSetEnvAttr**環境に接続ハンドルが割り当てられていない場合にのみです。 環境のアプリケーションによって設定が正常にすべての環境属性がまで保持**SQLFreeHandle**環境内で呼び出されるとします。 ODBC 3 に、1 つ以上の環境ハンドルを同時に割り当てることができる*.x*です。  
  
 情報の形式がを介して設定*ValuePtr*に指定された依存*属性*です。 **SQLSetEnvAttr**で 2 つの異なる形式のいずれかの属性情報を受け取ります。 null で終わる文字の文字列または 32 ビット整数値。 それぞれの形式は、属性の説明に記録されます。  
  
 ドライバー固有の環境属性はありません。  
  
 呼び出しによって接続属性を設定することはできません**SQLSetEnvAttr**です。 これを実行しようとすると、SQLSTATE HY092 が返されます (無効な属性またはオプション識別子)。  
  
|*属性*|*ValuePtr*内容|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|または、環境のレベルの接続プールを無効にする 32 ビット SQLUINTEGER 値。 次の値が使用されます。<br /><br /> SQL_CP_OFF = 接続プールがオフになっています。 これは既定値です。<br /><br /> SQL_CP_ONE_PER_DRIVER = 1 つの接続プールは、各ドライバーのサポートされています。 プール内のすべての接続は、1 つのドライバーに関連付けられます。<br /><br /> SQL_CP_ONE_PER_HENV = 1 つの接続プールは各環境でサポートされています。 プール内のすべての接続は、1 つの環境に関連付けられます。<br /><br /> SQL_CP_DRIVER_AWARE = 使用可能になる場合は、ドライバーの接続プール認識機能を使用します。 ドライバーが接続プールの認識をサポートしていない場合は、SQL_CP_DRIVER_AWARE は無視され、SQL_CP_ONE_PER_HENV を使用します。 詳細については、次を参照してください。[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。 環境では、ここで一部のドライバー サポートし、一部のドライバーは接続プールの認識をサポートしていません SQL_CP_DRIVER_AWARE には、サポート ドライバー、これらの接続プール認識機能が有効にすることができますがの SQL_CP_ONE_PER_HENV に設定すると等価であります。接続プール認識機能をサポートしているドライバーです。<br /><br /> 呼び出して接続プールが有効になっている**SQLSetEnvAttr** SQL_CP_ONE_PER_DRIVER または SQL_CP_ONE_PER_HENV SQL_ATTR_CONNECTION_POOLING 属性を設定します。 アプリケーションがどの接続のプールを有効にするのには、共有環境を割り当てる前に、この呼び出しを実行する必要があります。 呼び出しで、環境ハンドル**SQLSetEnvAttr** SQL_ATTR_CONNECTION_POOLING プロセス レベルの属性を null に設定されます。 その後、アプリケーションが呼び出すことによって暗黙的な共有環境を割り当てます接続プールを有効にすると、 **SQLAllocHandle**で、 *InputHandle*引数 SQL_HANDLE_ENV に設定します。<br /><br /> 接続プールを有効になっているし、アプリケーションが共有環境が選択されて、SQL_ATTR_CONNECTION_POOLING をリセットできません環境では、ため**SQLSetEnvAttr**が null の環境で呼び出されるこの属性を設定するときに処理します。 この属性は、接続プールが共有環境で既に有効なときに設定されている場合、属性は、その後に割り当てられている共有環境のみに影響します。<br /><br /> 環境での接続プールを有効にすることもできます。 環境の接続プールについて、次に注意してください。<br /><br /> NULL ハンドルのプールの接続を有効化は、プロセス レベルの属性です。 その後に割り当てられている環境は共有環境では、なりプロセス レベルの接続プール設定が継承されます。<br />-環境は、割り当て後、アプリケーションは、接続プール設定を変更できます。<br />-環境接続プールが有効になっているし、接続のドライバーがドライバーのプールを使用して、環境のプールの方 基本設定します。<br /><br /> SQL_ATTR_CONNECTION_POOLING では、ドライバー マネージャーの内部を実装します。 ドライバーは、SQL_ATTR_CONNECTION_POOLING を実装する必要はありません。 ODBC 2.0 および 3.0 アプリケーションは、この環境属性を設定できます。<br /><br /> 詳細については、次を参照してください。 [ODBC 接続プーリング](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)です。|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|接続プールからの接続を選択する方法を決定する 32 ビット SQLUINTEGER 値。 ときに**SQLConnect**または**SQLDriverConnect**が呼び出されると、ドライバー マネージャーを決定する接続がプールから再利用します。 ドライバー マネージャーでは、呼び出しと、キーワードと、接続の接続属性をアプリケーション プール内の設定、接続属性の接続オプションを照合します。 この属性の値では、一致条件の有効桁数のレベルを決定します。<br /><br /> 次の値は、この属性の値の設定に使用されます。<br /><br /> SQL_CP_STRICT_MATCH = 呼び出しで、接続オプションを完全に一致する唯一の接続と、アプリケーションによって設定された属性も再利用された接続。 これは既定値です。<br /><br /> SQL_CP_RELAXED_MATCH キーワードを使用できる接続文字列が一致する接続を = です。 キーワードが一致する必要がありますが、すべての接続属性に一致する必要があります。<br /><br /> ドライバー マネージャーが、プールされた接続を接続するときに、一致を実行する方法の詳細については、次を参照してください。 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)です。 接続プールの詳細については、次を参照してください。 [ODBC 接続プーリング](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)です。|  
|また (ODBC 3.0)|特定の機能の ODBC 2 欠落を表すかどうかを決定する 32 ビット整数*.x*動作または ODBC 3*.x*動作します。 次の値は、この属性の値の設定に使用されます。<br /><br /> SQL_OV_ODBC3_80 = ドライバー マネージャーは、次の ODBC 3.8 展示のドライバーの動作。<br /><br /> -ドライバーを返し、ODBC 3 が必要です。*x*日付、時刻、およびタイムスタンプのコード。<br />-ドライバーでは、ODBC 3 を返します。*x* SQLSTATE コードの場合に**SQLError**、 **SQLGetDiagField**、または**SQLGetDiagRec**と呼びます。<br />- *CatalogName*への呼び出しで引数**SQLTables**検索パターンを受け入れます。<br />-ドライバー マネージャーは、C データ型の拡張機能をサポートします。 データ型の C 拡張機能の詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)です。<br /><br /> 詳細については、次を参照してください。 [ODBC 3.8 新](../../../odbc/reference/what-s-new-in-odbc-3-8.md)です。<br /><br /> SQL_OV_ODBC3 = ドライバー マネージャーは、およびドライバー展示次の ODBC 3*.x*動作。<br /><br /> -ドライバー返し、ODBC 3 が必要ですが*.x*日付、時刻、およびタイムスタンプのコード。<br />-ドライバーには、ODBC 3 が返されます。*.x* SQLSTATE コードの場合に**SQLError**、 **SQLGetDiagField**、または**SQLGetDiagRec**と呼びます。<br />- *CatalogName*への呼び出しで引数**SQLTables**検索パターンを受け入れます。<br />ドライバー マネージャーは、C データ型の拡張機能をサポートしていません。<br /><br /> SQL_OV_ODBC2 = ドライバー マネージャーは、およびドライバー展示、次の ODBC 2*.x*動作します。 これは、ODBC 2 便利*.x* ODBC 3 作業アプリケーション*.x*ドライバー。<br /><br /> -ドライバー返し、ODBC 2 が必要ですが*.x*日付、時刻、およびタイムスタンプのコード。<br />-ドライバーは ODBC 2 を返します*.x* SQLSTATE コードの場合に**SQLError**、 **SQLGetDiagField**、または**SQLGetDiagRec**と呼びます。<br />- *CatalogName*への呼び出しで引数**SQLTables**検索パターンには受け入れません。<br />ドライバー マネージャーは、C データ型の拡張機能をサポートしていません。<br /><br /> SQLHENV 引数を持つ任意の関数を呼び出す前に、アプリケーションはこの環境属性を設定する必要がありますか、呼び出しが含む SQLSTATE HY010 を返す (関数のシーケンス エラーです)。 これは、その他の動作が、これらの環境フラグが存在するかどうかドライバー固有です。<br /><br /> 詳細については、次を参照してください。[アプリケーションの ODBC バージョンを宣言する](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)と[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)です。|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|ドライバーが文字列データを返す方法を決定する 32 ビット整数。 場合は SQL_TRUE、ドライバーは、null で終わる文字列データを返します。 場合は SQL_FALSE、ドライバーは、null で終わる文字列データを返しません。<br /><br /> この属性が SQL_TRUE に既定値です。 呼び出し**SQLSetEnvAttr** SQL_TRUE は設定に関係なく SQL_SUCCESS を返します。 呼び出し**SQLSetEnvAttr** SQL_ERROR と SQLSTATE HYC00 SQL_FALSE を返しますに設定する (省略可能な機能が実装されていません)。|  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|環境属性の設定値を返す|[SQLGetEnvAttr 関数](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
