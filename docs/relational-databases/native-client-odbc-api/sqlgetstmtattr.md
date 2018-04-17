---
title: SQLGetStmtAttr |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d00929114af83806a3b7c7ac7f98d01d603bd845
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーがドライバー固有のステートメント属性を公開する SQLGetStmtAttr を拡張します。  
  
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)の両方がリストのステートメント属性を読み書きします。 ここでは、読み取り専用のステートメント属性のみを示します。  
  
## <a name="sqlsoptsscurrentcommand"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 コマンド バッチの現在のコマンドを公開します。 バッチ内のコマンドの位置を表す整数を返します。 *ValuePtr*値型は SQLLEN です。  
  
## <a name="sqlsoptssnocountstatus"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 SQL_SOPT_SS_NOCOUNT_STATUS 属性は、NOCOUNT の現在の設定を示すオプションを制御するかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ステートメントによって影響を受ける行の数を報告するときに[SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md)と呼びます。 *ValuePtr*値型は SQLLEN です。  
  
|値|Description|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT を OFF にします。 SQLRowCount では、影響を受ける行の数を返します。|  
|SQL_NC_ON|NOCOUNT を ON にします。 影響を受ける行の数が SQLRowCount によって返されないと、返される値は 0 です。|  
  
 SQLRowCount では、0 を返します、アプリケーションは SQL_SOPT_SS_NOCOUNT_STATUS をテストする必要があります。 SQL_NC_ON が返される場合は SQLRowCount から 0 の値のみが示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が行の数は返されません。 SQL_NC_OFF が返される場合は NOCOUNT が無効、ある SQLRowCount から 0 の値をステートメントによって影響されなかったすべての行を意味します。  
  
 SQL_SOPT_SS_NOCOUNT_STATUS が SQL_NC_OFF のとき、アプリケーションは SQLRowCount の値を表示しない必要があります。 大きなバッチやストアド プロシージャには、複数の SET NOCOUNT ステートメントが含まれていることがあるので、SQL_SOPT_SS_NOCOUNT_STATUS が一定であると想定することはできません。 このオプションは、では 0 を返しますたびにテストしてください。  
  
## <a name="sqlsoptssquerynotificationmsgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 クエリ通知要求のメッセージ テキストを返します。  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr とテーブル値パラメーター  
 テーブル値パラメーターを使用する場合は、アプリケーション パラメーター記述子 (APD) の SQL_SOPT_SS_PARAM_FOCUS の値を取得する SQLGetStmtAttr を呼び出すことができます。 SQL_SOPT_SS_PARAM_FOCUS の詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLSetStmtAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59370)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
