---
title: "ステートメント ハンドルを割り当て |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d81aa8ac131a10e91beee3497611f1574cc186d2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="allocating-a-statement-handle"></a>ステートメント ハンドルの割り当てください。
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションでステートメントを実行する前に、ステートメント ハンドルを割り当てる必要があります。 これは呼び出すことによって、 **SQLAllocHandle**で、 *HandleType*パラメーターに SQL_HANDLE_STMT を設定し、 *InputHandle*接続ハンドルを指すです。  
  
 ステートメント属性は、ステートメント ハンドルの特徴を表します。 ブックマークやカーソルを使用してサンプル ステートメント属性を取り込み、ステートメントの結果セットと共に使用することができます。 ステートメント属性が設定されて[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)、その現在の設定を使用して取得されて[SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)です。 アプリケーションでステートメント属性を設定する必要はありません。すべてのステートメント属性には既定値があり、一部の属性は、ドライバー固有の属性になっています。  
  
 複数の ODBC ステートメント オプションと接続オプションを使用する場合は、注意が必要です。 呼び出す[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)で*fOption* SQL_ATTR_LOGIN_TIMEOUT コントロールに、アプリケーションが (0 の接続を確立するために待機中にタイムアウトへの接続試行を待機する時間を設定します。無期限の待機を指定) します。 応答時間が遅いサイトでは、この値を高く設定して、接続の完了までに十分な時間を与えることができます。 ただしこの間隔は、ドライバーが接続できない場合に、妥当な時間内にユーザーに応答できる程度に低く抑える必要があります。  
  
 呼び出す**SQLSetStmtAttr**で*fOption*に SQL_ATTR_QUERY_TIMEOUT を設定は、実行時間の長いクエリから、サーバーと、ユーザーを保護するために、クエリのタイムアウト間隔を設定します。  
  
 呼び出す**SQLSetStmtAttr**で*fOption*に SQL_ATTR_MAX_LENGTH を設定の量を制限する**テキスト**と**イメージ**データを個別のステートメントを取得できます。 呼び出す**SQLSetStmtAttr**で*fOption* SQL_ATTR_MAX_ROWS を設定する最初の行セットを制限も *n* すべてのアプリケーションである場合は、行数が必要です。 SQL_ATTR_MAX_ROWS を設定すると、ドライバーがサーバーに対して SET ROWCOUNT ステートメントを実行することになります。 全体に影響[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメント、トリガーや更新などです。  
  
 上記のオプションを設定するときは注意が必要です。 SQL_ATTR_MAX_LENGTH と SQL_ATTR_MAX_ROWS の場合、接続ハンドルのすべてのステートメント ハンドルが同じ設定になるようにすることをお勧めします。 ドライバーが、あるステートメント ハンドルから、これらのオプションに異なる値を持つ別のステートメント ハンドルに切り替える場合、適切な SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを生成して、設定を変更する必要があります。 ユーザー SQL ステートメントには、バッチ内では先頭に含めなければならないステートメントを含めることができるので、ドライバーはユーザー SQL ステートメントと同じバッチ内にこれらのステートメントを配置することはできません。 ドライバーは SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを別のバッチで送信する必要があります。その結果、サーバーに対する追加のラウンドトリップが自動的に生成されます。  
  
## <a name="see-also"></a>参照  
 [実行中のクエリ &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
