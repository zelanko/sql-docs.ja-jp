---
title: 手順 3:pyodbc を使用した SQL への接続を概念実証する | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e241d84ebc60acceafe09b1a9240711a72d2067
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "72798318"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>手順 3:pyodbc を使用した SQL への接続を概念実証する

この例は概念実証としてのみ検討してください。  わかりやすさのためにサンプル コードは簡略化されており、Microsoft が推奨するベスト プラクティスを表しているとは限りません。  

**次のサンプル スクリプトを実行します。** test.py という名前のファイルを作成し、各コード スニペットを追加していきます。 

```
> python test.py
```
  
## <a name="step-1--connect"></a>手順 1:接続する  
  
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
  
  
## <a name="step-2--execute-query"></a>手順 2:クエリの実行  
  
Cursor.execute 関数は、SQL Database に対するクエリから結果セットを取得するために使用できます。 この関数は基本的に任意のクエリを受け取り、cursor.fetchone() を使用して反復処理できる結果セットを返します。
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print(row[0])
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>手順 3:行を挿入する  
  
この例では、[INSERT](../../../t-sql/statements/insert-transact-sql.md) ステートメントを安全に実行し、[SQL インジェクション](../../../relational-databases/tables/primary-and-foreign-key-constraints.md)の値からアプリケーションを保護するパラメーターを渡す方法を確認します。    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
cnxn.commit()
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  

## <a name="azure-active-directory-aad-and-the-connection-string"></a>Azure Active Directory (AAD) と接続文字列

pyODBC では、Microsoft ODBC Driver for SQL Server が使用されます。
ODBC ドライバーのバージョンが 17.1 以降の場合は、pyODBC を通じて AAD 対話型モードの ODBC ドライバーを使用できます。
この AAD 対話型オプションは、Python と pyODBC によって ODBC ドライバーでのダイアログのポップアップ表示が許可されている場合に機能します。
このオプションは、Windows オペレーティング システムでのみ使用できます。

### <a name="example-connection-string-for-aad-interactive-authentication"></a>AAD 対話型認証の接続文字列の例

AAD 対話型認証を指定する ODBC 接続文字列の例を次に示します。

- `server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

ODBC ドライバーの AAD 認証オプションの詳細については、次の記事を参照してください。

- [ODBC ドライバーでの Azure Active Directory の使用](../../odbc/using-azure-active-directory.md#new-andor-modified-dsn-and-connection-string-keywords)

## <a name="next-steps"></a>次のステップ
  
詳細については、 [Python デベロッパー センター](https://azure.microsoft.com/develop/python/)を参照してください。
