---
title: データ ソースの管理 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLManageDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLManageDataSources
helpviewer_keywords:
- SQLManageDataSources [ODBC]
ms.assetid: ac6d186f-b394-406c-94c4-c6331d1ca468
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b572a861af3479e1543be9fda9598cc7e25d36c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290220"
---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 **SQLManageDataSources は**、システム情報のデータ ソースを設定、追加、および削除できるダイアログ ボックスを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>引数  
 *Hwnd*  
 [入力]親ウィンドウ ハンドル。  
  
## <a name="returns"></a>戻り値  
 *hwnd*が有効なウィンドウ ハンドルでない場合は、FALSE**を返します**。 それ以外の場合には、TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQL 管理データソースが**FALSE を返すと、SQLInstallerError を呼び出すことによって関連付けられた*\*pfErrorCode*値**を**取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*に失敗しました|**ConfigDSN**への呼び出しに失敗しました。|  
|ODBC_ERROR_INVALID__HWND|無効なウィンドウ ハンドル|*引数 hwnd*が無効か NULL です。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="managing-data-sources"></a>データ ソースの管理  
 **次の**図に示すように、**最初に [ODBC データ ソース アドミニストレータ**] ダイアログ ボックスが表示されます。  
  
 ![[ODBC データ ソース管理者] ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 ダイアログ ボックスには、システム情報に表示されるデータ ソースが **、ユーザー DSN**、**システム DSN**、**およびファイル DSN**の 3 つのタブに表示されます。 ユーザーがデータ ソースをダブルクリックするか、データ ソースを選択して **[構成**] をクリックすると **、SQLManageDataSources は**セットアップ DLL の**ConfigDSN**をODBC_CONFIG_DSN オプションで呼び出します。  
  
 ユーザーが **[追加**] をクリックすると **、次**の図に示すように[**新しいデータ ソースの作成**] ダイアログ ボックスが表示されます。  
  
 ![[新しいデータ ソースの作成] ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 ダイアログ ボックスには、インストールされているドライバの一覧が表示されます。 ユーザーがドライバーをダブルクリックするか、ドライバーを選択して **[OK]** をクリックすると **、SQLManageDataSources**はセットアップ DLL で**ConfigDSN**を呼び出し、ODBC_ADD_DSN オプションを渡します。  
  
 ユーザーがデータ ソースを選択して [**削除**] をクリックすると、ユーザーがデータ**ソース**を削除するかどうかを確認するメッセージが表示されます。 ユーザーが **[はい**] をクリックすると **、セットアップ**DLL の**ConfigDSN**がODBC_REMOVE_DSN オプションで呼び出されます。  
  
 [**新しいデータ ソースの作成**] ダイアログ ボックスは、ユーザー データ ソース、システム データ ソース、またはファイル データ ソースを追加または削除するために使用します。  
  
## <a name="user-dsns"></a>ユーザー DSN  
 個々のユーザー用に作成された DSN は、システム DSN と区別するためにユーザー DSN と呼ばれます。 ユーザー DSN は、システム情報に次のように登録されます。  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>システム DSN  
 [**新しいデータ ソースの作成**] ダイアログ ボックスでは、システム データ ソースをローカル コンピュータに追加したり、削除したり、システム データ ソースの構成を設定したりできます。  
  
 システム データ ソース名 (DSN) を使用して設定されたデータ ソースは、同じコンピュータ上の複数のユーザーが使用できます。 また、システム全体のサービスで使用でき、ユーザーがマシンにログオンしていなくてもデータ ソースにアクセスできます。  
  
 システム DSN は、HKEY_CURRENT_USERエントリではなく、システム情報のHKEY_LOCAL_MACHINEエントリに登録されます。 特定のユーザー名とパスワードでログオンするユーザーには関連付けられませんが、そのマシンの任意のユーザーまたはシステム全体の自動サービスで使用できます。 ただし、システム DSN は 1 台のマシンに関連付けられています。 マシン間でリモート DSN を使用する機能はサポートされていません。 システム DSN は、システム情報に次のように登録されます。  
  
 HKEY_LOCAL_MACHINE ソフトウェア ODBC ODBC.ini  
  
## <a name="file-dsns"></a>ファイル DSN  
 ファイル データ ソースには、コンピューターのデータ ソースと同様に、データ ソース名が含まれていないため、1 人のユーザーまたはコンピューターに登録されません。 そのデータ ソースの接続情報は、任意のコンピューターにコピーできる .dsn ファイルに含まれています。 ファイル データ ソースは共有可能であり、その場合は .dsn ファイルがネットワーク上に存在し、ユーザーが適切なドライバをインストールしている限り、ネットワーク上の複数のユーザーが同時に使用できます。 ファイル データ ソースは共有不可にすることもできます。  
  
 ファイル データ ソースの詳細については、「[ファイル データ ソースを使用した接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)」を参照するか、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)を参照してください。  
  
## <a name="managing-drivers"></a>ドライバの管理  
 ユーザーが **[ODBC データ ソース アドミニストレータ**] ダイアログ ボックスの [**ドライバ**] タブをクリックすると、**システム**にインストールされている ODBC ドライバの一覧と、ドライバに関する情報が表示されます。 表示される日付は、次の図に示すように、ドライバーの作成日です。  
  
 ![[ODBC データ ソース管理者のドライバー] タブ](../../../odbc/reference/syntax/media/ch23g.gif "ch23g")  
  
## <a name="tracing-options"></a>[トレース オプション]  
 ユーザーが **[ODBC データ ソース アドミニストレータ**] ダイアログ ボックスの [**トレース**] タブをクリック**すると、次**の図に示すように、トレース オプションが表示されます。  
  
 ![[ODBC データ ソース管理者のトレース] タブ](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h")  
  
 ユーザーが **[トレースの開始]** をクリックして **[OK]** をクリックすると **、SQLManageDataSources**を使用すると、そのコンピューターで現在実行中のすべてのアプリケーションのトレースを手動で実行できます。  
  
 ユーザーが **[ログ ファイルのパス**] ボックスでトレース ファイルの名前を指定し **、[OK] を**クリックすると、システム情報の [ODBC] セクションの**TraceFile**キーワードが指定した名前**に設定されます**。  
  
> [!IMPORTANT]  
>  Windows 8 で最初に Visual Studio アナライザーのサポートが削除されました (Visual Studio アナライザーは、以前のバージョンの Visual Studio にのみ含まれていました)。 代替トラブルシューティングメカニズムを使用するには、BID トレースを使用します。  
  
 ユーザーが **[Visual Studio アナライザーの開始**] をクリックし **、[OK] を**クリックすると、Visual Studio アナライザーが有効になります。 **[Visual Studio アナライザーの停止**] がクリックされるまで、この機能は有効のままです。  
  
 トレースの詳細については、「[トレース](../../../odbc/reference/develop-app/tracing.md)」を参照してください。 **トレース**キーワードと**トレース ファイル**キーワードの詳細については[、「ODBC サブキー](../../../odbc/reference/install/odbc-subkey.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの作成|[データ ソースを作成します。](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|
