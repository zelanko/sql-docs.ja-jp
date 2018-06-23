---
title: SQL Server の既定の結果セットを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e4b818f3ec580468a3ae1120709ffaa9c19a8ffe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178208"
---
# <a name="using-sql-server-default-result-sets"></a>SQL Server の既定の結果セットの使用
  ODBC カーソルの既定の属性を次に示します。  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 これらの属性は、既定値に設定されるたびに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]既定の結果セットです。 既定の結果セットは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるすべての SQL ステートメントに使用でき、結果セット全体をクライアントに転送する際の最も効率的な方法です。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 複数のアクティブな結果セット (MARS); サポートが追加されましたアプリケーションでは、1 つ以上のアクティブな既定の結果を 1 つの接続設定ができますようになりました。 MARS は既定では有効になっていません。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のリリースでは、既定の結果セットは 1 つの接続における複数のアクティブなステートメントをサポートしていません。 SQL ステートメントが 1 つの接続で実行された後、サーバーは結果セットのすべての行が処理されるまで、その接続に対するクライアントからのコマンドを受け付けません (結果セットの残りの行の処理を取り消す要求は除きます)。 部分的に処理された結果セットの残りの部分をキャンセルする[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)または[SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)で、 *fOption*パラメーターに SQL_CLOSE を設定します。 完了するには、部分的に処理された結果セットと別の結果セットの存在テストを呼び出す[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)です。 呼び出しを呼び出すと、SQL_ERROR が生成されます、ODBC アプリケーションは、既定の結果セットが完全に処理される前に、接続ハンドルでコマンドを試みると、 **SQLGetDiagRec**を返します。  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>参照  
 [カーソルの実装方法](how-cursors-are-implemented.md)  
  
  