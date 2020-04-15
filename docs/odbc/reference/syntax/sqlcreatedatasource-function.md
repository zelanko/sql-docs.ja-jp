---
title: 関数を作成する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCreateDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCreateDataSource
helpviewer_keywords:
- SQLCreateDataSource function [ODBC]
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94dc0d6d6f3b5bc96ae41aecda5b46f119cff85c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301202"
---
# <a name="sqlcreatedatasource-function"></a>SQLCreateDataSource 関数
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 **ユーザー**がデータ ソースを追加できるダイアログ ボックスが表示されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>引数  
 *Hwnd*  
 [入力]親ウィンドウ ハンドル。  
  
 *lpszDS*  
 [入力]データ ソース名。 *lpszDS*は、null ポインターまたは空の文字列にすることができます。  
  
## <a name="returns"></a>戻り値  
 データ**ソースが**作成された場合は TRUE を返します。 それ以外の場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLCreateDataSource が**FALSE を返すと、SQL**インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwnd*が無効か NULL です。|  
|ODBC_ERROR_INVALID_DSN|無効な DSN|*引数 lpszDS*に DSN に対して無効な文字列が含まれています。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*に失敗しました|ODBC_ADD_DSN オプションを指定した**ConfigDSN**への呼び出しが失敗しました。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバまたはトランスレータセットアップライブラリを読み込めませんでした|ドライバ セットアップ ライブラリを読み込めませんでした。|  
|ODBC_ERROR_USER_CANCELED|ユーザーが操作をキャンセルしました|ユーザーは新しいデータ ソースの作成をキャンセルしました。|  
|ODBC_ERROR_CREATE_DSN_FAILED|要求された DSN を作成できませんでした|データベースに接続できませんでした。ファイル DSN**の SQLDriverConnect**への呼び出しは、正常な接続を返しませんでした。<br /><br /> ファイルに書き込みできませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 *hwnd が*null の場合 **、FALSE を**返します。 それ以外の場合は、次の図に示すように、設定するデータ ソースの種類を選択するためのウィザード ページを含む [**新しいデータ ソースの作成**] ダイアログ ボックスが表示されます。  
  
 ![[新しいデータ ソースの作成] ダイアログ ボックス: 種類の選択](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 既定のオプションは **[ファイル データ ソース] です**。 データ ソースを選択し、[**次へ**] をクリックすると、インストールされているドライバの一覧を含む次のウィザード ページが表示されます。  
  
 ![[新しいデータ ソースの作成] ダイアログ ボックス: ドライバーの選択](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 **[キャンセル]** をクリックすると、ダイアログ ボックスが表示されなくなり **、エラー**コードがODBC_ERROR_USER_CANCELEDのエラー コードを持つ FALSE が返されます。 **[ユーザー データ ソース**] または **[システム データ ソース**] オプションが選択されている場合、[**詳細設定**] ボタンは使用できません。  
  
 **[次へ**] ボタンをクリックすると、選択したデータ ソースの種類に応じて、次のいずれかが発生します。  
  
-   **[ファイル データ ソース]** を選択した場合は、ユーザーがファイル名を入力するためのウィザード ページが表示されます。  
  
-   **[ユーザー データ ソース**] または **[システム データ ソース**] を選択した場合は、データ ソースとドライバの種類を表示するウィザード ページが表示され、[**完了]** をクリックするとデータ ソースが設定されます。  
  
 [新しいデータ ソースの作成] ウィザード ページで **[詳細設定**] をクリックすると、ユーザーがドライバ固有の情報を入力するためのウィザード ページが表示されます。 このダイアログ ボックスのテキスト ボックスに、次の図に示すように、ドライバーとキーワードを入力します。  
  
 ![[詳細なファイル DSN の作成設定] ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 追加のドライバー固有のキーワードは、 **SQLDriverConnect**の説明の下にあります。 **DSN**以外はすべて許可されます。  
  
 **[この接続を確認**する] オプションの既定値は TRUE です。 この既定の設定は、このウィザード ページをアクティブにするかどうかに関係なく適用されます。 **[OK] を**クリックすると、テキスト ボックスに指定した文字列と [**この接続の確認**] オプションの値がキャッシュされます。 (**閉じる**ボタンまたは**キャンセル**をクリックすると、テキスト ボックスに指定された文字列と **[この接続を確認**する]オプションの値がキャッシュされないため、新たに入力されたドライバ固有の情報は失われます)。  
  
 最初のウィザード ページで **[ファイル データ ソース]** を選択した場合、ドライバを選択し、[高度な設定] ウィザード ページにキーワード値を入力すると、ユーザーはファイル名を入力するように求められます。 [**参照**] をクリックしてファイル名を検索し、[**参照**] ボックスの既定のディレクトリは、HKEY_LOCAL_MACHINE\SOFTWARE\Windows\現在のバージョンと "ODBC\データ ソース" で CommonFileDir で指定されたパスの組み合わせによって指定されます。 (CommonFileDir が "C:\プログラム ファイル\共通ファイル" の場合、既定のディレクトリは "C:\プログラム ファイル\共通ファイル\ODBC\データ ソース" になります。  
  
 ファイル名を入力し、[**次へ**] をクリックすると、入力したファイル名がオペレーティング システムの標準のファイル命名規則と照らして有効かどうかがチェックされます。 ファイル名が無効な場合は、無効なファイル名が入力されたことを示すエラー メッセージ ボックスが表示されます。 ユーザーがメッセージ ボックスに同意すると、フォーカスはファイル名が入力されたウィザード ページに戻ります。 ファイル名が有効な場合、次の図に示すように、選択したキーワードと値のペアを示すウィザード ページが表示されます。  
  
 ![[新しいデータ ソースの作成] ダイアログ ボックス: 確認](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 **[完了]** をクリックし、データ ソースの種類として **[ファイル データ ソース**] を選択した場合、[**この接続の確認**] オプションが TRUE の場合は **、SAVEFILE**キーワードと**DRIVER**キーワードを指定して**SQLDriverConnect**が呼び出されます。 引数*DriverCompletion*がSQL_DRIVER_COMPLETEに設定されています。 **SAVEFILE**キーワードのファイル名は、入力または選択された名前であり **、DRIVER**キーワードのドライバー名は選択された名前です。 ドライバー固有の接続文字列が [高度な設定] ウィザード ページで指定されている場合、その文字列は**DRIVER**キーワードの後に追加されます。  
  
 **SQLDriverConnect**がSQL_SUCCESSを返す場合、ドライバー マネージャーは、ファイル DSN を作成します。 **TRUE を**返します。 **SQLDriverConnect**がSQL_SUCCESSを返さない場合は、データ ソースへの接続が行われないことを示す警告メッセージ ボックスが表示されます。 最小限の接続情報を持つ DSN は引き続き作成できます。 このメッセージ ボックスを使用すると、ユーザーはファイル DSN の作成をキャンセルするか、続行できます。  
  
 ユーザーが DSN の作成を続行する場合、このプロセスは、**この接続の確認**オプションが FALSE に設定されているかのように続行されます。 ユーザーがキャンセルを選択した場合は、エラー コードがODBC_ERROR_CREATE_DSN_FAILEDの**SQLCreateDataSource**に対して FALSE が返されます。  
  
 データ ソースの種類として **[ファイル データ ソース]** が選択され、[**この接続を確認する**] オプションが FALSE の場合は、ファイル DSN が **、DRIVER**キーワードとユーザー指定の接続文字列 (存在する場合) を使用して作成されます。 ファイルの作成が成功した場合は **、SQLCreateDataSource**に対して TRUE が返されます。 ファイルの作成が成功しなかった場合は、オペレーティング システムから返されたエラーをユーザーに通知するエラー メッセージ ボックスが表示されます。 エラー コードがODBC_ERROR_CREATE_DSN_FAILEDの**場合は、FALSE**が返されます。 ファイル データ ソースの詳細については、「 ファイル データ ソース[を使用した接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」を参照するか、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)を参照してください。  
  
 **ユーザー**または**システム データ ソース**がデータ ソースの種類として選択されている場合は、ドライバー セットアップ ライブラリの**ConfigDSN**が*fRequest*ODBC_ADD_DSN呼び出されます。 詳細については、 [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの管理|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|
