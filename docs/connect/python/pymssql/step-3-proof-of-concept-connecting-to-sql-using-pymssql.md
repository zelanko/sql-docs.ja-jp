---
title: 'ステップ 3: pymssql を使用した SQL への接続を概念実証する | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81042ababad2b8ec7107a4413dfd6e3dcecafb8c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764060"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>ステップ 3: pymssql を使用した SQL への接続を概念実証する
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

この例は、のみの概念実証を検討してください。  サンプル コードがわかりやすくするために、簡略化し、Microsoft によって推奨されるベスト プラクティスに表すとは限りません。  
  
## <a name="step-1--connect"></a>手順 1: 接続  
  
[Pymssql.connect](http://pymssql.org/en/latest/ref/pymssql.html)関数を使用して、SQL Database に接続します。  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>手順 2: クエリを実行します。  
  
[Cursor.execute](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute) SQL Database に対するクエリのセットの結果を取得する関数を使用できます。 この関数は、基本的に任意のクエリを受け入れるし、使用して反復処理できる結果セットを返します[cursor.fetchone()](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone)します。  
  
  
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
  
## <a name="step-3--insert-a-row"></a>手順 3: 行を挿入します。  
  
実行する方法がわかります。 この例では、[挿入](../../../t-sql/statements/insert-transact-sql.md)ステートメントが安全に、からアプリケーションを保護するパラメーターを渡す[SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)値。    
  
  
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
  
## <a name="step-4--rollback-a-transaction"></a>手順 4: トランザクションをロールバックします。  
  
このコード例でトランザクションを使用します。  
  
* トランザクションを開始します。  
* データの行を挿入します。  
* ロールバック、トランザクションの挿入を元に戻す  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
    cursor = conn.cursor()  
    cursor.execute("BEGIN TRANSACTION")  
    cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, CURRENT_TIMESTAMP)")  
    conn.rollback()  
    conn.close()
```  
    
  ## <a name="next-steps"></a>次の手順  
  
詳細については、次を参照してください。、 [Python デベロッパー センター](https://azure.microsoft.com/develop/python/)します。
