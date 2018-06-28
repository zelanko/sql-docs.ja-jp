---
title: '手順 3: pymssql を使用して SQL に接続する概念実証 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: python
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2246ddeb-7c2f-46f3-8a91-cdd718d39b40
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 003fedf9f8a629c39cfeffb8a2b6ac8840496c40
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pymssql"></a>手順 3: 概念実証の pymssql を使用して SQL に接続します。
[!INCLUDE[Driver_Python_Download](../../../includes/driver_python_download.md)]

この例は、概念実証としてのみ考慮してください。 サンプル コードは、わかり易いよう簡略化されており、必ずしも Microsoft が推奨するベスト プラクティスを表しているとは限りません。

## <a name="step-1--connect"></a>手順 1: 接続  
  
[Pymssql.connect](http://pymssql.org/en/latest/ref/pymssql.html)関数は SQL データベースへの接続に使用します。  
  
```python
    import pymssql  
    conn = pymssql.connect(server='yourserver.database.windows.net', user='yourusername@yourserver', password='yourpassword', database='AdventureWorks')  
```  
  
  
## <a name="step-2--execute-query"></a>手順 2: クエリを実行します。  
  
[Cursor.execute](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.execute)関数を使用して SQL データベースに対するクエリからセットの結果を取得することができます。 この関数は、本質的に任意のクエリを受け入れ、[cursor.fetchone()](http://pymssql.org/en/latest/ref/pymssql.html#pymssql.Cursor.fetchone) を使用して反復処理できる結果セットを返します。
  
  
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
  
この例では、[SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md) を防ぐようにパラメーターを渡しながら、安全に [INSERT](../../../t-sql/statements/insert-transact-sql.md) ステートメントを実行する方法を示しています。

  
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
* ロールバック、トランザクション挿入を元に戻す  
  
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
  
詳細については [Python デベロッパー センター](https://azure.microsoft.com/en-us/develop/python/) を参照してください。
