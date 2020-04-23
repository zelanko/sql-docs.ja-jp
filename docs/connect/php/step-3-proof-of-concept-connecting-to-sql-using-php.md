---
title: 手順 3:PHP を使用して SQL に接続する
description: 手順 3 は概念実証であり、PHP を使用して SQL Server に接続する方法がわかります。 基本的な例で、データの選択と挿入が示されます。
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a7451a85-18e5-4fd0-bbcb-2f15a1117290
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69c8b1ec58dbb40ab6e4463d343720e02e583ac8
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528586"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-php"></a>手順 3:PHP を使用した SQL への接続を概念実証する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="step-1--connect"></a>手順 1:接続する  
  
  
**OpenConnection** 関数は、後に続くすべての関数の上部近くで呼び出されます。  
  
  
```php 
    function OpenConnection()  
    {  
        try  
        {  
            $serverName = "tcp:myserver.database.windows.net,1433";  
            $connectionOptions = array("Database"=>"AdventureWorks",  
                "Uid"=>"MyUser", "PWD"=>"MyPassword");  
            $conn = sqlsrv_connect($serverName, $connectionOptions);  
            if($conn == false)  
                die(FormatErrors(sqlsrv_errors()));  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-2--execute-query"></a>手順 2:クエリの実行  
  
[sqlsrv_query()](https://php.net/manual/en/function.sqlsrv-query.php) 関数は、SQL Database に対するクエリから結果セットを取得するために使用できます。 この関数では基本的に任意のクエリと接続オブジェクトを受け入れ、[sqlsrv_fetch_array()](https://php.net/manual/en/function.sqlsrv-fetch-array.php) を使用して反復処理できる結果セットを返します。  
  
```php  
    function ReadData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
            $tsql = "SELECT [CompanyName] FROM SalesLT.Customer";  
            $getProducts = sqlsrv_query($conn, $tsql);  
            if ($getProducts == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
            $productCount = 0;  
            while($row = sqlsrv_fetch_array($getProducts, SQLSRV_FETCH_ASSOC))  
            {  
                echo($row['CompanyName']);  
                echo("<br/>");  
                $productCount++;  
            }  
            sqlsrv_free_stmt($getProducts);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
  
## <a name="step-3--insert-a-row"></a>手順 3:行を挿入する  
  
この例では、[INSERT](../../t-sql/statements/insert-transact-sql.md) ステートメントを安全に実行し、パラメーターを渡す方法について説明します。 パラメーター値により、アプリケーションは [SQL インジェクション](../../relational-databases/tables/primary-and-foreign-key-constraints.md)から保護されます。
  
```php 
    function InsertData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            $tsql = "INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT            INSERTED.ProductID VALUES ('SQL Server 1', 'SQL Server 2', 0, 0, getdate())";  
            //Insert query  
            $insertReview = sqlsrv_query($conn, $tsql);  
            if($insertReview == FALSE)  
                die(FormatErrors( sqlsrv_errors()));  
            echo "Product Key inserted is :";  
            while($row = sqlsrv_fetch_array($insertReview, SQLSRV_FETCH_ASSOC))  
            {     
                echo($row['ProductID']);  
            }  
            sqlsrv_free_stmt($insertReview);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-4--roll-back-a-transaction"></a>手順 4:トランザクションをロールバックする  
  
  
このコード例は、以下のトランザクションの使用について示します。  
  
\- トランザクションの開始  
  
\- データ行の挿入、別のデータ行の更新  
  
\- 挿入と更新が正常に完了した場合はトランザクションをコミットし、それらのいずれかがなかった場合はそのトランザクションをロールバックする  
  
  
```php 
    function Transactions()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            if (sqlsrv_begin_transaction($conn) == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
  
            $tsql1 = "INSERT INTO SalesLT.SalesOrderDetail (SalesOrderID,OrderQty,ProductID,UnitPrice)  
            VALUES (71774, 22, 709, 33)";  
            $stmt1 = sqlsrv_query($conn, $tsql1);  
  
            /* Set up and execute the second query. */  
            $tsql2 = "UPDATE SalesLT.SalesOrderDetail SET OrderQty = (OrderQty + 1) WHERE ProductID = 709";  
            $stmt2 = sqlsrv_query( $conn, $tsql2);  
  
            /* If both queries were successful, commit the transaction. */  
            /* Otherwise, rollback the transaction. */  
            if($stmt1 && $stmt2)  
            {  
                   sqlsrv_commit($conn);  
                   echo("Transaction was commited");  
            }  
            else  
            {  
                sqlsrv_rollback($conn);  
                echo "Transaction was rolled back.\n";  
            }  
            /* Free statement and connection resources. */  
            sqlsrv_free_stmt( $stmt1);  
            sqlsrv_free_stmt( $stmt2);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="additional-examples"></a>その他の例  
  
[サンプル アプリケーション (SQLSRV ドライバー)](../../connect/php/example-application-sqlsrv-driver.md)  

[サンプル アプリケーション (PDO_SQLSRV ドライバー)](../../connect/php/example-application-pdo-sqlsrv-driver.md)
