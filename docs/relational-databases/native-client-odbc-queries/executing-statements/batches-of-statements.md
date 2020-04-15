---
title: ステートメントのバッチ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6054ea09c297bc0d8521d0bc3e509585012e8ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297988"
---
# <a name="batches-of-statements"></a>ステートメントのバッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ステートメントのバッチ[!INCLUDE[tsql](../../../includes/tsql-md.md)]には **、2**つ以上のステートメント ;)が含まれています。 [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) 次に例を示します。  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 バッチでは、通常、ネットワーク トラフィックが削減されるので、複数のステートメントを個別に送信するよりも効率的になる可能性があります。 現在の結果セットが終了したら、次の結果セットに位置を取得するには[、SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md)を使用します。  
  
 行セットのサイズが 1 になっている、順方向専用かつ読み取り専用のカーソルの既定値に ODBC カーソル属性が設定されている場合は、常にバッチを使用できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してサーバー カーソルを使用しているときにバッチを実行すると、サーバー カーソルが暗黙的に既定の結果セットに変換されます。 **SQL_SUCCESS_WITH_INFOを****返し****、SQLGetDiagRec**の呼び出しは次の関数を返します。  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;ステートメントの実行](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
