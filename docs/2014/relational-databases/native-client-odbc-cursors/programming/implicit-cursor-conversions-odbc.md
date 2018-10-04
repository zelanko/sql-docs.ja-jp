---
title: 暗黙のカーソル変換 (ODBC) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 300ce02538a59ef043424d866ad4ce49267fcfa4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145266"
---
# <a name="implicit-cursor-conversions-odbc"></a>暗黙のカーソル変換 (ODBC)
  アプリケーションでのカーソルの種類を要求できます。 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 、要求された型のサーバー カーソルでサポートされていない SQL ステートメントを実行します。 呼び出し**SQLExecute**または**SQLExecDirect** sql_success_with_info と**SQLGetDiagRec**を返します。  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 カーソルの種類は、呼び出すことによって使用されているようになりましたが、アプリケーションが判断できます**SQLGetStmtOption** SQL_CURSOR_TYPE を設定します。 カーソルの種類の変換は、1 つのステートメントにのみ適用されます。 次**SQLExecDirect**または**SQLExecute**行われます元のステートメントのカーソル設定を使用します。  
  
## <a name="see-also"></a>参照  
 [カーソル プログラミングの詳細&#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
