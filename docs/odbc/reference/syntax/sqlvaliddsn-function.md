---
title: "SQLValidDSN 関数 |Microsoft ドキュメント"
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
apiname: SQLValidDSN
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLValidDSN
helpviewer_keywords: SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c745b7ac285f09ff80478dab911b3cd3a9fc94d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **SQLValidDSN**名前は、システム情報を追加する前に、長さとデータ ソース名の有効性をチェックします。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>引数  
 *lpszDSN*  
 [入力]データ ソースの名前を確認します。  
  
## <a name="returns"></a>戻り値  
 関数は、データ ソース名が有効な場合に TRUE を返します。 データ ソース名が無効であるか、関数呼び出しが失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLValidDSN**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 A  *\*pfErrorCode*が返されるだけ関数呼び出しが失敗したかどうか、データ ソース名が無効なために、FALSE が返された場合にありません。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLValidDSN** 、運転免許によって呼び出される[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)をデータ ソース名の長さと、データ ソースの個別の文字の有効性を確認します。 これは、Sqlext.h で定義されている名前の長さが SQL_MAX_DSN_LENGTH より大きいかどうかを確認します。 (データ ソース名の長さがによってチェックも[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md))。**SQLValidDSN**データ ソース名に次の無効な文字を含めるかどうかを確認します。  
  
 [ ] { } ( ) , ; ? * = ! @ \  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはデータ ソースを削除します。|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)で DLL のセットアップ)|  
|追加、変更、またはデータ ソースを削除します。|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|システム情報へのデータ ソース名の書き込み|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
