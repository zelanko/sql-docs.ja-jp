---
title: SQL ステートメントのバッチ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e7f0119110e1bc57d106163d2e187bf599a0c596
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="batches-of-sql-statements"></a>SQL ステートメントのバッチ
SQL ステートメントのバッチは、2 つ以上の SQL ステートメントまたはを 2 つ以上の SQL ステートメントのグループと同じ効果を持つ単一の SQL ステートメントのグループです。 一部の実装では、すべての結果を利用する前に、バッチ全体のステートメントが実行されます。 これは、多くの場合、複数のネットワーク トラフィックが低下することができ、データ ソースが SQL ステートメントのバッチの実行を最適化できる場合がありますので、個別にステートメントを送信するよりも効率的です。 呼び出し、他の実装で**SQLMoreResults**バッチ内の次のステートメントの実行を開始します。 ODBC には、次の種類のバッチがサポートされています。  
  
-   **明示的なバッチ**、*明示的なバッチ*はセミコロン (;) で区切られた 2 つ以上の SQL ステートメント。 たとえば、SQL ステートメントの次のバッチでは、新しい販売注文が表示されます。 これは、Orders と行の両方のテーブルに行を挿入する必要があります。 最後のステートメントの後にセミコロンがないことに注意してください。  
  
    ```  
    INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
       VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 1, 1234, 10);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 2, 987, 8);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 3, 566, 17);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 4, 412, 500)  
    ```  
  
-   **プロシージャ**場合は、プロシージャには、1 つ以上の SQL ステートメントが含まれている、SQL ステートメントのバッチであると見なされます。 たとえば、次の SQL Server 固有のステートメントでは、顧客とその顧客の開いているすべての販売注文を含む結果セットに関する情報を含む結果セットを返すプロシージャを作成します。  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     **CREATE PROCEDURE**ステートメント自体は、SQL ステートメントのバッチではありません。 ただし、作成手順は、SQL ステートメントのバッチをします。 セミコロンで区切られていない 2 つ**選択**ステートメントのため、 **CREATE PROCEDURE**ステートメントは、SQL Server を特定し、SQL Server には、複数のステートメントをセミコロンは不要**CREATE PROCEDURE**ステートメントです。  
  
-   **パラメーター配列**パラメーターの配列は、一括操作を実行する効果的な方法としてパラメーター化された SQL ステートメントで使用できます。 パラメーターの配列を使用して、次のたとえば、**挿入**行のテーブルに 1 つの SQL ステートメントのみを実行中に複数の行を挿入するステートメント。  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     データ ソースがパラメーターの配列をサポートしていない場合、ドライバーをエミュレートできますそれらのパラメーターのセットごとに、SQL ステートメントを実行しています。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)と[パラメーター値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)、このセクションで後述します。  
  
 相互運用可能な方法でさまざまな種類のバッチを混在させることはできません。 つまり、アプリケーションがプロシージャを含む、明示的なバッチの実行結果を決定する方法を呼び出すと、パラメーターの配列を使用する明示的なバッチおよびパラメーターの配列を使用するプロシージャの呼び出しは、ドライバー固有です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果生成および結果解放ステートメント](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [バッチの実行](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [エラーおよびバッチ](../../../odbc/reference/develop-app/errors-and-batches.md)
