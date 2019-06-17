---
title: 'ステップ 3: pyodbc を使用した SQL への接続を概念実証する | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e8f4c34c1b6b945c28193a549a06546ec952a5d9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780372"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>ステップ 3: pyodbc を使用した SQL への接続を概念実証する

この例は概念実証としてのみ検討してください。  わかりやすさのためにサンプル コードは簡略化されており、Microsoft が推奨するベスト プラクティスを表しているとは限りません。  

**次のサンプル スクリプトを実行**である test.py という名前のファイルを作成し、移動すると、各コード スニペットを追加します。 

```
> python test.py
```
  
## <a name="step-1--connect"></a>手順 1: 接続する  
  
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
  
## <a name="step-3--insert-a-row"></a>手順 3: 行を挿入する  
  
この例では、[INSERT](../../../t-sql/statements/insert-transact-sql.md) ステートメントを安全に実行し、[SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)の値からアプリケーションを保護するパラメーターを渡す方法を確認します。    
  
  
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
