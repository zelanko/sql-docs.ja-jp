---
title: ConfigDSN 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9387ffefe2fdcc9b30824018a763b87b81b831dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538093"
---
# <a name="configdsn-function"></a>ConfigDSN 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0  
  
 **まとめ**  
 **ConfigDSN**追加、変更、またはシステム情報のデータ ソースを削除します。 接続情報をユーザーに求めることができます。 これは、ドライバ DLL または別のセットアップ DLL に存在できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL ConfigDSN(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 関数では、ハンドルが null の場合、ダイアログ ボックスは表示されません。  
  
 *fRequest*  
 [入力]要求の種類。 *起こり*引数は、次の値のいずれかを含める必要があります。  
  
 ODBC_ADD_DSN:新しいデータ ソースを追加します。  
  
 ODBC_CONFIG_DSN:構成 (変更) 既存のデータ ソース。  
  
 ODBC_REMOVE_DSN:既存のデータ ソースを削除します。  
  
 *lpszDriver*  
 [入力]ドライバーの名前 (通常は、関連付けられている DBMS の名前)、物理ドライバー名ではなくユーザーに表示されます。  
  
 *lpszAttributes*  
 [入力]二重の null で終わるキーワードと値のペアの形式で属性の一覧。 詳細については、「コメントです。」を参照してください。  
  
## <a name="returns"></a>戻り値  
 関数は、成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**ConfigDSN** 、関連付けられている FALSE が返されます *\*pfErrorCode*インストーラー エラー バッファーへの呼び出しで値が投稿された**SQLPostInstallerError**と呼び出すことによって取得できる**SQLInstallerError**します。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とこの関数のコンテキストでそれぞれについて説明します。  
  
|*\*pfErrorCode*|[エラー]|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効です。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*LpszAttributes*引数には、構文エラーが含まれています。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは翻訳者名|*LpszDriver*引数が無効です。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|要求の型が無効です。|*起こり*引数が、次のいずれか。<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|によって要求された操作を実行できませんでした、*起こり*引数。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバーに translator 固有のエラー|定義された ODBC インストーラーのエラーがないドライバー固有のエラーです。 *SzError*への呼び出しの引数、 **SQLPostInstallerError**関数は、ドライバー固有のエラー メッセージを含める必要があります。|  
  
## <a name="comments"></a>コメント  
 **ConfigDSN**キーワードと値のペアの形式で属性の一覧としてインストーラー DLL からの接続情報を受信します。 各ペアは、null バイトで終了し、全体の一覧は null バイトで終了します。 (つまり、2 つの null バイトの末尾を示す一覧。)スペースは、キーワードと値のペアで、等号は使用できません。 **ConfigDSN**のキーワードが指定されていないキーワードを受け入れることができる**SQLBrowseConnect**と**SQLDriverConnect**します。 **ConfigDSN**が必ずしもサポートのキーワードが指定されているすべてのキーワード**SQLBrowseConnect**と**SQLDriverConnect**します。 (**ConfigDSN**受け入れません、**ドライバー**キーワードです)。使用されるキーワード、 **ConfigDSN**関数は、インストーラーの自動セットアップ機能を使用してデータ ソースを再作成に必要なすべてのオプションをサポートする必要があります。 ときに、使用、 **ConfigDSN**値と、接続文字列の値が同じで、同じキーワードを使用する必要があります。  
  
 うに**SQLBrowseConnect**と**SQLDriverConnect**、キーワードとその値を含めないで、 **{}()、;?\*=! @** 文字、およびの値、 **DSN**空白のみのキーワードは受け付けられません。 レジストリの文法のためのキーワードおよびデータ ソース名が円記号を含めることはできません (\\) 文字。  
  
 **ConfigDSN**呼び出す必要があります**SQLValidDSN**データ ソース名の長さを確認し、名前に無効な文字が含まれていないことを確認します。 データ ソース名が SQL_MAX_DSN_LENGTH よりも長いまたは無効な文字が含まれています**SQLValidDSN**はエラーを返しますと**ConfigDSN**はエラーを返します。 データ ソース名の長さがによってチェックも**SQLWriteDSNToIni**します。  
  
 たとえば、ユーザー ID、パスワード、およびデータベース名を必要とするデータ ソースを構成するには、セットアップ アプリケーションは、次のキーワードと値のペアを渡す可能性があります。  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 これらのキーワードの詳細については、次を参照してください。 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)と各ドライバーのドキュメント。  
  
 ダイアログ ボックスを表示する*hwndParent*は null にできません。  
  
