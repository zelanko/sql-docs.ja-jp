---
title: バッチの実行 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ce0c043fcfad41a624ad129a757a047d2c87fb6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305733"
---
# <a name="executing-batches"></a>バッチの実行
アプリケーションは、ステートメントのバッチを実行する前に、まず、それらがサポートされているかどうかを確認する必要があります。 これを行うには、アプリケーションは、SQL_BATCH_SUPPORT、SQL_PARAM_ARRAY_ROW_COUNTS、およびSQL_PARAM_ARRAY_SELECTSオプションを使用して**SQLGetInfo**を呼び出します。 最初のオプションは、行数生成ステートメントと結果セット生成ステートメントが明示的なバッチおよびプロシージャでサポートされているかどうかを返し、後者の 2 つのオプションは、パラメータ化された実行で行数と結果セットの可用性に関する情報を返します。  
  
 ステートメントのバッチは **、 SQL 実行または** **SQLExecDirect を**介して実行されます。 たとえば、次の呼び出しは、新しい販売注文を開くステートメントの明示的なバッチを実行します。  
  
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
  
 結果生成ステートメントのバッチが実行されると、1 つ以上の行カウントまたは結果セットが返されます。 これらを取得する方法については、「[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)」を参照してください。  
  
 ステートメントのバッチにパラメーター・マーカーが含まれている場合、これらは他のステートメントと同じように、パラメーターの昇順で番号が付けられます。 たとえば、次のバッチのステートメントには、1 から 21 までの番号が付いたパラメーターがあります。最初の**INSERT**ステートメントの番号は 1 から 5、最後の**INSERT**ステートメントの番号は 18 から 21 です。  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 パラメーターの詳細については、このセクションの後の[「ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。
