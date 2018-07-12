---
title: 非同期モードと SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4465e572aaa0068e5a5c9f84c1a6525438e75c17
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431571"
---
# <a name="asynchronous-mode-and-sqlcancel"></a>非同期モードと SQLCancel
  ODBC 関数には、同期して動作する関数と非同期に動作する関数があります。 アプリケーションでは、ステートメント ハンドルまたは接続ハンドルのいずれかに対して非同期動作を有効にすることができます。 オプションが接続ハンドル用に設定されている場合、接続ハンドルのすべてのステートメント ハンドルに影響します。 アプリケーションで次のステートメントを使用すると、非同期動作を有効または無効にすることができます。  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 アプリケーションが同期モードで ODBC 関数を呼び出した場合、サーバーでのコマンドの実行が完了したことがドライバーに通知されるまでは、ドライバーからアプリケーションに制御が戻りません。  
  
 非同期動作の場合は、ドライバーからサーバーにコマンドを送信する前でも、ドライバーからアプリケーションに直ちに制御が戻ります。 ドライバーは、リターン コードを SQL_STILL_EXECUTING に設定します。 アプリケーションでは他の作業を実行できます。  
  
 アプリケーションでコマンドが完了したかどうかをテストするときは、ドライバーに対して同じ関数を同じパラメーターを指定して呼び出します。 ドライバーがサーバーからまだ応答を受け取っていない場合、SQL_STILL_EXECUTING が再び返されます。 アプリケーションでは、リターン コードが SQL_STILL_EXECUTING 以外になるまで、定期的にコマンドをテストする必要があります。 アプリケーションで他のリターン コードを受け取ると、それが SQL_ERROR であっても、コマンドが完了したことがわかります。  
  
 コマンドが長時間未完了になることがあります。 アプリケーションの応答を待機することがなく、コマンドをキャンセルする場合、そのように呼び出すことによって**SQLCancel**同じステートメントを使用して、未完了のコマンドとして処理します。 これは、唯一の時間**SQLCancel**使用する必要があります。 プログラマによって使用**SQLCancel**の結果から途中、処理があるときに設定し、結果セットの残りの部分をキャンセルします。 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)または[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) 、未処理の結果セットの残りの部分にキャンセルするために使用する必要があります**SQLCancel**します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client ODBC ドライバー アプリケーションの作成](creating-a-driver-application.md)  
  
  
