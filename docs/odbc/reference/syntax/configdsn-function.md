---
title: "ConfigDSN 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ConfigDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDSN
helpviewer_keywords:
- ConfigDSN [ODBC]
ms.assetid: 01ced74e-c575-4a25-83f5-bd7d918123f8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 491396da26d75d6710e708b840c9407b4a976bb9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="configdsn-function"></a>ConfigDSN 関数
**準拠**  
 1.0 ODBC のバージョンで導入されました。  
  
 **概要**  
 **ConfigDSN**を追加、変更、またはシステム情報のデータ ソースを削除します。 接続情報をユーザーに要求があります。 ドライバー DLL または別のセットアップ DLL があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL ConfigDSN(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 関数では、ハンドルが null の場合、ダイアログ ボックスは表示されません。  
  
 *起こり*  
 [入力]要求の種類。 *起こり*引数は、次の値のいずれかを含める必要があります。  
  
 ODBC_ADD_DSN: は、新しいデータ ソースを追加します。  
  
 ODBC_CONFIG_DSN: 構成 (変更) 既存のデータ ソース。  
  
 ODBC_REMOVE_DSN: は、既存のデータ ソースを削除します。  
  
 *lpszDriver*  
 [入力]ドライバーの名前 (通常は、関連付けられた DBMS の名前)、物理ドライバー名の代わりにユーザーに表示されます。  
  
 *lpszAttributes*  
 [入力]二重の null で終わる、キーワードと値のペアの形式での属性の一覧。 詳細については、「コメント」を参照してください。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**ConfigDSN**は FALSE を返します、関連付けられている *\*pfErrorCode*への呼び出しで値がインストーラー エラー バッファーにポストされた**SQLPostInstallerError**と呼び出すことによって取得できます**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効です。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*LpszAttributes*引数に構文エラーが含まれています。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszDriver*引数が無効です。 これをレジストリで見つかりませんでした。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*起こり*引数が、次のいずれか。<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|要求した操作を実行できませんでした、*起こり*引数。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバー固有またはトランスレーター エラー|定義された ODBC インストーラーのエラーがないドライバー固有のエラーです。 *SzError*への呼び出しで引数、 **SQLPostInstallerError**関数は、ドライバー固有のエラー メッセージを含める必要があります。|  
  
## <a name="comments"></a>コメント  
 **ConfigDSN**キーワードと値のペアの形式で属性の一覧としてインストーラー DLL からの接続情報を受信します。 各ペアは、null バイトで終了し、null バイトのリスト全体が終了します。 (つまり、2 つの null バイトの末尾を示す一覧です。)スペースはキーワード/値ペア内の等号 (=) を使用できません。 **ConfigDSN**のキーワードが指定されていないキーワードを受け入れることができる**SQLBrowseConnect**と**SQLDriverConnect**です。 **ConfigDSN**が必ずしもサポートのキーワードが指定されているすべてのキーワード**SQLBrowseConnect**と**SQLDriverConnect**です。 (**ConfigDSN**受け付けない、**ドライバー**キーワードです)。使用されるキーワード、 **ConfigDSN**関数は、インストーラーの自動設定機能を使用してデータ ソースを再作成に必要なすべてのオプションをサポートする必要があります。 場合の使用、 **ConfigDSN**値と接続文字列の値が同じで、同じキーワードを使用する必要があります。  
  
 として**SQLBrowseConnect**と**SQLDriverConnect**、キーワードとその値を含めないで、 **{} ()、;?\*=! @**文字、およびの値、 **DSN**空白のみのキーワードは受け付けられません。 レジストリの文法のためのキーワードおよびデータ ソース名が円記号を含めることはできません (\\) 文字です。  
  
 **ConfigDSN**呼び出す必要があります**SQLValidDSN**をデータ ソース名の長さを確認し、名前に無効な文字が含まれていないことを確認してください。 場合は、データ ソース名 SQL_MAX_DSN_LENGTH より長いか、無効な文字が含まれています**SQLValidDSN**はエラーを返しますと**ConfigDSN**はエラーを返します。 データ ソース名の長さがによってチェックも**SQLWriteDSNToIni**です。  
  
 たとえば、ユーザー ID、パスワード、およびデータベース名を必要とするデータ ソースを構成するのにセットアップ アプリケーションは、次のキーワードと値のペアを渡す可能性があります。  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 これらのキーワードの詳細については、次を参照してください。 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)と各ドライバーのドキュメントです。  
  
 ダイアログ ボックスを表示する*hwndParent*は null にできません。  
  
