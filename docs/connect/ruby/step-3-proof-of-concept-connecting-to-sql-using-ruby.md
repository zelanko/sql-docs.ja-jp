---
title: "手順 3: 概念実証の Ruby を使用して SQL への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 445782c1958ee5344f64b365dd81725c5ac8e6f6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>手順 3: 概念実証の Ruby を使用して SQL に接続します。

この例は、概念実証ののみを考慮してください。  サンプル コードでは、わかりやすくするため、簡略化し、Microsoft によって推奨されるベスト プラクティスを必ずしもは表しません。  
  
## <a name="step-1--connect"></a>手順 1: 接続  
  
[TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds)関数は SQL データベースへの接続に使用します。  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>手順 2: クエリを実行します。  
  
コピーし、空のファイルを次のコードを貼り付けます。 Test.rb 呼び出します。 コマンド プロンプトから次のコマンドを入力して実行します。  
  
    ruby test.rb  
  
コード サンプルでは、 [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds)関数を使用して、SQL データベースに対するクエリからセットの結果を取得します。 この関数では、クエリを受け取り、結果セットを返します。 結果セットがキーを使用して場所を空ける反復処理される[result.each しないで | 行 |](https://github.com/rails-sqlserver/tiny_tds)です。  
  
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
  
この例を実行する方法が表示されます、[挿入](../../t-sql/statements/insert-transact-sql.md)ステートメントは、安全にからアプリケーションを保護するためのパラメーターを渡す[SQL インジェクション](../../relational-databases/tables/primary-and-foreign-key-constraints.md)値。    
  
TinyTDS を Azure で使用することをお勧めのいくつかを実行すること`SET`ステートメントを現在のセッションが特定の情報を処理する方法を変更します。 推奨`SET`ステートメントは、コード サンプルに用意されています。 たとえば、`SET ANSI_NULL_DFLT_ON`新しい列が列の null 値の許容状態が明示的に記されていない場合でも、null 値を許可するために作成できるようになります。  
  
Microsoft SQL Server に合うように[datetime](http://msdn.microsoft.com/library/ms187819.aspx)を使用して、書式設定、 [strftime](http://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime)関数に対応する datetime 形式にキャストします。  
  
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

