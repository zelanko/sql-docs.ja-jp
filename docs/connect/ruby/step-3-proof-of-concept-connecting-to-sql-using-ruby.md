---
title: 'ステップ 3: Java を使用した SQL への接続を概念実証する | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eed37349152b48ab49859b44cc23cb463d8541b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801380"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>ステップ 3: Ruby を使用した SQL への接続を概念実証する

この例は、のみの概念実証を検討してください。  サンプル コードがわかりやすくするために、簡略化し、Microsoft によって推奨されるベスト プラクティスに表すとは限りません。  
  
## <a name="step-1--connect"></a>手順 1: 接続  
  
[Tinytds::client](https://github.com/rails-sqlserver/tiny_tds)関数を使用して、SQL Database に接続します。  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>手順 2: クエリの実行  
  
コピーして空のファイルで、次のコードを貼り付けます。 Test.rb という名前です。 コマンド プロンプトから次のコマンドを入力して実行します。  
  
    ruby test.rb  
  
コード サンプルで、 [tinytds::result](https://github.com/rails-sqlserver/tiny_tds)関数を使用して、SQL Database に対するクエリのセットの結果を取得します。 この関数は、クエリを受け取り、結果セットを返します。 結果セットが反復処理を使用して[result.each しないで | 行 |](https://github.com/rails-sqlserver/tiny_tds)します。  
  
``` ruby 
    require 'tiny_tds'    
    print 'test'       
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC")  
    results.each do |row|  
    puts row  
    end  
```  
  
## <a name="step-3--insert-a-row"></a>手順 3: 行を挿入します。  
  
実行する方法がわかります。 この例では、[挿入](../../t-sql/statements/insert-transact-sql.md)ステートメントが安全に、からアプリケーションを保護するパラメーターを渡す[SQL インジェクション](../../relational-databases/tables/primary-and-foreign-key-constraints.md)値。    
  
Azure で TinyTDS を使用することをお勧めのいくつかを実行すること`SET`を現在のセッションが特定の情報を処理する方法を変更するステートメント。 推奨`SET`ステートメントは、コード サンプルで提供されます。 たとえば、`SET ANSI_NULL_DFLT_ON`新しい列が列の null 値許容ステータスを明示的に宣言されていない場合でも、null 値を許可するために作成できるようになります。  
  
Microsoft SQL Server とを連携させる[datetime](../../t-sql/data-types/datetime-transact-sql.md)を使用して、書式設定、 [strftime](http://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime)対応する datetime 形式にキャストする関数。  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SET ANSI_NULLS ON")  
    results = client.execute("SET CURSOR_CLOSE_ON_COMMIT OFF")  
    results = client.execute("SET ANSI_NULL_DFLT_ON ON")  
    results = client.execute("SET IMPLICIT_TRANSACTIONS OFF")  
    results = client.execute("SET ANSI_PADDING ON")  
    results = client.execute("SET QUOTED_IDENTIFIER ON")  
    results = client.execute("SET ANSI_WARNINGS ON")  
    results = client.execute("SET CONCAT_NULL_YIELDS_NULL ON")  
    require 'date'  
    t = Time.now  
    curr_date = t.strftime("%Y-%m-%d %H:%M:%S.%L")  
    results = client.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate)  
    OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, '#{curr_date}' )")  
    results.each do |row|  
    puts row  
    end  
```
