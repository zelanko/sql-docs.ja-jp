---
title: "SQL Server およびクライアント アプリでの FOR JSON 出力の使用 (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, using in client apps
- FOR JSON, using in SQL Server
ms.assetid: 302e5397-b499-4ea3-9a7f-c24ccad698eb
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5331ff00081a7b79756ef14e771ab4a22d3e35ac
ms.lasthandoff: 04/11/2017

---
# <a name="use-for-json-output-in-sql-server-and-in-client-apps-sql-server"></a>SQL Server およびクライアント アプリでの FOR JSON 出力の使用 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  ここでは、 **またはクライアント アプリで** FOR JSON [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 句またはその出力を使用する方法を例として示します。  
  
## <a name="use-for-json-output-in-sql-server-variables"></a>FOR JSON 出力を SQL Server の変数で使用する  
 FOR JSON 句の出力は NVARCHAR(MAX) 型のため、次の例に示すように、任意の変数に割り当てることができます。  
  
```tsql  
DECLARE @x NVARCHAR(MAX) = (SELECT TOP 10 * FROM Sales.SalesOrderHeader FOR JSON AUTO)  
```  
  
## <a name="use-for-json-output-in-sql-server-user-defined-functions"></a>FOR JSON 出力を SQL Server のユーザー定義関数で使用する  
 結果セットを JSON として書式設定し、この JSON 出力を返すユーザー定義関数を作成することができます。 次の例では、いくつかの販売注文の詳細行を取得してそれを JSON 配列として書式設定するユーザー定義関数を作成しています。  
  
```tsql  
CREATE FUNCTION GetSalesOrderDetails(@salesOrderId int)  
 RETURNS NVARCHAR(MAX)  
AS  
BEGIN  
   RETURN (SELECT UnitPrice, OrderQty  
           FROM Sales.SalesOrderDetail  
           WHERE SalesOrderID = @salesOrderId  
           FOR JSON AUTO)  
END
```  
  
 この関数は、次の例に示すように、バッチまたはクエリで使用することができます。  
  
```tsql  
DECLARE @x NVARCHAR(MAX)=dbo.GetSalesOrderDetails(43659)

PRINT dbo.GetSalesOrderDetails(43659)

SELECT TOP 10
  H.*,dbo.GetSalesOrderDetails(H.SalesOrderId) AS Details
FROM Sales.SalesOrderHeader H
```  
  
## <a name="merge-parent-and-child-data-into-a-single-table"></a>親と子のデータを 1 つのテーブルにマージする  
 次の例では、それぞれの子の行のセットを JSON 配列として書式設定し、親テーブルの Details 列の値に設定しています。  
  
```tsql  
SELECT TOP 10 SalesOrderId, OrderDate,  
      (SELECT TOP 3 UnitPrice, OrderQty  
         FROM Sales.SalesOrderDetail D  
         WHERE H.SalesOrderId = D.SalesOrderID  
         FOR JSON AUTO) as Details  
INTO SalesOrder  
FROM Sales.SalesOrderHeader H  
```  
  
## <a name="update-the-data-in-json-columns"></a>JSON の列のデータを更新する  
 次の例に、JSON テキストを含む列の値を更新する方法を示します。  
  
```tsql  
UPDATE SalesOrder  
SET Details =  
     (SELECT TOP 1 UnitPrice, OrderQty  
       FROM Sales.SalesOrderDetail D  
       WHERE D.SalesOrderId = SalesOrder.SalesOrderId  
      FOR JSON AUTO 
```  
  
## <a name="use-for-json-output-in-a-c-client-app"></a>C# クライアント アプリで FOR JSON 出力を使用する  
 次の例に、クエリの JSON の出力を C# クライアント アプリの StringBuilder オブジェクトに取得する方法を示します。 変数 queryWithForJson には FOR JSON 句を含む SELECT ステートメントのテキストが含まれているものと仮定します。  
  
```csharp  
            var queryWithForJson = "SELECT ... FOR JSON";
            var conn = new SqlConnection("<connection string>");
            var cmd = new SqlCommand(queryWithForJson, conn);
            conn.Open();
            var jsonResult = new StringBuilder();
            var reader = cmd.ExecuteReader();
            if (!reader.HasRows)
            {
                jsonResult.Append("[]");
            }
            else
            {
                while (reader.Read())
                {
                    jsonResult.Append(reader.GetValue(0).ToString());
                }
            }
```  
  
## <a name="see-also"></a>参照  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