## <a name="adding-a-data-source"></a>データ ソースの追加  
 データ ソース名が渡された場合**ConfigDSN**で*lpszAttributes*、 **ConfigDSN**名前が有効なことを確認します。 データ ソース名には、既存のデータ ソース名が一致する場合と*hwndParent*が null、 **ConfigDSN**既存の名前が上書きされます。 既存の名前と一致する場合と*hwndParent*が null でない**ConfigDSN**既存の名前を上書きするように求めます。  
  
 場合*lpszAttributes* 、データ ソースに接続するための十分な情報が含まれます**ConfigDSN**をユーザーが接続情報を変更できるダイアログ ボックスを表示またはデータがソースに追加できます。 場合*lpszAttributes* 、データ ソースに接続するための十分な情報を含まない**ConfigDSN**場合、必要な情報を確認する必要があります*hwndParent*が null でないです。ユーザーから情報を取得するダイアログ ボックスが表示されます。  
  
 場合**ConfigDSN**  ダイアログ ボックスを表示内で渡されるすべての接続情報を表示する必要があります*lpszAttributes*です。 特に、データ ソース名が、渡された場合**ConfigDSN**その名前が表示されますが、ユーザーを変更することはできません。 **ConfigDSN**でに渡されなかった接続情報の既定値を指定できます*lpszAttributes*です。  
  
 場合**ConfigDSN**完全な接続情報を取得できないデータ ソースの場合は FALSE を返します。  
  
 場合**ConfigDSN**データ ソースの完全な接続情報を取得できます、呼び出す**SQLWriteDSNToIni**の Odbc.ini ファイル (またはレジストリ) に新しいデータ ソースの指定を追加する DLL のインストーラーにします。 **SQLWriteDSNToIni** [ODBC データ ソース] セクションに、データ ソース名を追加し、データ ソースの仕様」セクションを作成し、追加、**ドライバー**キーワードの値としてドライバー説明を入力します。 **ConfigDSN**呼び出し**SQLWritePrivateProfileString**の任意の他のキーワードと、ドライバーによって使用される値を追加する DLL のインストーラーにします。  
  
## <a name="modifying-a-data-source"></a>データ ソースの変更  
 データ ソースを変更するには、データ ソース名に渡すことが**ConfigDSN**で*lpszAttributes*です。 **ConfigDSN** Odbc.ini ファイル (レジストリ) でデータ ソース名は、ことを確認します。  
  
 場合*hwndParent*が null、 **ConfigDSN**で情報を使用して*lpszAttributes* Odbc.ini ファイル (レジストリ) の情報を変更します。 場合*hwndParent*が null でない**ConfigDSN**で情報を使用してダイアログ ボックスを表示*lpszAttributes*についてではなく*lpszAttributes。*、システムについての情報を使用します。 ユーザーが前に、情報を変更できる**ConfigDSN**システム情報に格納します。  
  
 データ ソース名が変更された場合**ConfigDSN** 、まず呼び出し**SQLRemoveDSNFromIni**を既存のデータを削除する DLL をインストーラーには、ソースの Odbc.ini ファイル (レジストリ) から指定します。 次に、新しいデータ ソースの指定を追加する前のセクションで手順を実行します。 データ ソースの名前を変更していない場合**ConfigDSN**呼び出し**SQLWritePrivateProfileString**の他の変更を加える DLL のインストーラーにします。 **ConfigDSN**を削除またはの値を変更することがあります、**ドライバー**キーワード。  
  
## <a name="deleting-a-data-source"></a>データ ソースを削除します。  
 データ ソースを削除するにはデータ ソース名を渡すことが**ConfigDSN**で*lpszAttributes*です。 **ConfigDSN** Odbc.ini ファイル (レジストリ) でデータ ソース名は、ことを確認します。 呼び出して**SQLRemoveDSNFromIni**のデータ ソースを削除するための DLL のインストーラーにします。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはデータ ソースを削除します。|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Odbc.ini ファイルまたはレジストリから値を取得します。|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|既定のデータ ソースを削除します。|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Odbc.ini (レジストリ) からデータ ソース名を削除します。|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Odbc.ini (レジストリ) へのデータ ソース名の追加|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Odbc.ini ファイルまたはレジストリ値の書き込み|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|

