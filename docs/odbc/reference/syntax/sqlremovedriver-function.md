---
title: "SQLRemoveDriver 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLRemoveDriver
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLRemoveDriver
helpviewer_keywords: SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2f1a0e147d300e193ebadab06fb220e90aeb901
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLRemoveDriver**システム情報の Odbcinst.ini エントリからドライバーに関する情報を削除または変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *lpszDriver*  
 [入力]システム情報の Odbcinst.ini キーに登録されているドライバーの名前。  
  
 *fRemoveDSN*  
 [入力]有効な値は次のとおりです。  
  
 TRUE: 削除 Dsn に指定されたドライバーに関連付けられている*lpszDriver*です。 FALSE: Dsn に指定されたドライバーに関連付けられている削除しない*lpszDriver*です。  
  
 *lpdwUsageCount*  
 [出力]この関数が呼び出された後に、ドライバーの使用率カウントします。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。 エントリが存在しない場合、システム情報でこの関数が呼び出されたときに、関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLRemoveDriver**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|コンポーネントがレジストリに見つかりません|インストーラーは、レジストリに存在しませんでしたや、レジストリに見つかりませんでしたので、ドライバの情報を削除できませんでした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszDriver*引数が無効です。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|インクリメントまたはコンポーネントの使用率カウントは減少できませんでした。|ドライバーの使用率カウントをデクリメントするためにインストーラーが失敗しました。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|*FRemoveDSN*引数が TRUE です。 ただし、1 つまたは複数の Dsn を削除できませんでした。 呼び出し**SQLConfigDriver** ODBC_REMOVE_DRIVER 要求に失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLRemoveDriver**補完するもの、 [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)コンポーネントの使用法のシステム情報のカウント関数と更新プログラム。 この関数は、セットアップ アプリケーションからのみ呼び出す必要があります。  
  
 **SQLRemoveDriver**コンポーネントの使用状況カウント値を 1 だけデクリメントされます。 コンポーネントの使用率カウントが 0 になった場合、次のようになります。  
  
1.  **SQLConfigDriver** ODBC_REMOVE_DRIVER オプションを使用して関数が呼び出されます。 場合、 *fRemoveDSN*オプションが TRUE に設定されている、 **ConfigDSN**関数呼び出し**SQLRemoveDSNFromIni**で指定されたドライバーに関連付けられているすべてのデータ ソースを削除するには*lpszDriver です。* 場合、 *fRemoveDSN*オプションが FALSE に設定されているデータ ソースは削除されません場合、。  
  
2.  システム情報 のドライバー エントリが削除されます。 ドライバーのエントリは、システムについては、次の場所、ドライバー名の下には。  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver**すべてのファイルを実際に削除されません。 呼び出し元のプログラムは、ファイルを削除して、ファイルの使用率カウントを保守を担当します。 コンポーネントの使用率カウントとファイルの使用率カウントの両方に達した後にのみ、0 は、物理的に削除ファイルになります。 コンポーネントの一部のファイルを削除でき、他のユーザーは削除されません、ファイルの使用率カウントをインクリメントが他のアプリケーションでファイルを使用するかどうかによって異なります。  
  
 **SQLRemoveDriver**アップグレード プロセスの一部としても呼ばれます。 アプリケーション検出した場合のアップグレードを実行する必要があることと、ドライバーが既にインストール、ドライバーを削除して再インストールする必要があります。 **SQLRemoveDriver**コンポーネント使用率カウントをデクリメントするために呼び出す必要がありますはまずし**SQLInstallDriverEx**コンポーネントの使用率カウントをインクリメントするために呼び出す必要があります。 アプリケーションのセットアップ プログラムは、古いファイルを新しいファイルに置き換える必要があります。 ファイルの使用率カウントは変わりません、および古いバージョンのファイルを使用するその他のアプリケーションの新しいバージョンが使用されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはドライバーを削除します。|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)で DLL のセットアップ)|  
|追加、変更、またはドライバーを削除します。|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|ドライバーをインストールします。|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|
