---
title: ドライバ マネージャ&#39;接続プロセスでの役割 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], role in connection process
- connecting to data source [ODBC], driver manager
- connecting to driver [ODBC], driver manager
- ODBC driver manager [ODBC]
ms.assetid: 77c05630-5a8b-467d-b80e-c705dc06d601
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0227a4063573cb05ecaa9434605ba35f2811bd06
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305803"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>ドライバー マネージャー&#39;接続プロセスでの役割
アプリケーションは、ドライバー関数を直接呼び出さないことに注意してください。 代わりに、同じ名前でドライバー マネージャー関数を呼び出し、ドライバー マネージャーは、ドライバー関数を呼び出します。 通常、これはほぼ即座に起こります。 たとえば、アプリケーションは、ドライバー マネージャーで**SQLExecute**を呼び出し、いくつかのエラー チェックの後、ドライバー マネージャーは、ドライバーで**SQLExecute**を呼び出します。  
  
 接続プロセスが異なります。 アプリケーションは、SQL_HANDLE_ENVとSQL_HANDLE_DBCオプションを使用して**SQLAllocHandle**を呼び出すと、関数は、ドライバー マネージャーでのみハンドルを割り当てます。 ドライバー マネージャーは、呼び出すドライバーを知らないので、ドライバーでこの関数を呼び出しません。 同様に、アプリケーションが接続されていない接続のハンドルを**SQLSetConnectAttr**または**SQLGetConnectAttr**に渡す場合は、ドライバー マネージャーのみが関数を実行します。 設定されていない属性の値を取得し、ODBC がデフォルト値を定義していない場合に、接続ハンドルから属性値を格納または取得し、SQLSTATE 08003 (接続が開いていない) を返します。  
  
 アプリケーションが呼び出すとき**に SQLConnect** **、SQLDriverConnect**、または**SQLBrowseConnect、** ドライバー マネージャーは、最初に使用するドライバーを決定します。 次に、ドライバが現在接続に読み込まれているかどうかを確認します。  
  
-   接続にドライバーが読み込まれていない場合、ドライバー マネージャーは、指定されたドライバーが同じ環境で別の接続に読み込まれているかどうかを確認します。 ない場合、ドライバー マネージャーは、接続上のドライバーを読み込み、SQL_HANDLE_ENV オプションを使用してドライバーで**SQLAllocHandle**を呼び出します。  
  
     ドライバー マネージャーは、読み込まれたかどうかにかかわらず、SQL_HANDLE_DBC オプションを使用してドライバーで**SQLAllocHandle**を呼び出します。 アプリケーションが接続属性を設定した場合、ドライバー マネージャーは、ドライバーで**SQLSetConnectAttr**を呼び出します。エラーが発生した場合、ドライバー マネージャーの接続関数は SQLSTATE IM006 (ドライバーの**SQLSetConnectAttr**に失敗しました) を返します。 最後に、ドライバー マネージャーは、ドライバーの接続関数を呼び出します。  
  
-   指定されたドライバーが接続に読み込まれている場合、ドライバー マネージャーは、ドライバーの接続関数のみを呼び出します。 この場合、ドライバーは、接続のすべての接続属性が現在の設定を維持することを確認する必要があります。  
  
-   接続に別のドライバーが読み込まれている場合、ドライバー マネージャーは、接続を解放するドライバーで**SQLFreeHandle**を呼び出します。 ドライバーを使用する他の接続がない場合、ドライバー マネージャーは、ドライバーで**SQLFreeHandle**を呼び出して、環境を解放し、ドライバーをアンロードします。 ドライバー マネージャーは、接続でドライバーが読み込まれていない場合と同じ操作を実行します。  
  
 ドライバー マネージャーは、*ドライバー*の**SQLAllocHandle**と呼び出す前に、環境**ハンドル**(*henv*) をロック**SQL_HANDLE_DBCします**。  
  
 アプリケーションが**SQLDisconnect**を呼び出すと、ドライバー マネージャーは、ドライバーで**SQLDisconnect**を呼び出します。 ただし、アプリケーションがドライバーに再接続した場合に備えて、ドライバーは読み込まれたままになります。 アプリケーションは、SQL_HANDLE_DBC オプションを使用して**SQLFreeHandle**を呼び出すと、ドライバー マネージャーは、ドライバーで**SQLFreeHandle**を呼び出します。 ドライバーが他の接続で使用されていない場合、ドライバー マネージャーは、ドライバーの**SQLFreeHandle** SQL_HANDLE_ENV オプションを使用して呼び出し、ドライバーをアンロードします。