## <a name="adding-a-data-source"></a>データ ソースの追加  
 データ ソース名が渡された場合**ConfigDSN**で*lpszAttributes*、 **ConfigDSN**名が有効なことを確認します。 データ ソース名が既存のデータ ソース名と一致する場合と*hwndParent*が null、 **ConfigDSN**既存の名前が上書きされます。 既存の名前と一致する場合と*hwndParent*が null でない**ConfigDSN**既存の名前を上書きするように求めます。  
  
 場合*lpszAttributes* 、データ ソースに接続するための十分な情報が含まれます**ConfigDSN**データ ソースまたはユーザーが接続情報を変更できるダイアログ ボックスの表示を追加できます。 場合*lpszAttributes* 、データ ソースに接続するための十分な情報は含まれません**ConfigDSN**場合; に必要な情報を確認する必要があります*hwndParent*が null でないです。ユーザーから情報を取得する ダイアログ ボックスが表示されます。  
  
 場合**ConfigDSN**  ダイアログ ボックスを表示でに渡される任意の接続情報を表示する必要があります*lpszAttributes*します。 データ ソース名が、渡された場合、特に**ConfigDSN**その名が表示されますが、ユーザーを変更することはできません。 **ConfigDSN**接続情報が渡されない内での既定値を指定できます*lpszAttributes*します。  
  
 場合**ConfigDSN**完全な接続情報を取得できないデータ ソースの場合は FALSE を返します。  
  
 場合**ConfigDSN**データ ソースの完全な接続情報を取得できます、呼び出す**SQLWriteDSNToIni**インストーラー DLL Odbc.ini ファイル (またはレジストリ) に新しいデータ ソースの指定を追加します。 **SQLWriteDSNToIni** [ODBC データ ソース] セクションに、データ ソース名を追加、データ ソースの仕様」セクションを作成し、追加、**ドライバー**キーワードの値としてドライバーの説明をします。 **ConfigDSN**呼び出し**SQLWritePrivateProfileString**インストーラー DLL をその他のキーワードと、ドライバーによって使用される値を追加します。  
  
## <a name="modifying-a-data-source"></a>データ ソースの変更  
 データ ソースを変更するにはデータ ソース名を渡す必要が**ConfigDSN**で*lpszAttributes*します。 **ConfigDSN** Odbc.ini ファイル (またはレジストリ) のデータ ソース名は、ことを確認します。  
  
 場合*hwndParent*が null、 **ConfigDSN** 、情報を使用して*lpszAttributes* Odbc.ini ファイル (またはレジストリ) で情報を変更します。 場合*hwndParent*が null でない**ConfigDSN**で情報を使用してダイアログ ボックスを表示します*lpszAttributes*についてにない*lpszAttributes*、情報システム情報を使用します。 ユーザーが前に、情報を変更できる**ConfigDSN**システム情報に格納されます。  
  
 データ ソース名が変更された場合**ConfigDSN**まず呼び出し**SQLRemoveDSNFromIni**既存のデータを削除する DLL をインストーラーには、ソースの Odbc.ini ファイル (またはレジストリ) から指定します。 新しいデータ ソースの指定を追加する前のセクションの手順に従います。 データ ソース名が変更されていない場合**ConfigDSN**呼び出し**SQLWritePrivateProfileString**インストーラー DLL を使用してその他の変更。 **ConfigDSN**を削除またはの値を変更することがあります、**ドライバー**キーワード。  
  
## <a name="deleting-a-data-source"></a>データ ソースを削除します。  
 データ ソースを削除するにはデータ ソース名を渡す必要が**ConfigDSN**で*lpszAttributes*します。 **ConfigDSN** Odbc.ini ファイル (またはレジストリ) のデータ ソース名は、ことを確認します。 呼び出して**SQLRemoveDSNFromIni**インストーラー DLL をデータ ソースを削除します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはデータ ソースを削除します。|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Odbc.ini ファイルまたはレジストリから値を取得します。|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|既定のデータ ソースを削除します。|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Odbc.ini (またはレジストリ) からのデータ ソース名の削除|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Odbc.ini (またはレジストリ) へのデータ ソース名の追加|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Odbc.ini ファイルまたはレジストリ値の書き込み|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
