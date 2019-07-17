---
title: SQLSetEnvAttr 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 92d3689c91d301a95427862f464738090c430619
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039717"
---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLSetEnvAttr**環境の側面を制御する属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *EnvironmentHandle*  
 [入力]環境ハンドル。  
  
 *属性*  
 [入力]属性を設定すると、「コメントです」記載されています。  
  
 *ValuePtr*  
 [入力]関連付けられる値を指すポインター*属性*します。 値に応じて*属性*、 *ValuePtr*は 32 ビット整数の値を指定または null で終わる文字列をポイントします。  
  
 *StringLength*  
 [入力]場合*ValuePtr*文字の文字列またはバイナリのバッファーを指す、この引数の長さである必要があります **ValuePtr*します。 文字の文字列データでは、この引数は、文字列のバイト数を含める必要があります。  
  
 場合*ValuePtr*整数*StringLength*は無視されます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetEnvAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_ENV と*処理*の*EnvironmentHandle*します。 次の表に、によって返される通常の SQLSTATE 値**SQLSetEnvAttr** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。 ドライバーが環境属性をサポートしていない場合、エラーが接続時にのみ返されます。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーがで指定された値をサポートしていませんでした*ValuePtr*のような値を置き換えるとします。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|属性引数が文字列値を必要とする環境属性を識別し、 *ValuePtr*引数が null ポインター。|  
|HY010|関数のシーケンス エラー|(DM) では、接続ハンドルを割り当てた*EnvironmentHandle*します。<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION**に設定されていない**SQLSetEnvAttr**と*属性*が等しくない**SQL_ATTR_ODBC_VERSION**します。 設定する必要はありません**SQL_ATTR_ODBC_VERSION**を使用する場合は明示的に**SQLAllocHandleStd**します。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY024|無効な属性値|指定した*属性*値、無効な値に指定されました*ValuePtr*します。|  
|HY090|文字列またはバッファーの長さが無効です。|*StringLength*引数は SQL_NTS が 0 未満でした。|  
|HY092|無効な属性またはオプション識別子|引数に指定された値 (DM)*属性*ODBC ドライバーでサポートされているのバージョンには無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*有効な ODBC 環境属性が ODBC のバージョンのドライバーでサポートされていますが、ドライバーによってサポートされていませんでした。<br /><br /> (DM)、*属性*引数が SQL_ATTR_OUTPUT_NTS、および*ValuePtr*が sql_false になります。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLSetEnvAttr**環境に接続ハンドルが割り当てられていない場合にのみです。 正常に環境のアプリケーションによって設定されたすべての環境属性がされるまで保持**SQLFreeHandle**が環境内で呼び出されます。 ODBC では、複数の環境ハンドルを同時に割り当てることが*3.x*します。  
  
 情報の形式設定*ValuePtr*に指定した依存*属性*します。 **SQLSetEnvAttr**は 2 つの異なる形式のいずれかの属性情報を受け入れます。 null で終わる文字列または 32 ビット整数値。 それぞれの形式は、属性の説明に記録されます。  
  
 ドライバー固有の環境属性はありません。  
  
 呼び出して接続属性を設定することはできません**SQLSetEnvAttr**します。 これを実行しようとすると、SQLSTATE HY092 が返されます (無効な属性またはオプション識別子)。  
  
