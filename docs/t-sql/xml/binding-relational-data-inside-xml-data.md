---
title: "XML データ内部のリレーショナル データをバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- relational data binding [SQL Server]
- XML [SQL Server], binding relational data
- xml data type [SQL Server], relational data binding
- binding relational data [XML in SQL Server]
- variables [XML in SQL Server], relational data binding
- columns [XML in SQL Server], relational data binding
ms.assetid: 03d013a9-b53f-46c3-9628-da77f099c74a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87dca9b5bcd70335a6121b1be1e49f4cc352826e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="binding-relational-data-inside-xml-data"></a>XML データ内部のリレーショナル データのバインド
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定できます[xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)に対して、 **xml**データ型の変数または列。 たとえば、[クエリ &#40; #41メソッド &#40;xml データ型&#41;](../../t-sql/xml/query-method-xml-data-type.md) XML インスタンスに対して指定した XQuery を実行します。 この方法で XML を構築するときに、XML 以外の型の列の値や Transact-SQL 変数を使用することもできます。 この処理を、XML 内部のリレーショナル データのバインドと呼びます。  
  
 XML 内部の XML 以外のリレーショナル データをバインドするために、SQL Server データベース エンジンには次の擬似関数が用意されています。  
  
-   [sql:column &#40; &#41;関数と #40 です。XQuery と #41 です。](../../xquery/xquery-extension-functions-sql-column.md) XQuery 式または XML DML 式で、リレーショナル列の値を使用することができます。  
  
-   [sql:variable &#40; &#41;関数と #40 です。XQuery と #41 です。](../../xquery/xquery-extension-functions-sql-variable.md) . この関数を使用すると、SQL 変数の値を XQuery 式または XML DML 式で使用できます。  
  
 これらの関数を使用する**xml** XML 内部のリレーショナル値を公開するたびにデータ型のメソッドです。  
  
 これらの関数を使用しての列や変数のデータを参照することはできません、 **xml**、CLR ユーザー定義型、datetime、smalldatetime、**テキスト**、 **ntext**、 **sql_variant**、および**イメージ**型です。  
  
 また、このバインドは読み取り専用です。 つまり、これらの関数を使用する列には、データを書き込めません。 For example, sql:variable("@x")="*some expression"* is not allowed.  
  
## <a name="example-cross-domain-query-using-sqlvariable"></a>例 : sql:variable() を使用した複数の領域にまたがるクエリ  
 この例ではどのように**sql:variable()**クエリをパラメーター化するアプリケーションを有効にすることができます。 Isbn を保存が SQL 変数を使用して渡された@isbnです。 使用して、定数に置き換えることで**sql:variable()**クエリは、どの ISBN でも、ISBN が 0-7356-1588-2、1 つだけでなくの検索に使用することができます。  
  
```  
DECLARE @isbn varchar(20)  
SET     @isbn = '0-7356-1588-2'  
SELECT  xCol  
FROM    T  
WHERE   xCol.exist ('/book/@ISBN[. = sql:variable("@isbn")]') = 1  
```  
  
 **sql:column()**同様の方法で使用でき、その他のメリットを提供します。 コストベースのクエリ オプティマイザーの判断により、効率を上げるために列のインデックスが使用される場合があります。 また、昇格したプロパティが計算列に保存される場合があります。  
  
## <a name="see-also"></a>参照  
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)  
  
  
