---
title: "暗黙のカーソル変換 (ODBC) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 451110a16f022cd71f848066685082662d57d1a4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="implicit-cursor-conversions-odbc"></a>暗黙のカーソル変換 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  アプリケーションがを介してカーソルの種類を要求できます。 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) 、要求された種類のサーバー カーソルでサポートされていない SQL ステートメントを実行します。 呼び出し**SQLExecute**または**SQLExecDirect** sql_success_with_info が返されますと**SQLGetDiagRec**を返します。  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 アプリケーションでは、呼び出すことによってカーソルの種類を使用していますを判断できます**SQLGetStmtOption** SQL_CURSOR_TYPE を設定します。 カーソルの種類の変換は、1 つのステートメントにのみ適用されます。 次へ**SQLExecDirect**または**SQLExecute**は実行元のステートメントのカーソル設定を使用します。  
  
## <a name="see-also"></a>参照  
 [カーソル プログラミングの詳細 &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
