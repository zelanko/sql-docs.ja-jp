---
title: ODBC 3.x ドライバの記述 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62f2a701fd5ac94c92d41494a4fd1ab023edaf25
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300362"
---
# <a name="writing-odbc-3x-drivers"></a>ODBC 3.x ドライバーの作成
次の表は、ODBC 3 での関数サポートを示しています。*x*ドライバと ODBC アプリケーション、および ODBC 3 に対して関数が呼び出されたときにドライバ マネージャによって実行されるマッピング。*x*ドライバ。  
  
|機能|サポートされています<br /><br /> によって、<br /><br /> ODBC 3.*x*<br /><br /> ドライバー。|サポートされています<br /><br /> によって、<br /><br /> ODBC 3.*x*<br /><br /> アプリケーション。|マップ/サポート<br /><br /> ODBC 3 によって。*x*<br /><br /> ドライバー マネージャー<br /><br /> ODBC 3 です。*x*ドライバ?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**コネクト**|いいえ|いいえ[1]|はい|  
|**SQLAllocEnv**|いいえ|いいえ[1]|はい|  
|**ハンドル**|はい|はい|いいえ|  
|**をクリックします。**|いいえ|いいえ[1]|はい|  
|**SQLBindCol**|はい|はい|いいえ|  
|**パラム**|いいえ|はい[2]|はい|  
|**SQLBindParameter**|はい|はい|いいえ|  
|**SQLBrowseConnect**|はい|はい|いいえ|  
|**オペレーション**|はい|はい|いいえ|  
|**SQLCancel**|はい|はい|いいえ|  
|**SQLCloseCursor**|はい|はい|いいえ|  
|**SQLColAttribute**|はい|はい|いいえ|  
|**属性**|いいえ[3]|いいえ|はい|  
|**SQLColumnPrivileges**|はい|はい|いいえ|  
|**SQLColumns**|はい|はい|いいえ|  
|**SQLConnect**|はい|はい|いいえ|  
|**を使用する**|はい|はい|はい[4]|  
|**データベースソース**|いいえ|はい|はい|  
|**SQLDescribeCol**|はい|はい|いいえ|  
|**SQLDescribeParam**|はい|はい|いいえ|  
|**接続解除**|はい|はい|いいえ|  
|**SQLDriverConnect**|はい|はい|いいえ|  
|**SQLDrivers**|いいえ|はい|はい|  
|**SQLEndTran**|はい|はい|いいえ|  
|**エラー**|いいえ|いいえ[1]|はい|  
|**SQLExecDirect**|はい|はい|いいえ|  
|**SQLExecute**|はい|はい|いいえ|  
|**フェッチ**|はい|いいえ|いいえ|  
|**SQLFetch**|はい|はい|いいえ|  
|**SQLFetchScroll**|はい|はい|いいえ|  
|**SQLForeignKeys**|はい|はい|いいえ|  
|**コネクト**|いいえ|はい[1]|はい|  
|**を実行する**|いいえ|はい[1]|はい|  
|**SQLFreeHandle**|はい|はい|いいえ|  
|**SQLFreeStmt**|はい|はい|いいえ|  
|**SQLGetConnectAttr**|はい|はい|いいえ|  
|**オプションを指定します。**|いいえ[5]|いいえ[1]|はい|  
|**SQLGetCursorName**|はい|はい|いいえ|  
|**SQLGetData**|はい|はい|いいえ|  
|**SQLGetDescField**|はい|はい|いいえ|  
|**SQLGetDescRec**|はい|はい|いいえ|  
|**SQLGetDiagField**|はい|はい|いいえ|  
|**SQLGetDiagRec**|はい|はい|いいえ|  
|**アズ・ビジトル**|はい|はい|いいえ|  
|**SQLGetFunctions**|いいえ[6]|はい|はい|  
|**SQLGetInfo**|はい|はい|いいえ|  
|**SQLGetStmtAttr**|はい|はい|いいえ|  
|**オプションを指定します。**|いいえ[5]|いいえ[1]|はい|  
|**SQLGetTypeInfo**|はい|はい|いいえ|  
|**SQLMoreResults**|はい|はい|いいえ|  
|**SQLNativeSql**|はい|はい|いいえ|  
|**SQLNumParams**|はい|はい|いいえ|  
|**SQLNumResultCols**|はい|はい|いいえ|  
|**SQLParamData**|はい|はい|いいえ|  
|**オプション**|いいえ|いいえ|はい|  
|**SQLPrepare**|はい|はい|いいえ|  
|**SQLPrimaryKeys**|はい|はい|いいえ|  
|**SQLProcedureColumns**|はい|はい|いいえ|  
|**SQLProcedures**|はい|はい|いいえ|  
|**SQLPutData**|はい|はい|いいえ|  
|**SQLRowCount**|はい|はい|いいえ|  
|**SQLSetConnectAttr**|はい|はい|いいえ|  
|**オプションを指定します。**|いいえ[5]|いいえ[1]|はい|  
|**カーソルを設定します。**|はい|はい|いいえ|  
|**SQLSetDescField**|はい|はい|いいえ|  
|**SQLSetDescRec**|はい|はい|いいえ|  
|**SQLSetEnvAttr**|はい|はい|いいえ|  
|**SQLSetPos**|はい|はい|いいえ|  
|**を使用する**|いいえ|いいえ|はい|  
|**スクロールオプション**|はい|はい|いいえ|  
|**SQLSetStmtAttr**|はい|はい|いいえ|  
|**オプションを設定します。**|いいえ[5]|いいえ[1]|はい|  
|**SQLSpecialColumns**|はい|はい|いいえ|  
|**SQLStatistics**|はい|はい|いいえ|  
|**SQLTablePrivileges**|はい|はい|いいえ|  
|**SQLTables**|はい|はい|いいえ|  
|**トランスアクト**|いいえ|いいえ[1]|はい|  
  
 [1] この関数は ODBC 3 では非推奨です。*x .* ODBC 3.*x*アプリケーションはこの関数を使用しないでください。 ただし、オープングループまたは ISO CLI 準拠のアプリケーションは、この関数を呼び出すことができます。  
  
 [2] ODBC 3.*x*アプリケーションでは **、SQLBind** **パラム**の代わりに SQL バインド パラメーターを使用する必要があります。 ただし、オープングループまたは ISO CLI 準拠のアプリケーションは、この関数を呼び出すことができます。  
  
 [3] ドライバーの作成者は ODBC 2 を注意する必要があります。*x*列属性SQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、およびSQL_COLUMN_LENGTHは**SQLColAttribute**でサポートされている必要があります。  
  
 [4] **SQLCopyDesc**は、記述子が別のドライバーに属する接続を介してコピーされている場合、ドライバー マネージャーによって部分的に実装されます。 ドライバーは、2 つの接続で**SQLCopyDesc**をサポートする必要があります。 ドライバー マネージャーだけで実装される**SQLDrivers**などの関数は、この一覧には表示されません。  
  
 [5] 特定の状況下では、ドライバがこの機能をサポートする必要があります。 詳細については、この関数のリファレンスページを参照してください。  
  
 [6] ドライバーがサポートする関数のセットが接続ごとに異なる場合は、ドライバーは**SQLGetFunctions**をサポートすることを選択できます。
