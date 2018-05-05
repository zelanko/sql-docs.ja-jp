---
title: '手順 3: 概念実証の ADO.NET を使用して SQL への接続 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado-net
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aebe3dc6-3ee4-4d11-8e43-5d32b3f91490
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f75fdbb497fc596f572f6e91684a528f344b0c26
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-adonet"></a>手順 3: 概念実証の ADO.NET を使用して SQL に接続します。

- 前の記事:&nbsp;&nbsp;&nbsp;[手順 2: ADO.NET の開発用の SQL データベースの作成](step-2-create-a-sql-database-for-ado-net-development.md)  
- 次の記事:&nbsp;&nbsp;&nbsp;[手順 4: ADO.NET を使用した SQL に弾性的に接続](step-4-connect-resiliently-to-sql-with-ado-net.md)  

  
この c# コード例は、概念実証ののみを考慮してください。 サンプル コードでは、わかりやすくするため、簡略化し、Microsoft によって推奨されるベスト プラクティスを必ずしもは表しません。  
  
## <a name="step-1-connect"></a>手順 1: 接続
  
メソッド**SqlConnection.Open**は、SQL データベースへの接続に使用します。  


```CSharp  
    // C# , ADO.NET  
    using System;
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
  
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    Press any key to finish...  
    ****/  
```  


## <a name="step-2--execute-a-query"></a>手順 2: クエリを実行します。  
  
SqlCommand.ExecuteReader メソッド:  
  
- SQL システムに SQL の SELECT ステートメントを発行します。  
- 結果の行へのアクセスを提供する SqlDataReader のインスタンスを返します。  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using DT = System.Data;            // System.Data.dll  
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.SelectRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void SelectRows(QC.SqlConnection connection)  
            {  
                using (var command = new QC.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = DT.CommandType.Text;  
                    command.CommandText = @"  
    SELECT  
        TOP 5  
            COUNT(soh.SalesOrderID) AS [OrderCount],  
            c.CustomerID,  
            c.CompanyName  
        FROM  
                            SalesLT.Customer         AS c  
            LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh  
                ON c.CustomerID = soh.CustomerID  
        GROUP BY  
            c.CustomerID,  
            c.CompanyName  
        ORDER BY  
            [OrderCount] DESC,  
            c.CompanyName; ";  
      
                    QC.SqlDataReader reader = command.ExecuteReader();  
      
                    while (reader.Read())  
                    {  
                        Console.WriteLine("{0}\t{1}\t{2}",  
                            reader.GetInt32(0),  
                            reader.GetInt32(1),  
                            reader.GetString(2));  
                    }  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    1       29736   Action Bicycle Specialists  
    1       29638   Aerobic Exercise Company  
    1       29546   Bulk Discount Store  
    1       29741   Central Bicycle Specialists  
    1       29612   Channel Outlet  
    Press any key to finish...  
    ****/  
```  
  
  
  
## <a name="step-3-insert-a-row"></a>手順 3: 行を挿入します。  
  
  
この例は、する方法。  
  
- パラメーターを渡すことによって安全に、SQL の INSERT ステートメントを実行します。  
  - パラメーターの使用は、SQL インジェクション攻撃から保護します。  
- 自動生成された値を取得します。  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using DT = System.Data;            // System.Data.dll  
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.InsertRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void InsertRows(QC.SqlConnection connection)  
            {  
                QC.SqlParameter parameter;  
      
                using (var command = new QC.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = DT.CommandType.Text;  
                    command.CommandText = @"  
    INSERT INTO SalesLT.Product  
            (Name,  
            ProductNumber,  
            StandardCost,  
            ListPrice,  
            SellStartDate  
            )  
        OUTPUT  
            INSERTED.ProductID  
        VALUES  
            (@Name,  
            @ProductNumber,  
            @StandardCost,  
            @ListPrice,  
            CURRENT_TIMESTAMP  
            ); ";  
      
                    parameter = new QC.SqlParameter("@Name", DT.SqlDbType.NVarChar, 50);  
                    parameter.Value = "SQL Server Express 2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@ProductNumber", DT.SqlDbType.NVarChar, 25);  
                    parameter.Value = "SQLEXPRESS2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@StandardCost", DT.SqlDbType.Int);  
                    parameter.Value = 11;  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@ListPrice", DT.SqlDbType.Int);  
                    parameter.Value = 12;  
                    command.Parameters.Add(parameter);  
      
                    int productId = (int)command.ExecuteScalar();  
                    Console.WriteLine("The generated ProductID = {0}.", productId);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    The generated ProductID = 1000.  
    Press any key to finish...  
    ****/  
```
