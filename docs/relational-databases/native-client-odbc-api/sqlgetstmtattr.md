---
title: をクリックして行う |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f59b7f006387beea3d213b7f120e567487232e69
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282057"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは、ドライバー固有のステートメント属性を公開する SQLGetStmtAttr を拡張します。  
  
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)は、読み取りと書き込みの両方のステートメント属性をリストします。 ここでは、読み取り専用のステートメント属性のみを示します。  
  
## <a name="sql_sopt_ss_current_command"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 コマンド バッチの現在のコマンドを公開します。 バッチ内のコマンドの位置を表す整数を返します。 *値が*SQLLEN 型です。  
  
## <a name="sql_sopt_ss_nocount_status"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 SQL_SOPT_SS_NOCOUNT_STATUS属性は[、SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md)が呼び出されたときにステートメントの影響[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を受ける行の数を報告するかどうかを制御する NOCOUNT オプションの現在の設定を示します。 *値が*SQLLEN 型です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT を OFF にします。 影響を受ける行の数を返します。|  
|SQL_NC_ON|NOCOUNT を ON にします。 影響を受ける行数は SQLRowCount によって返されず、戻り値は 0 です。|  
  
 SQLRowCount が 0 を返す場合、アプリケーションはSQL_SOPT_SS_NOCOUNT_STATUSテストする必要があります。 SQL_NC_ONが返された場合、SQLRowCount の値 0 は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]行カウントを返さなかったことを示します。 SQL_NC_OFF が返される場合、NOCOUNT が無効になっており、SQLRowCount から返される値が 0 であると、ステートメントで処理された行がなかったことを示します。  
  
 SQL_SOPT_SS_NOCOUNT_STATUS が SQL_NC_OFF のときは、アプリケーションでは、SQLRowCount の値を表示しないでください。 大きなバッチやストアド プロシージャには、複数の SET NOCOUNT ステートメントが含まれていることがあるので、SQL_SOPT_SS_NOCOUNT_STATUS が一定であると想定することはできません。 このオプションは、SQLRowCount が 0 を返すたびにテストする必要があります。  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 クエリ通知要求のメッセージ テキストを返します。  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr とテーブル値パラメーター  
 SQLGetStmtAttr は、テーブル値パラメーターを使用する場合に、アプリケーション・パラメーター記述子 (APD) 内のSQL_SOPT_SS_PARAM_FOCUSの値を取得するために呼び出すことができます。 SQL_SOPT_SS_PARAM_FOCUSの詳細については、 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を参照してください。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59370)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
