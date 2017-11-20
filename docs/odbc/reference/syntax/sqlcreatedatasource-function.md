---
title: "SQLCreateDataSource 関数 |Microsoft ドキュメント"
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
- SQLCreateDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCreateDataSource
helpviewer_keywords:
- SQLCreateDataSource function [ODBC]
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c4c7b0b4ebecf75f1bcf31b0b1716a7076513488
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcreatedatasource-function"></a>SQLCreateDataSource 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **SQLCreateDataSource**をユーザーがデータ ソースの追加に使用できるダイアログ ボックスを表示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>引数  
 *hwnd*  
 [入力]親ウィンドウ ハンドル。  
  
 *lpszDS*  
 [入力]データ ソースの名前。 *lpszDS* null ポインターまたは空の文字列を指定できます。  
  
## <a name="returns"></a>返します。  
 **SQLCreateDataSource**データ ソースを作成する場合は TRUE を返します。 それ以外の場合、FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLCreateDataSource**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*Hwnd*引数が無効または NULL。|  
|ODBC_ERROR_INVALID_DSN|無効な DSN|*LpszDS*引数には、DSN に無効な文字列が含まれています。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|呼び出し**ConfigDSN** ODBC_ADD_DSN オプションを使用できませんでした。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバーまたはトランスレーター セットアップ ライブラリを読み込むことができませんでした。|ドライバーのセットアップ ライブラリを読み込むことができませんでした。|  
|ODBC_ERROR_USER_CANCELED|操作のユーザーにより取り消されました|ユーザーには、新しいデータ ソースの作成が取り消されました。|  
|ODBC_ERROR_CREATE_DSN_FAILED|要求された DSN を作成できませんでした。|データベースに接続できませんでした。呼び出し**SQLDriverConnect**の DSN 接続に成功が返されませんでした。<br /><br /> ファイルに書き込めませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 場合*hwnd*が null、 **SQLCreateDataSource** FALSE を返します。 それ以外の場合、表示、**データ ソースの新規作成**ダイアログ ボックスに次の図に示すように、設定、データ ソースの種類を選択するためのウィザード ページです。  
  
 ![新しいデータ ソース ダイアログ ボックスを作成します種類を選択](../../../odbc/reference/syntax/media/ch23a.gif "CH23A。")  
  
 既定のオプションは**ファイル データ ソース**です。 データ ソースが選択されていない場合と**次**クリックすると、インストールされているドライバーの一覧を含む次のウィザード ページが表示されます。  
  
 ![新しいデータ ソース ダイアログ ボックスを作成しますドライバーの選択](../../../odbc/reference/syntax/media/ch23b.gif "CH23B。")  
  
 場合**キャンセル**がクリックされると、ダイアログ ボックスが閉じられますと**SQLCreateDataSource** ODBC_ERROR_USER_CANCELED のエラー コードでは FALSE を返します。 いずれか、**ユーザー データ ソース**または**システム データ ソース**オプションが選択されている、**詳細**ボタンは使用できません。  
  
 ときに、**次**ボタンをクリックすると、次のいずれかが発生、ソースの選択によっては、データの種類。  
  
-   場合**ファイル データ ソース**がファイル名を入力するユーザーに選択すると、ウィザードのページを表示します。  
  
