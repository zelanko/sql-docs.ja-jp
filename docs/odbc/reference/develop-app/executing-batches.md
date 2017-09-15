---
title: "バッチを実行して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b3235040d910f2dd9b5bdbf4a81765d25dcd8be1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executing-batches"></a>バッチの実行
アプリケーションでは、ステートメントのバッチを実行する前に、サポートされているかどうかをまずチェックする必要があります。 これには、アプリケーションの呼び出しを行う**SQLGetInfo** SQL_BATCH_SUPPORT、SQL_PARAM_ARRAY_ROW_COUNTS と SQL_PARAM_ARRAY_SELECTS オプションを使用します。 最初のオプションでは、行のカウント – 生成および – セットを生成するステートメントが明示的なバッチおよび後者 2 つのオプションの戻り値の行の数と結果の可用性に関する情報を設定中に、プロシージャでサポートされる結果がパラメーター化するかどうかが返されます。実行します。  
  
 ステートメントのバッチが実行される**SQLExecute**または**SQLExecDirect**です。 たとえば、次の呼び出しは、明示的なバッチ内のステートメントを開くには、新しい販売注文を実行します。  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 バッチの結果を生成するときにステートメントが実行される、1 つを返しますまたは行数、あるいは結果の詳細を設定します。 これらを取得する方法については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 ステートメントのバッチには、パラメーター マーカーが含まれている場合、これらは、他のステートメントではそのパラメーターの順序を増やすことに番号付けします。 たとえば、ステートメントの次のバッチが 1 ~ 21 です。 番号付きのパラメーター最初の**挿入**ステートメントには、番号付き 1 ~ 5 および、最後にその**挿入**ステートメントは、番号が 18 21 ~ です。  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 パラメーターの詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)、このセクションで後述します。
