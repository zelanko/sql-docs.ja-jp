---
title: 手順 3:pymssql を使用して SQL に接続する
description: 手順 3 は概念実証であり、Python と pymssql を使用して SQL Server に接続する方法がわかります。 基本的な例で、データの選択と挿入が示されます。
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1c75d13e9e44632c411639385227776f54ca1a9
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528566"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>手順 3:pymssql を使用した SQL への接続を概念実証する
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

この例は概念実証としてのみ検討してください。  わかりやすさのためにサンプル コードは簡略化されており、Microsoft が推奨するベスト プラクティスを表しているとは限りません。  
  
## <a name="step-1--connect"></a>手順 1:接続する  
  
[pymssql.connect](https://pypi.org/project/pymssql/) 関数は、SQL Database に接続するために使用します。  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>手順 2:クエリの実行  
  
[Cursor.execute](https://pypi.org/project/pymssql/) 関数は、SQL Database に対するクエリから結果セットを取得するために使用できます。 この関数は基本的に任意のクエリを受け取り、[cursor.fetchone()](https://pypi.org/project/pymssql/) を使用して反復処理できる結果セットを返します。  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute('SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC;')  
    row = cursor.fetchone()  
    while row:  
        print str(row[0]) + " " + str(row[1]) + " " + str(row[2])     
        row = cursor.fetchone()  
```  
  
## <a name="step-3--insert-a-row"></a>手順 3:行を挿入する  
  
この例では、[INSERT](../../../t-sql/statements/insert-transact-sql.md) ステートメントを安全に実行し、パラメーターを渡す方法について説明します。 パラメーターを値として渡すと、アプリケーションは [SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)から保護されます。  
  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express', 'SQLEXPRESS', 0, 0, CURRENT_TIMESTAMP)")  
    row = cursor.fetchone()  
    while row:  
        print "Inserted Product ID : " +str(row[0])  
        row = cursor.fetchone()  
    conn.commit()
    conn.close()
```  
  
## <a name="step-4-roll-back-a-transaction"></a>手順 4:トランザクションをロールバックする  
  
このコード例は、以下のトランザクションの使用について示します。  
  
* トランザクションの開始  
* データの挿入  
* トランザクションをロールバックして、挿入を元に戻す  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>次のステップ  
  
詳細については、 [Python デベロッパー センター](https://azure.microsoft.com/develop/python/)を参照してください。
