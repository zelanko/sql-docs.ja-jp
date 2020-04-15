---
title: コンフィグDSN機能 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbae126c819088bd277621b207454503a86c8955
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306043"
---
# <a name="configdsn-function"></a>ConfigDSN 関数
**適合 性**  
 バージョン導入: ODBC 1.0  
  
 **まとめ**  
 **ConfigDSN は**、システム情報からデータ ソースを追加、変更、または削除します。 接続情報の入力を求めるメッセージが表示される場合があります。 これは、ドライバ DLL または別のセットアップ DLL に含めることができます。  
  
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
 [入力]親ウィンドウ ハンドル。 ハンドルが null の場合、この関数はダイアログ ボックスを表示しません。  
  
 *リクエスト*  
 [入力]要求の種類。 *fRequest*引数には、次のいずれかの値を指定する必要があります。  
  
 ODBC_ADD_DSN: 新しいデータ ソースを追加します。  
  
 ODBC_CONFIG_DSN: 既存のデータ ソースを構成 (変更) します。  
  
 ODBC_REMOVE_DSN: 既存のデータ ソースを削除します。  
  
 *ドライバー*  
 [入力]物理ドライバ名の代わりに、ドライバの説明 (通常は関連付けられた DBMS の名前) をユーザーに表示します。  
  
 *属性*  
 [入力]キーワードと値のペアの形式での属性の二重に終端された一覧。 詳細については、「コメント」を参照してください。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **ConfigDSN**が FALSE を返すと、関連付けられた*\*pfErrorCode*値が**SQLPostInstallerError エラー**の呼び出しによってインストーラー エラー バッファーにポストされ **、SQLInstallerError**を呼び出すことによって取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwndParent*が無効でした。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*引数 lpszAttributes*に構文エラーが含まれていました。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*fRequest*引数は、次の引数の 1 つではありません。<br /><br /> ODBC_CONFIG_DSNODBC_REMOVE_DSNODBC_ADD_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*要求*に失敗しました|*fRequest*引数によって要求された操作を実行できませんでした。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバまたはトランスレータ固有のエラー|定義された ODBC インストーラー エラーがないドライバー固有のエラー。 関数の呼び出しで*SzError*引数には、ドライバー固有のエラー メッセージが含まれている必要があります。 **SQLPostInstallerError**|  
  
