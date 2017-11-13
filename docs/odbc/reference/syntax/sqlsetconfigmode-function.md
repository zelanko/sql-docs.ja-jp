---
title: "SQLSetConfigMode 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8919f758c486e6569b9620fcaa7bcf76f4dac0f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLSetConfigMode** DSN の値を一覧表示する Odbc.ini エントリがシステム情報の場所を示す構成モードを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>引数  
 *wConfigMode*  
 [入力]インストーラーの構成モード (「コメント」を参照してください)。 値*wConfigMode*を指定できます。  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetConfigMode**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|無効なパラメーターのシーケンス|*WConfigMode* ODBC_USER_DSN、ODBC_SYSTEM_DSN、または ODBC_BOTH_DSN が、引数に含まれていませんでした。|  
  
## <a name="comments"></a>コメント  
 この関数は、システム情報の DSN の値を一覧表示する Odbc.ini エントリの場所を設定に使用されます。 場合*wConfigMode*は ODBC_USER_DSN、DSN ユーザー DSN と、関数は、HKEY_CURRENT_USER の Odbc.ini エントリから読み取ります。 ODBC_SYSTEM_DSN である場合は、DSN はシステム DSN と関数は、HKEY_LOCAL_MACHINE 内の Odbc.ini エントリから読み取ります。 ODBC_BOTH_DSN の場合は、HKEY_CURRENT_USER 試行すると、失敗した場合は、HKEY_LOCAL_MACHINE 使用されます。  
  
 この関数には影響しません**SQLCreateDataSource**と**SQLDriverConnect**です。 呼び出してドライバーがレジストリから読み取るときに設定する、構成モードでは**SQLGetPrivateProfileString**や呼び出すことによって、レジストリに書き込まれます**SQLWritePrivateProfileString**です。 呼び出す**SQLGetPrivateProfileString**と**SQLWritePrivateProfileString**構成モードを使用して操作するために、レジストリのどの部分を確認します。  
  
> [!CAUTION]  
>  **SQLSetConfigMode**適切に機能する、ODBC のインストーラーが失敗するときに必要な; モードは正しく設定されている場合のみ呼び出す必要があります。  
  
 **SQLSetConfigMode**構成モードのレジストリを直接変更します。 これは、プロセスへの呼び出しによって、構成モードを変更するのとは別に**SQLConfigDataSource**です。 呼び出し**SQLConfigDataSource** DSN を変更する場合、ユーザーとシステム Dsn を区別するために、構成モードを設定します。 戻る、前に**SQLConfigDataSource** BOTHDSN 構成モードに戻します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|データ ソースを作成します。|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|接続文字列やダイアログ ボックスを使用してデータ ソースに接続します。|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|構成モードを取得します。|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|

