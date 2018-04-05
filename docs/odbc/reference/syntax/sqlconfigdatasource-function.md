---
title: SQLConfigDataSource 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6678a9b2fd25a1c639d03753f7e89a47d287adf2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource 関数
**準拠**  
 1.0 ODBC のバージョンで導入されました。  
  
 **概要**  
 **SQLConfigDataSource**を追加、変更、またはデータ ソースを削除します。  
  
 機能**SQLConfigDataSource**にアクセスすることも[ODBCCONF です。EXE](../../../odbc/odbcconf-exe.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLConfigDataSource(  
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
  
 ODBC_ADD_DSN: は、新しいユーザー データ ソースを追加します。  
  
 ODBC_CONFIG_DSN: 構成 (変更) 既存のユーザー データ ソース。  
  
 ODBC_REMOVE_DSN: は、既存のユーザー データ ソースを削除します。  
  
 ODBC_ADD_SYS_DSN: は、新しいシステム データ ソースを追加します。  
  
 ODBC_CONFIG_SYS_DSN: は、既存のシステム データ ソースを変更します。  
  
 ODBC_REMOVE_SYS_DSN: は、既存のシステム データ ソースを削除します。  
  
 ODBC_REMOVE_DEFAULT_DSN: は、システム情報の既定データ ソースの仕様のセクションを削除します。 (これも既定ドライバーの仕様のセクション エントリから削除 Odbcinst.ini システム情報にします。 これは、*起こり*、非推奨と同じ機能を実行**SQLRemoveDefaultDataSource**関数です)。このオプションを指定すると、すべての呼び出しでは、その他のパラメーター **SQLConfigDataSource** Null にする必要があります以外の場合は、情報が NULL でない場合、無視されます。  
  
 *lpszDriver*  
 [入力]ドライバーの名前 (通常は、関連付けられた DBMS の名前)、物理ドライバー名の代わりにユーザーに表示されます。  
  
 *lpszAttributes*  
 [入力]二重の null で終わる、キーワードと値のペアの形式での属性の一覧。 詳細については、次を参照してください。 [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)です。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。 エントリが存在しない場合、システム情報でこの関数が呼び出されたときに、関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLConfigDataSource**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効または NULL。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*起こり*引数が、次のいずれか。<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszDriver*引数が無効です。 これをレジストリで見つかりませんでした。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*LpszAttributes*引数に構文エラーが含まれています。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|インストーラーでは、要求した操作は実行できませんでした、*起こり*引数。 呼び出し**ConfigDSN**できませんでした。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバーまたはトランスレーター セットアップ ライブラリを読み込むことができませんでした。|ドライバーのセットアップ ライブラリを読み込むことができませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLConfigDataSource**の値を使用して*lpszDriver*システム情報から、ドライバーのセットアップ DLL の完全なパスを読み取れません。 DLL および呼び出しが読み込まれます**ConfigDSN**に渡された同じ引数を使用します。  
  
 **SQLConfigDataSource**見つからないか、セットアップの DLL をロードすることがない場合、またはユーザーがダイアログ ボックスを取り消す場合は FALSE を返します。 受け取ったステータスを返すそれ以外の場合、 **ConfigDSN**です。  
  
 **SQLConfigDataSource**システム DSN をマップ*起こり*ユーザー DSN を*起こり*(ODBC_ADD_DSN に ODBC_ADD_SYS_DSN、ODBC_CONFIG_DSN、および ODBC_REMOVE_SYS ODBC_CONFIG_SYS_DSN s_DSN ODBC_REMOVE_DSN に)。 ユーザーとシステム Dsn を区別するために**SQLConfigDataSource**インストーラーに次の表に従って構成モードを設定します。 戻る、前に**SQLConfigDataSource** BOTHDSN 構成モードに戻します。 **ConfigDSN** (ドライバーによって実装される) 呼び出す必要があります**SQLWriteDSNToIni**と**SQLWritePrivateProfileString**システム DSN をサポートするためにします。 詳細については、次を参照してください。 [ConfigDSN 関数](../../../odbc/reference/syntax/configdsn-function.md)です。  
  
|*起こり*|構成モード|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはデータ ソースを削除します。|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)で DLL のセットアップ)|  
|システム情報のデータ ソース名を削除します。|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|システム情報へのデータ ソース名の追加|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