## <a name="comments"></a>説明  
 **ConfigDSN は**、キーワードと値のペアの形式で属性のリストとして、インストーラー DLL から接続情報を受け取ります。 各ペアはヌルバイトで終了し、リスト全体がヌルバイトで終了します。 (つまり、2 つの null バイトがリストの末尾をマークします。キーワードと値のペアでは、等号の前後にスペースを入れることはできません。 **構成DSN**は **、SQL ブラウズ接続**および**SQL ドライバー接続**の有効なキーワードではないキーワードを受け入れることができます。 **構成DSN**は、必ずしも**SQL ブラウズ接続**および**SQL ドライバ接続**の有効なキーワードであるすべてのキーワードをサポートしているわけではありません。 (**構成 DSN**は**DRIVER**キーワードを受け入れません。**ConfigDSN**関数で使用されるキーワードは、インストーラの AUTO セットアップ機能を使用してデータ ソースを再作成するために必要なすべてのオプションをサポートしている必要があります。 **ConfigDSN**値と接続文字列の値の使用が同じ場合は、同じキーワードを使用する必要があります。  
  
 **SQLBrowseConnect**および**SQLDriverConnect**のように、キーワードとその値には **[] ()、;?{}\*=!@** 文字、**および DSN**キーワードの値はブランクのみで構成することはできません。 レジストリ文法のため、キーワードとデータ ソース名には円記号 (\\) 文字を含めることはできません。  
  
 データ ソース名の長さを確認し、無効な文字が名前に含まれていないことを確認するには **、ConfigDSN**が**SQLValidDSN**を呼び出す必要があります。 データ・ソース名がSQL_MAX_DSN_LENGTHより長い場合、または無効な文字が含まれている場合 **、SQLValidDSN**はエラーを戻し **、ConfigDSN**はエラーを戻します。 データ ソース名の長さは **、SQLWriteDSNToIni**によってもチェックされます。  
  
 たとえば、ユーザー ID、パスワード、およびデータベース名を必要とするデータ ソースを構成する場合、セットアップ アプリケーションは次のキーワードと値のペアを渡します。  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 これらのキーワードの詳細については[、SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)と各ドライバーのドキュメントを参照してください。  
  
 ダイアログ ボックスを表示するには *、hwndParent*を null にすることはできません。  
  
## <a name="adding-a-data-source"></a>データ ソースの追加  
 データ ソース名が*lpszAttributes*の**ConfigDSN**に渡された場合、その名前が有効かどうか**がチェック**されます。 データ ソース名が既存のデータ ソース名と一致し *、hwndParent*が null の場合 **、ConfigDSN**は既存の名前を上書きします。 既存の名前と一致し *、hwndParent*が null でない場合 **、ConfigDSN**は既存の名前を上書きするようにユーザーに求めます。  
  
 *lpszAttributes に*データ ソースに接続するための十分な情報が含まれている場合 **、ConfigDSN**はデータ ソースを追加するか、ユーザーが接続情報を変更できるダイアログ ボックスを表示できます。 *lpszAttributes に*データ ソースに接続するための十分な情報が含まれていない場合 **、ConfigDSN**は必要な情報を判断する必要があります。*hwndParent*が null でない場合は、ユーザーから情報を取得するためのダイアログ ボックスを表示します。  
  
 **ConfigDSN**がダイアログ ボックスを表示する場合は *、lpszAttributes*で渡された接続情報を表示する必要があります。 特に、データ ソース名が渡された場合 **、ConfigDSN**はその名前を表示しますが、ユーザーは変更できません。 **configDSN**は *、lpszAttributes*で渡されていない接続情報のデフォルト値を指定できます。  
  
 **ConfigDSN が**データ ソースの完全な接続情報を取得できない場合は、FALSE を返します。  
  
 **ConfigDSN**がデータ ソースの完全な接続情報を取得できる場合は、インストーラー DLL で**SQLWriteDSNToIni**を呼び出して、新しいデータ ソース仕様を Odbc.ini ファイル (またはレジストリ) に追加します。 **SQLWriteDSNToIni**は、データ ソース名を [ODBC データ ソース] セクションに追加し、データ ソース仕様セクションを作成し、ドライバーの説明を値として**DRIVER**キーワードを追加します。 **インストーラー** DLL で**SQLWritePrivateProfileString**を呼び出して、ドライバーが使用する追加のキーワードと値を追加します。  
  
## <a name="modifying-a-data-source"></a>データ ソースの変更  
 データ ソースを変更するには、データ ソース名を*lpszAttributes*の**ConfigDSN**に渡す必要があります。 **データ**ソース名が Odbc.ini ファイル (またはレジストリ) 内にあるかどうかをチェックします。  
  
 *hwndParent*が null の場合 **、ConfigDSN**は*lpszAttributes*内の情報を使用して Odbc.ini ファイル (またはレジストリ) 内の情報を変更します。 *hwndParent*が null でない場合は *、lpszAttributes*の情報を使用してダイアログ ボックスが表示されます。 **ConfigDSN***lpszAttributes*にはない情報については、システム情報からの情報を使用します。 ユーザーは **、ConfigDSN**がシステム情報に情報を保存する前に、情報を変更できます。  
  
 データ ソース名が変更された場合 **、ConfigDSN**はまずインストーラー DLL で**SQLRemoveDSNFromIni**を呼び出して、Odbc.ini ファイル (またはレジストリ) から既存のデータ ソース仕様を削除します。 次に、前のセクションの手順に従って、新しいデータ ソース仕様を追加します。 データ ソース名が変更されていない場合は、**インストーラー** DLL で**SQLWritePrivateProfileString**を呼び出して、他の変更を行います。 **ConfigDSN**は **、ドライバ**キーワードの値を削除または変更することはできません。  
  
## <a name="deleting-a-data-source"></a>データ ソースの削除  
 データ ソースを削除するには、データ ソース名を*lpszAttributes*の**ConfigDSN**に渡す必要があります。 **データ**ソース名が Odbc.ini ファイル (またはレジストリ) 内にあるかどうかをチェックします。 その後、インストーラー DLL で**SQLRemoveDSNFromIni**を呼び出して、データ ソースを削除します。  
  
## <a name="note"></a>Note
 このルーチンのユニコード・バージョンを作成する場合は、LPCSTR の代わりに LPCWSTR 引数を指定して**ConfigDSNW**と呼ばれる必要があります。
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの追加、変更、または削除|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Odbc.ini ファイルまたはレジストリから値を取得する|[文字列](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|既定のデータ ソースを削除する|[データ ソースを削除します。](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Odbc.ini (またはレジストリ) からデータ ソース名を削除する|[イニから削除します。](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Odbc.ini (またはレジストリ) にデータ ソース名を追加する|[を使用します。](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Odbc.ini ファイルまたはレジストリに値を書き込む|[文字列](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
