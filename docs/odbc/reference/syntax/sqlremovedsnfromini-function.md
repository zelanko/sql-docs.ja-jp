---
title: SQLRemoveDSNFromIni 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac2128424e1b48ecc82a0d0534db9222ad6ee734
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni 関数
**準拠**  
 1.0 ODBC のバージョンで導入されました。  
  
 **概要**  
 **SQLRemoveDSNFromIni**システム情報からデータ ソースを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>引数  
 *lpszDSN*  
 [入力]削除するデータ ソースの名前です。  
  
## <a name="returns"></a>返します。  
 関数は、データ ソースが削除または Odbc.ini ファイルで、データ ソースはなかった場合に TRUE を返します。 データ ソースを削除に失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLRemoveDSNFromIni**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_DSN|無効な DSN|*LpszDSN*引数が無効です。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|インストーラーは、レジストリから DSN 情報を削除できませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLRemoveDSNFromIni**のシステム情報 [ODBC データ ソース] セクションからデータ ソース名を削除します。 また、システム情報からデータ ソースの仕様のセクションを削除します。  
  
 この関数は、ドライバーのセットアップ ライブラリからのみ呼び出す必要があります。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはデータ ソースを削除します。|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|追加、変更、またはデータ ソースを削除します。|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|既定のデータ ソースを削除します。|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|システム情報へのデータ ソース名の追加|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
