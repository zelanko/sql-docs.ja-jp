---
title: 暗黙のカーソル変換 (ODBC) |Microsoft ドキュメント
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
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b1f1880ea464949bd962bab002d1f1129261463c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077308"
---
# <a name="implicit-cursor-conversions-odbc"></a>暗黙のカーソル変換 (ODBC)
  アプリケーションがを介してカーソルの種類を要求できます。 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 、要求された種類のサーバー カーソルでサポートされていない SQL ステートメントを実行します。 呼び出し**SQLExecute**または**SQLExecDirect** sql_success_with_info が返されますと**SQLGetDiagRec**を返します。  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 アプリケーションでは、呼び出すことによってカーソルの種類を使用していますを判断できます**SQLGetStmtOption** SQL_CURSOR_TYPE を設定します。 カーソルの種類の変換は、1 つのステートメントにのみ適用されます。 次へ**SQLExecDirect**または**SQLExecute**は実行元のステートメントのカーソル設定を使用します。  
  
## <a name="see-also"></a>参照  
 [カーソル プログラミングの詳細&#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  