|*属性*|*ValuePtr*内容|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|または、環境レベルの接続プールを無効にする 32 ビット SQLUINTEGER 値。 次の値が使用されます。<br /><br /> SQL_CP_OFF = 接続プールは無効になります。 既定値です。<br /><br /> SQL_CP_ONE_PER_DRIVER = 1 つの接続プールが各ドライバーのサポートされています。 プール内のすべての接続は、1 つのドライバーに関連付けられます。<br /><br /> SQL_CP_ONE_PER_HENV = 1 つの接続プールが環境ごとにサポートされています。 プール内のすべての接続は、1 つの環境に関連付けられます。<br /><br /> SQL_CP_DRIVER_AWARE = 入手可能になった場合は、ドライバーの接続プールの認識機能を使用します。 ドライバー対応接続プールをサポートしていない場合は、SQL_CP_DRIVER_AWARE は無視され、SQL_CP_ONE_PER_HENV を使用します。 詳細については、次を参照してください。[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)します。 環境では、一部のドライバー サポートし、一部のドライバーは対応接続プールをサポートしていない、SQL_CP_DRIVER_AWARE には、サポート ドライバー、これらの接続プールの認識機能を有効が SQL_CP_ONE_PER_HENV にする設定に相当接続プールの認識機能をサポートしているドライバーです。<br /><br /> 呼び出すことによって接続プールが有効になっている**SQLSetEnvAttr** SQL_CP_ONE_PER_DRIVER または SQL_CP_ONE_PER_HENV に SQL_ATTR_CONNECTION_POOLING 属性を設定します。 アプリケーションを有効にする接続プールは共有環境を割り当てる前に、この呼び出しを実行する必要があります。 呼び出しで環境ハンドル**SQLSetEnvAttr** SQL_ATTR_CONNECTION_POOLING プロセス レベルの属性は、null に設定されます。 その後、アプリケーションが呼び出すことによって暗黙の共有環境を割り当てる接続プールを有効にすると後、 **SQLAllocHandle**で、 *InputHandle*を SQL_HANDLE_ENV 引数を設定します。<br /><br /> ために、SQL_ATTR_CONNECTION_POOLING をその環境をリセットできません接続プールを有効になっているし、アプリケーションの共有環境が選択されて、 **SQLSetEnvAttr**が null の環境で呼び出されるこの属性を設定するときに処理します。 この属性は、接続プールが、共有環境で既に有効なときに設定されている場合、属性は、その後に割り当てられている共有環境のみに影響します。<br /><br /> 環境での接続プールを有効にすることもできます。 環境の接続プールについては、次に注意してください。<br /><br /> -接続プールの NULL ハンドルの有効化は、プロセス レベルの属性です。 その後に割り当てられている環境を使用して、共有環境では、なります、プロセス レベルの接続プール設定が継承されます。<br />の後環境が割り当てられているアプリケーションは、接続プールの設定を変更できます。<br />-環境の接続プールが有効になっているし、接続のドライバーがドライバー プールを使用して場合に、基本設定を実行環境がプールされます。<br /><br /> SQL_ATTR_CONNECTION_POOLING は、ドライバー マネージャーの内部に実装されます。 ドライバーは、SQL_ATTR_CONNECTION_POOLING を実装する必要はありません。 ODBC 2.0 および 3.0 のアプリケーションには、この環境属性を設定できます。<br /><br /> 詳細については、「 [ODBC Connection Pooling (ODBC 接続プール)](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)」を参照してください。|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|接続プールからの接続を選択する方法を決定する 32 ビット SQLUINTEGER 値。 ときに**SQLConnect**または**SQLDriverConnect**が呼び出されると、ドライバー マネージャーを決定する接続がプールから再利用されます。 ドライバー マネージャーは、呼び出しと、プール内のキーワードと、接続の接続属性にアプリケーションによって設定された接続属性の接続オプションの一致を試みます。 この属性の値は、一致条件の有効桁数のレベルを決定します。<br /><br /> 次の値は、この属性の値の設定に使用されます。<br /><br /> SQL_CP_STRICT_MATCH = の呼び出しで、接続オプションと完全に一致するのみの接続と、アプリケーションによって設定された属性が再利用、接続します。 既定値です。<br /><br /> SQL_CP_RELAXED_MATCH キーワードを使用する接続文字列が一致する接続を = です。 キーワードが一致する必要がありますが、接続のすべての属性に一致する必要があります。<br /><br /> ドライバー マネージャーが、プールされた接続への接続で、一致を実行する方法の詳細については、次を参照してください。 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)します。 接続プールの詳細については、次を参照してください。 [ODBC 接続プーリング](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)します。|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|特定の機能の ODBC 欠落を表すかどうかを決定する 32 ビット整数*2.x*動作または ODBC *3.x*動作します。 次の値は、この属性の値の設定に使用されます。<br /><br /> SQL_OV_ODBC3_80 =、ドライバー マネージャーとドライバーの次の ODBC 3.8 展示場の動作。<br /><br /> -ドライバー返し、ODBC *3.x*日付、時刻、およびタイムスタンプのコード。<br />-ドライバーは ODBC を返します*3.x* SQLSTATE コードの場合に**SQLError**、 **SQLGetDiagField**、または**SQLGetDiagRec**が呼び出されます。<br />- *CatalogName*への呼び出しで引数**SQLTables**検索パターンします。<br />ドライバー マネージャーは、C データ型の拡張機能をサポートします。 C データ型の機能拡張の詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)します。<br /><br /> 詳細については、次を参照してください。[で ODBC 3.8 新](../../../odbc/reference/what-s-new-in-odbc-3-8.md)します。<br /><br /> SQL_OV_ODBC3 =、ドライバー マネージャーと、次の ODBC ドライバーの展示場*3.x*動作。<br /><br /> -ドライバー返し、ODBC *3.x*日付、時刻、およびタイムスタンプのコード。<br />-ドライバーは ODBC を返します*3.x* SQLSTATE コードの場合に**SQLError**、 **SQLGetDiagField**、または**SQLGetDiagRec**が呼び出されます。<br />- *CatalogName*への呼び出しで引数**SQLTables**検索パターンします。<br />ドライバー マネージャーは、C データ型の拡張機能をサポートしていません。<br /><br /> SQL_OV_ODBC2 =、ドライバー マネージャーと、次の ODBC ドライバーの展示場*2.x*動作します。 これは、ODBC の場合に特に役立ちます*2.x* odbc 作業アプリケーション*3.x*ドライバー。<br /><br /> -ドライバー返し、ODBC *2.x*日付、時刻、およびタイムスタンプのコード。<br />-ドライバーは ODBC を返します*2.x* SQLSTATE コードの場合に**SQLError**、 **SQLGetDiagField**、または**SQLGetDiagRec**が呼び出されます。<br />- *CatalogName*への呼び出しで引数**SQLTables**検索パターンを受け入れません。<br />ドライバー マネージャーは、C データ型の拡張機能をサポートしていません。<br /><br /> SQLHENV 引数を持つ任意の関数を呼び出す前に、アプリケーションはこの環境属性を設定する必要がありますまたは呼び出しが SQLSTATE HY010 を返す (関数のシーケンス エラーです)。 これは、これらの環境のフラグの他の動作が存在かどうかドライバー固有です。<br /><br /> 詳細については、次を参照してください。[アプリケーションの ODBC バージョンを宣言する](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)と[動作が変更される](../../../odbc/reference/develop-app/behavioral-changes.md)します。|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|32 ビットの整数で、ドライバーが文字列データを返す方法を決定します。 場合は SQL_TRUE、ドライバーは、null で終わる文字列データを返します。 場合は sql_false になります、ドライバーでは、null で終わる文字列データは返されません。<br /><br /> この属性の既定値は SQL_TRUE です。 呼び出し**SQLSetEnvAttr** SQL_TRUE に設定する SQL_SUCCESS が返されます。 呼び出し**SQLSetEnvAttr** SQL_FALSE を返します。 SQL_ERROR と SQLSTATE HYC00 に設定する (省略可能な機能が実装されていません)。|  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|環境属性の設定を返す|[SQLGetEnvAttr 関数](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
