---
title: SQL Server の既定の結果セットを使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d7101cf4775e5280c22cc27ecae009410d231d5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "62511687"
---
# <a name="using-sql-server-default-result-sets"></a>SQL Server の既定の結果セットの使用
  ODBC カーソルの既定の属性を次に示します。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 これらの属性が既定値に設定され[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ている場合、NATIVE Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC ドライバーでは、既定の結果セットが使用されます。 既定の結果セットは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるすべての SQL ステートメントに使用でき、結果セット全体をクライアントに転送する際の最も効率的な方法です。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、複数のアクティブな結果セット (MARS) のサポートが導入されました。アプリケーションは、接続ごとに複数のアクティブな既定の結果セットを持つことができるようになりました。 MARS は既定では有効になっていません。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のリリースでは、既定の結果セットは 1 つの接続における複数のアクティブなステートメントをサポートしていません。 SQL ステートメントが 1 つの接続で実行された後、サーバーは結果セットのすべての行が処理されるまで、その接続に対するクライアントからのコマンドを受け付けません (結果セットの残りの行の処理を取り消す要求は除きます)。 部分的に処理された結果セットの残りの部分を取り消すには、 *Foption*パラメーターを SQL_CLOSE に設定して[sqlcloを](../../native-client-odbc-api/sqlclosecursor.md)呼び出すか、 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)を呼び出します。 部分的に処理された結果セットを完成させ、別の結果セットが存在するかどうかをテストするには、 [Sqlmoreresults](../../native-client-odbc-api/sqlmoreresults.md)を呼び出します。 既定の結果セットが完全に処理される前に ODBC アプリケーションが接続ハンドルに対してコマンドを試行した場合は SQL_ERROR が生成され、 **SQLGetDiagRec**を呼び出すとが返されます。  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>参照  
 [カーソルの実装方法](how-cursors-are-implemented.md)  
  
  
