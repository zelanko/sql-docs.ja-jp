---
title: '手順 3: pyodbc を使用して SQL に接続する概念実証 |Microsoft ドキュメント'
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
ms.openlocfilehash: 9914b8bd941eb3e6ddc64fb1a4e37b38335fa01f
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309751"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>手順 3: 概念実証の pyodbc を使用して SQL に接続します。

この例は、概念実証ののみを考慮してください。  サンプル コードでは、わかりやすくするため、簡略化し、Microsoft によって推奨されるベスト プラクティスを必ずしもは表しません。  

**次のサンプル スクリプトを実行**test.py と呼ばれるファイルを作成しを進めながら、各コード スニペットを追加します。 

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
  
SQL データベースに対するクエリからセットの結果を取得する、cursor.executefunction を使用できます。 この関数は本質的には任意のクエリを受け入れるし、反復処理できる cursor.fetchone() の使用に結果セットを返します
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>手順 3: 行を挿入します。  
  
この例を実行する方法が表示されます、[挿入](../../../t-sql/statements/insert-transact-sql.md)ステートメントは、安全にからアプリケーションを保護するためのパラメーターを渡す[SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)値。    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>次のステップ  
  
詳細については、次を参照してください。、 [Python デベロッパー センター](https://azure.microsoft.com/en-us/develop/python/)です。
