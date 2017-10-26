---
title: "SQLWriteDSNToIni 関数 |Microsoft ドキュメント"
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
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 230accf6ae34f7b6bbced597e6e8bf2991bc8544
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni 関数
**準拠**  
 1.0 ODBC のバージョンで導入されました。  
  
 **概要**  
 **SQLWriteDSNToIni**システム情報をデータ ソースを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>引数  
 *lpszDSN*  
 [入力]追加するデータ ソースの名前です。  
  
 *lpszDriver*  
 [入力]ドライバーの名前 (通常は、関連付けられた DBMS の名前)、物理ドライバー名の代わりにユーザーに表示されます。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLWriteDSNToIni**は FALSE を返します、関連付けられている* \*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、 * \*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_DSN|無効な DSN|*LpszDSN*引数には、DSN に無効な文字列が含まれています。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszDriver*引数が無効です。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|インストーラーは、レジストリの DSN を作成できませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLWriteDSNToIni**システム情報 [ODBC データ ソース] セクションに、データ ソースを追加します。 データ ソースの仕様のセクションを作成し、1 つのキーワードを追加します (**ドライバー**) ドライバーの値として DLL の名前に置き換えます。 データ ソースの仕様のセクションで既に存在する場合、 **SQLWriteDSNToIni**新しいものを作成する前に、古いセクションを削除します。  
  
 この関数の呼び出し元は、システム情報のデータ ソースの仕様のセクションに、ドライバー固有のキーワードと値を追加する必要があります。  
  
 場合は、データ ソースの名前は、既定**SQLWriteDSNToIni**もシステム情報 の既定のドライバーの仕様のセクションを作成します。  
  
 この関数は、DLL のセットアップからのみ呼び出す必要があります。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはデータ ソースを削除します。|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)で DLL のセットアップ)|  
|追加、変更、またはデータ ソースを削除します。|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|システム情報のデータ ソース名を削除します。|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|

