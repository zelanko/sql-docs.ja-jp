---
title: "SQLGetConfigMode 関数 |Microsoft ドキュメント"
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
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d52a471de1590df140f766a417820126ac191f77
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLGetConfigMode** DSN の値を一覧表示する Odbc.ini エントリがシステム情報の場所を示す構成モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>引数  
 *pwConfigMode*  
 [出力]構成モードを格納するバッファーへのポインター。 (「コメント」を参照してください)値* \*pwConfigMode*を指定できます。  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetConfigMode**は FALSE を返します、関連付けられている* \*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、 * \*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 この関数は、システム情報の DSN の値を一覧表示する Odbc.ini エントリの場所を確認に使用されます。 場合* \*pwConfigMode*は ODBC_USER_DSN、DSN ユーザー DSN と、関数は、HKEY_CURRENT_USER の Odbc.ini エントリから読み取ります。 ODBC_SYSTEM_DSN である場合は、DSN はシステム DSN と関数は、HKEY_LOCAL_MACHINE 内の Odbc.ini エントリから読み取ります。 HKEY_CURRENT_USER を試す ODBC_BOTH_DSN である場合、HKEY_LOCAL_MACHINE が使用されますが失敗した場合。  
  
 既定では、 **SQLGetConfigMode** ODBC_BOTH_DSN を返します。 呼び出しによってユーザー DSN またはシステム DSN を作成するときに**SQLConfigDataSource**関数が ODBC_USER_DSN または ODBC_SYSTEM_DSN DSN の変更中にユーザーとシステム Dsn を区別するために、構成モードを設定します。 戻る、前に**SQLConfigDataSource** ODBC_BOTH_DSN 構成モードに戻します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|構成モードの設定|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|

