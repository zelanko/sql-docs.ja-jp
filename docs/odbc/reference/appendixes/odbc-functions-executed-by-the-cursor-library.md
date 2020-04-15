---
title: カーソルライブラリによって実行される ODBC 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: 2f1d3386-7e59-4d55-a5b4-3440b61343a3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70fb48a8764a913ea4c2376c1a44bcd8712e7d29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298232"
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>カーソル ライブラリによって実行される ODBC 関数
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソルライブラリは、次の機能を実行します。 アプリケーションがこの一覧の関数を呼び出すと、ドライバー マネージャーは、ドライバーではなく、カーソル ライブラリを呼び出します。 カーソル ライブラリは、関数の実行時にドライバーを呼び出す場合があることに注意してください。  
  
|||  
|-|-|  
|**SQLBindCol**|**オプションを指定します。**|  
|**パラム**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**オプション**|  
|**SQLEndTran**|**SQLRowCount**|  
|**フェッチ**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**オプションを指定します。**|  
|**SQLFreeHandle**|**SQLSetDescField**|  
|**SQLFreeStmt**|**SQLSetDescRec**|  
|**SQLGetData**|**SQLSetPos**|  
|**SQLGetDescField**|**スクロールオプション**|  
|**SQLGetDescRec**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**オプションを設定します。**|  
|**SQLGetInfo**|**トランスアクト**|  
|**SQLGetStmtAttr**||
