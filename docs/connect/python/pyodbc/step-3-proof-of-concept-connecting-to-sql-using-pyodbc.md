---
title: 'ステップ 3: pyodbc を使用した SQL への接続を概念実証する | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3fa70619208df8940ec10a1b5a0f46704ce9c43
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979978"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>ステップ 3: pyodbc を使用した SQL への接続を概念実証する

この例は、のみの概念実証を検討してください。  サンプル コードがわかりやすくするために、簡略化し、Microsoft によって推奨されるベスト プラクティスに表すとは限りません。  

**次のサンプル スクリプトを実行**である test.py という名前のファイルを作成し、移動すると、各コード スニペットを追加します。 

```
> python test.py
```
  
## <a name="step-1--connect"></a>手順 1: 接続  
  
```python

import pyodbc 
# Some other example server values are
# server = 'localhost\sqlexpress' # for a named instance
# server = 'myserver,port' # to specify an alternate port
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()

```  
  
  
## <a name="step-2--execute-query"></a>手順 2: クエリを実行します。  
  
SQL Database に対するクエリのセットの結果を取得する、cursor.executefunction を使用できます。 この関数は、基本的に任意のクエリを受け入れるし、cursor.fetchone() の使用に反復処理できる結果セットを返します
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>手順 3: 行を挿入します。  
  
実行する方法がわかります。 この例では、[挿入](../../../t-sql/statements/insert-transact-sql.md)ステートメントが安全に、からアプリケーションを保護するパラメーターを渡す[SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)値。    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>次の手順  
  
詳細については、次を参照してください。、 [Python デベロッパー センター](https://azure.microsoft.com/develop/python/)します。
