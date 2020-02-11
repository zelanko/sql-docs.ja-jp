---
title: 暗黙のカーソル変換 (ODBC) |Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62711570"
---
# <a name="implicit-cursor-conversions-odbc"></a>暗黙のカーソル変換 (ODBC)
  アプリケーションでは、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を使用してカーソルの種類を要求した後、要求された種類のサーバーカーソルでサポートされていない SQL ステートメントを実行できます。 **Sqlexecute**または**SQLExecDirect**を呼び出すと SQL_SUCCESS_WITH_INFO が返され、 **SQLGetDiagRec**はを返します。  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 アプリケーションでは、SQL_CURSOR_TYPE に設定された**SQLGetStmtOption**を呼び出すことによって現在使用されているカーソルの種類を特定できます。 カーソルの種類の変換は、1 つのステートメントにのみ適用されます。 次の**SQLExecDirect**または**sqlexecute**は、元のステートメントのカーソル設定を使用して実行されます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;のカーソルプログラミングの詳細](cursor-programming-details-odbc.md)  
  
  
