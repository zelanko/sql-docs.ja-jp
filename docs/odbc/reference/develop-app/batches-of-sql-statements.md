---
title: SQL ステートメントのバッチ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d68ea1c13655ca7c57ba076823f461a4b2e22055
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283512"
---
# <a name="batches-of-sql-statements"></a>SQL ステートメントのバッチ
SQL ステートメントのバッチは、2 つ以上の SQL ステートメントまたは 2 つ以上の SQL ステートメントのグループと同じ効果を持つ単一の SQL ステートメントのグループです。 一部の実装では、バッチ ステートメント全体が実行されてから、結果が得られる場合があります。 多くの場合、この方法は、ネットワーク トラフィックが削減され、データ ソースが SQL ステートメントのバッチの実行を最適化できるため、ステートメントを個別に送信するよりも効率的です。 他の実装では **、SQLMoreResults**を呼び出すと、バッチ内の次のステートメントの実行がトリガーされます。 ODBC では、次の種類のバッチがサポートされます。  
  
-   **明示的なバッチ***明示的バッチ*は、セミコロン (;) で区切られた 2 つ以上の SQL ステートメントです。 たとえば、次のバッチの SQL ステートメントは、新しい販売注文を開きます。 これには、"受注" テーブルと "明細行" テーブルの両方に行を挿入する必要があります。 最後のステートメントの後にセミコロンが存在しない点に注意してください。  
  
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
  
-   **手順**プロシージャーに複数の SQL ステートメントが含まれている場合は、そのプロシージャーは SQL ステートメントのバッチと見なされます。 たとえば、次の SQL Server 固有のステートメントは、顧客に関する情報を含む結果セットを返すプロシージャを作成し、その顧客に対してオープンしているすべての販売注文を一覧表示する結果セットを返します。  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     **CREATE PROCEDURE**ステートメント自体は、SQL ステートメントのバッチではありません。 ただし、作成するプロシージャは SQL ステートメントのバッチです。 CREATE PROCEDURE**ステートメントは**SQL Server に固有であり、SQL Server では CREATE **PROCEDURE**ステートメントで複数のステートメントを区切るためにセミコロン**CREATE PROCEDURE**は必要ありません。  
  
-   **パラメータの配列**パラメータの配列は、一括操作を実行する効果的な方法として、パラメータ化された SQL ステートメントと共に使用できます。 たとえば、次の**INSERT**ステートメントとパラメータの配列を使用すると、1 つの SQL ステートメントだけを実行しながら、Lines テーブルに複数の行を挿入できます。  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     データ ソースがパラメーターの配列をサポートしていない場合、ドライバーは、パラメーターのセットごとに 1 回 SQL ステートメントを実行することによって、パラメーターをエミュレートできます。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)と[パラメータ値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)」を参照してください。  
  
 異なる種類のバッチを相互運用可能な方法で混在することはできません。 つまり、プロシージャ呼び出しを含む明示的なバッチを実行した結果、パラメーターの配列を使用する明示的なバッチ、およびパラメーターの配列を使用するプロシージャ呼び出しは、アプリケーションがドライバー固有です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果生成および結果解放ステートメント](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [バッチの実行](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [エラーおよびバッチ](../../../odbc/reference/develop-app/errors-and-batches.md)