-   いずれか**ユーザー データ ソース**または**システム データ ソース**が選択すると、データ ソースとドライバーの型を表示するウィザード ページが表示されます、レビュー用とタイミング**完了**はクリックすると、データ ソースを設定します。  
  
 場合**詳細**がクリックされたドライバー固有の情報を入力するユーザーのデータ ソースの新規作成ウィザード ページで、ウィザードのページが表示されます。 このダイアログ ボックスのテキスト ボックスには、次の図に示すように、ドライバーと戻り値で区切られたキーワードを入力します。  
  
 ![ファイル DSN の作成の設定 ダイアログ ボックスの事前](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 追加のドライバー固有のキーワードの説明の下にあります**SQLDriverConnect**です。 除くすべて**DSN**は許可されています。  
  
 既定値を**この接続のことを確認**オプションが TRUE です。 この既定値は、このウィザード ページがアクティブになるかどうかを適用します。 場合**[ok]**がクリックされると、テキスト ボックスで指定した文字列と**この接続のことを確認**オプションの値がキャッシュされます。 (場合、**閉じる**ボタンまたは**キャンセル**がクリックすると、新たに入力した任意、テキスト ボックスに文字列が指定されているために、ドライバー固有の情報が失われた、 **の接続のことを確認**オプションの値はキャッシュされません)。  
  
 場合**ファイル データ ソース**ユーザーがファイル名を入力するように求め、ドライバーが選択されているし、キーワードの値は、詳細ウィザードのページに入力されている、し、ウィザードの最初のページで選択しました。 をクリックして**参照**で検索するファイル名では、その場合の既定のディレクトリ、**参照**ボックスは、hkey_local_machine \software\ で CommonFileDir によって指定されたパスの組み合わせで指定されました。Microsoft\Windows\CurrentVersion と"ODBC\DataSources"です。 (CommonFileDir が"C:\Program files \common files Files"の場合は、既定のディレクトリになります"C:\Program files \common files 場合 Sources"です。)  
  
 ファイル名が入力された場合と**[次へ]**がクリックされると、ファイル入力名に対して、オペレーティング システムの標準のファイルの名前付け規則の有効性がチェックされます。 ファイル名が有効でない場合、エラー メッセージ ボックスは、無効なファイル名が入力されたユーザーを通知します。 ユーザーが承認されると、メッセージ ボックス後は、ファイル名が入力されるウィザードのページにフォーカスが返されます。 ファイル名が有効な場合は、次の図に示すように、レビュー用を選択したキーワードと値のペアを示すウィザード ページが表示されます。  
  
 ![新しいデータ ソース ダイアログ ボックスを作成します確認](../../../odbc/reference/syntax/media/ch23d.gif "CH23D。")  
  
 場合**完了**がクリックされたと**ファイル データ ソース**データ ソースの種類として選択されている場合は、**この接続を確認して**オプションが TRUE、 **SQLDriverConnect**してを呼び出すと、 **SAVEFILE**と**ドライバー**キーワード。 *DriverCompletion*引数 SQL_DRIVER_COMPLETE に設定されています。 ファイル名、 **SAVEFILE**キーワードは、入力された名前を選択、やのドライバー名、**ドライバー**キーワードは、選択された名。 後にその文字列が追加されるドライバー固有の接続文字列は、詳細ウィザードのページで指定されている場合、**ドライバー**キーワード。  
  
 場合**SQLDriverConnect**返します SQL_SUCCESS、ドライバー マネージャーがファイル DSN を作成します。 **SQLCreateDataSource** TRUE を返します。 場合**SQLDriverConnect** SQL_SUCCESS、警告メッセージを返さないボックスは、接続がデータ ソースに加えられたされなかったことを示します。 最低限の接続情報を使用する DSN は作成できます。 このメッセージ ボックスをキャンセルするか、ファイル DSN の作成を続行できます。  
  
 かどうか、ユーザーは、DSN の作成を続行するが、このプロセスは継続として、**この接続を確認して**オプションが FALSE に設定されました。 FALSE が返されます場合は、ユーザーは、[キャンセル] を選択した、 **SQLCreateDataSource**と ODBC_ERROR_CREATE_DSN_FAILED のエラー コード。  
  
 場合**ファイル データ ソース**データ ソースの種類として選択されていると、**この接続を確認して**オプションは、FALSE、ファイル DSN がで作成された、**ドライバー**キーワードとユーザーが指定した文字列の詳細ウィザードのページから (存在する場合) に接続します。 ファイルの作成が成功した場合に TRUE が返されます。 **SQLCreateDataSource**です。 ファイルの作成が成功しなかった場合、エラー メッセージ ボックスは、オペレーティング システムからどのようなエラーが返されたを持つユーザーを通知します。 FALSE が返されます**SQLCreateDataSource**と ODBC_ERROR_CREATE_DSN_FAILED のエラー コード。 ファイルのデータ ソースの詳細については、次を参照してください。[を使用してファイル データ ソースの接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)、を参照してくださいまたは[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
 場合**ユーザー**または**システム データ ソース**データ ソースの種類として選択されている**ConfigDSN**ドライバーのセットアップでは、ライブラリが、ODBC_ADD_DSN で呼び出された*起こり*です。 詳細については、次を参照してください。 [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|データ ソースの管理|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|

