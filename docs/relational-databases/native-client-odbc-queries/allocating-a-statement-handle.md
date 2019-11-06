---
title: ステートメント ハンドルの割り当て |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 41bf309a1a2b1795f8d642ea7418289e94db4591
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937320"
---
# <a name="allocating-a-statement-handle"></a>ステートメント ハンドルの割り当て
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションでステートメントを実行する前に、ステートメント ハンドルを割り当てる必要があります。 これは呼び出すことによって、 **SQLAllocHandle**で、 *HandleType*パラメーターに sql_handle_stmt として設定し、 *InputHandle*接続ハンドルを指します。  
  
 ステートメント属性は、ステートメント ハンドルの特徴を表します。 ブックマークやカーソルを使用してサンプル ステートメント属性を取り込み、ステートメントの結果セットと共に使用することができます。 ステートメント属性が設定されて[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を使用して、現在の設定を取得して[SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)します。 アプリケーションでステートメント属性を設定する必要はありません。すべてのステートメント属性には既定値があり、一部の属性は、ドライバー固有の属性になっています。  
  
 複数の ODBC ステートメント オプションと接続オプションを使用する場合は、注意が必要です。 呼び出す[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)で*fOption* SQL_ATTR_LOGIN_TIMEOUT コントロールに、アプリケーションが (0 の接続を確立するために待機中にタイムアウトへの接続試行を待機する時間を設定します。無期限の待機を指定) します。 応答時間が遅いサイトでは、この値を高く設定して、接続の完了までに十分な時間を与えることができます。 ただしこの間隔は、ドライバーが接続できない場合に、妥当な時間内にユーザーに応答できる程度に低く抑える必要があります。  
  
 呼び出す**SQLSetStmtAttr**で*fOption*に SQL_ATTR_QUERY_TIMEOUT を設定は、実行時間の長いクエリから、サーバーと、ユーザーを保護するために、クエリのタイムアウト間隔を設定します。  
  
 呼び出す**SQLSetStmtAttr**で*fOption*に SQL_ATTR_MAX_LENGTH を設定の量が制限**テキスト**と**イメージ**データを個々 のステートメントを取得できます。 呼び出す**SQLSetStmtAttr**で*fOption* SQL_ATTR_MAX_ROWS を設定では、最初の行セットによっても制限*n*行の場合は、すべてのアプリケーションが必要です。 SQL_ATTR_MAX_ROWS を設定すると、ドライバーがサーバーに対して SET ROWCOUNT ステートメントを実行することになります。 これは、すべて影響[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメント、トリガーや更新など。  
  
 上記のオプションを設定するときは注意が必要です。 SQL_ATTR_MAX_LENGTH と SQL_ATTR_MAX_ROWS の場合、接続ハンドルのすべてのステートメント ハンドルが同じ設定になるようにすることをお勧めします。 ドライバーが、あるステートメント ハンドルから、これらのオプションに異なる値を持つ別のステートメント ハンドルに切り替える場合、適切な SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを生成して、設定を変更する必要があります。 ユーザー SQL ステートメントには、バッチ内では先頭に含めなければならないステートメントを含めることができるので、ドライバーはユーザー SQL ステートメントと同じバッチ内にこれらのステートメントを配置することはできません。 ドライバーは SET TEXTSIZE ステートメントと SET ROWCOUNT ステートメントを別のバッチで送信する必要があります。その結果、サーバーに対する追加のラウンドトリップが自動的に生成されます。  
  
## <a name="see-also"></a>関連項目  
 [クエリの実行&#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
