---
title: "SQLManageDataSources |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLManageDataSources
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLManageDataSources
helpviewer_keywords: SQLManageDataSources [ODBC]
ms.assetid: ac6d186f-b394-406c-94c4-c6331d1ca468
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b10fd1109c41d1d19418ce83dd14b60488a85fd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **SQLManageDataSources**ユーザーことができますを設定、追加、およびシステム情報のデータ ソースを削除 ダイアログ ボックスが表示されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>引数  
 *hwnd*  
 [入力]親ウィンドウ ハンドル。  
  
## <a name="returns"></a>戻り値  
 **SQLManageDataSources**場合は FALSE を返します*hwnd*有効なウィンドウ ハンドルではありません。 それ以外の場合、TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLManageDataSources**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|呼び出し**ConfigDSN**できませんでした。|  
|ODBC_ERROR_INVALID__HWND|無効なウィンドウ ハンドル|*Hwnd*引数が無効または NULL。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="managing-data-sources"></a>データ ソースの管理  
 **SQLManageDataSources**は最初に表示、 **ODBC データ ソース アドミニストレーター**ダイアログ ボックスで、次の図に示すようにします。  
  
 ![ODBC データ ソース アドミニストレーター ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 ダイアログ ボックスには、システムについては、3 つのタブの下に表示されているデータ ソースが表示されます:**ユーザー DSN**、**システム DSN**、および**ファイル DSN**です。 かどうか、ユーザー データ ソースをダブルクリックするかがデータ ソースを選択してクリックした**構成**、 **SQLManageDataSources**呼び出し**ConfigDSN** ODBC_CONFIG_ を持つ DLL のセットアップDSN オプション。  
  
 ユーザーがクリックした場合**追加**、 **SQLManageDataSources**が表示されます、**データ ソースの新規作成**ダイアログ ボックスで、次の図に示すようにします。  
  
 ![新しいデータ ソース ダイアログ ボックスを作成する](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 ダイアログ ボックスには、インストールされているドライバーの一覧が表示されます。 かどうか、ユーザー、ドライバーをダブルクリックするか、ドライバーを選択してクリックする、 **OK**、 **SQLManageDataSources**呼び出し**ConfigDSN**セットアップ DLL で ODBC_ADD_DSN オプションを渡します。  
  
 ユーザーがデータ ソースを選択してクリックすると**削除**、 **SQLManageDataSources**ユーザーがデータ ソースを削除するかどうかを確認します。 ユーザーがクリックした場合**はい**、 **SQLManageDataSources**呼び出し**ConfigDSN** ODBC_REMOVE_DSN オプションを使用してセットアップ DLL にします。  
  
 **データ ソースの新規作成**を追加またはユーザー データ ソース、システム データ ソース、またはファイル データ ソースを削除 ダイアログ ボックスを使用します。  
  
## <a name="user-dsns"></a>ユーザー Dsn  
 個々 のユーザー用に作成された Dsn はシステム Dsn と区別するためのユーザー Dsn と呼ばれます。 ユーザー Dsn は、システム情報に、次のように登録されます。  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>システム Dsn  
 **データ ソースの新規作成**ダイアログ ボックスで、ローカル コンピューターまたは 1 つを削除するシステム データ ソースを追加したりすると、システム データ ソースの構成を設定できます。  
  
 システム データ ソース名 (DSN) をセットアップ、データ ソースは、同じコンピューター上の 1 つ以上のユーザーによって使用できます。 アクセスできるように、データ ソースに、マシンにログオンしているユーザーがいない場合でも、システム全体のサービスによっても使用できます。  
  
 システム DSN は、HKEY_CURRENT_USER エントリではなくシステム情報で、HKEY_LOCAL_MACHINE エントリに登録されます。 1 人のユーザーの特定のユーザー名とパスワードを使用してログオンしますが、使用できるそのマシンのすべてのユーザーまたはシステム全体の自動サービスに関連付けられていません。 システム DSN は、ただし、1 つのマシンに関連付けられています。 コンピューター間でのリモートの Dsn を使用する機能はサポートされません。 システム Dsn は、システム情報に、次のように登録されます。  
  
 HKEY_LOCAL_MACHINE ソフトウェア ODBC Odbc.ini  
  
## <a name="file-dsns"></a>ファイル Dsn  
 ファイル データ ソースには、データ ソース名はありませんが、コンピューターのデータ ソースと任意の 1 つのユーザーまたはコンピューターに登録されていません。 そのデータ ソースの接続情報は、任意のコンピューターにコピーできる .dsn ファイルに含まれます。 ファイル データ ソース、共有可能 .dsn ファイルをネットワークに存在する場合できできます同時に、ネットワーク上の複数のユーザーが、ユーザーがある適切なドライバーがインストールされている限りです。 ファイル データ ソースも解除できます共有可能、それを使用して 1 台のコンピューターでのみ場合。  
  
 ファイルのデータ ソースの詳細については、次を参照してください。[を使用してファイル データ ソースの接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)、を参照してくださいまたは[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
## <a name="managing-drivers"></a>ドライバーの管理  
 ユーザーがクリックした場合、**ドライバー**  タブで、 **ODBC データ ソース アドミニストレーター**ダイアログ ボックスで、 **SQLManageDataSources**システムにインストールされている ODBC ドライバーの一覧を表示ドライバーに関する情報。 表示される日付は、次の図に示すように、ドライバーの作成日です。  
  
 ![ODBC データ ソース アドミニストレーター [ドライバー] タブ](../../../odbc/reference/syntax/media/ch23g.gif "ch23g")  
  
## <a name="tracing-options"></a>[トレース オプション]  
 ユーザーがクリックした場合、**トレース** タブで、 **ODBC データ ソース アドミニストレーター**ダイアログ ボックスで、 **SQLManageDataSources**次に示すようにトレース オプションが表示されます図。  
  
 ![ODBC データ ソース アドミニストレーター [トレース] タブ](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h")  
  
 ユーザーがクリックした場合**トレースの開始** をクリックし、 **OK**、 **SQLManageDataSources**マシンで現在実行されているすべてのアプリケーションを手動でトレースを有効にします。  
  
 ユーザーが内のトレース ファイルの名前を指定するかどうか、**ログ ファイルのパス**テキスト ボックスをクリックする**OK**、 **SQLManageDataSources**設定、 **TraceFile**の指定した名前のシステム情報 [ODBC] セクションでキーワード。  
  
> [!IMPORTANT]  
>  Visual Studio Analyzer のサポートが以降 (Visual Studio Analyzer のみに含まれていました Visual Studio の古いバージョンです。) Windows 8 では削除されました。 トラブルシューティング メカニズムの代わりの BID トレースを使用します。  
  
 ユーザーがクリックした場合**Visual Studio Analyzer の開始** をクリックし、 **OK**、Visual Studio Analyzer を有効にします。 これまで有効のままに**Visual Studio Analyzer の停止**をクリックします。  
  
 トレースの詳細については、次を参照してください。[トレース](../../../odbc/reference/develop-app/tracing.md)です。 詳細については、**トレース**と**TraceFile**キーワードを参照してください[ODBC サブキー](../../../odbc/reference/install/odbc-subkey.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|データ ソースの作成|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|
