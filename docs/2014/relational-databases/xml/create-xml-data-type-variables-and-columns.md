---
title: XML データ型の変数と列の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 62f1bd69d60fb7a0c919b07a8582d28a08e666e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164735"
---
# <a name="create-xml-data-type-variables-and-columns"></a>XML データ型の変数と列の作成
  `xml`データ型は、組み込みのデータ型で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]などと他の組み込み型に類似したおよび`int`と`varchar`です。 他の組み込み型にも使用できるように、`xml`変数の型、パラメーターの型、関数の戻り値の型、またはテーブルを作成するときに、データ型列の型として[CAST および CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)です。  
  
## <a name="creating-columns-and-variables"></a>列と変数の作成  
 テーブルの一部として `xml` 型の列を作成するには、 `CREATE TABLE` ステートメントを使用します。次に例を示します。  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 `DECLARE statement` を使用して `xml` 型の変数を作成できます。次に例を示します。  
  
```  
DECLARE @x xml   
```  
  
 XML スキーマ コレクションを指定して、型指定された `xml` 変数を作成します。次に例を示します。  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 `xml` 型のパラメーターをストアド プロシージャに渡すには、 `CREATE PROCEDURE` ステートメントを使用します。次に例を示します。  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 XQuery を使用して、列、パラメーター、または変数に格納されている XML インスタンスにクエリを実行できます。 また、XML DML (データ操作言語) を使用して、XML インスタンスに更新を適用することもできます。 開発時点では XQuery 標準に XQuery DML が定められていなかったので、XQuery については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML DML (XML データ変更言語) [拡張機能が](/sql/t-sql/xml/xml-data-modification-language-xml-dml) に実装されています。 この拡張機能を使用して、挿入、更新、および削除を実行できます。  
  
## <a name="assigning-defaults"></a>既定の XML の割り当て  
 テーブル内で、`xml` 型の列に、既定の XML インスタンスを割り当てることができます。 既定の XML を割り当てるには、XML 定数を使用する方法と、`xml` 型への明示的なキャストを使用する方法の 2 つがあります。  
  
 既定の XML を XML 定数として割り当てるには、次の例の構文を使用します。 文字列は暗黙的にキャスト注`xml`型です。  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 既定の XML を `CAST` への明示的な `xml`として割り当てるには、次の例の構文を使用します。  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`xml` 型の列に対する NULL 制約および NOT NULL 制約もサポートされます。 以下に例を示します。  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a>制約の指定  
 `xml` 型の列を作成するときには、列レベルまたはテーブル レベルの制約を定義できます。 制約は、次のような場合に使用してください。  
  
-   ビジネス ルールが XML スキーマでは表現できない場合。 たとえば、花屋の配達可能地域が店舗から 80 km 以内に限られている場合などです。 このルールは XML 列の制約として記述できます。 この制約には、`xml` データ型のメソッドが必要になる場合があります。  
  
-   制約が、テーブル内の他の XML 列または XML 以外の列に関係している場合。 たとえば、XML インスタンスに現れる Customer の ID (`/Customer/@CustId`) が、CustomerID リレーショナル列の値と一致する必要がある場合などです。  
  
 制約は、型指定された `xml` データ型の列にも、型指定されていない  データ型の列にも指定できます。 ただし、制約を指定するとき、[XML データ型のメソッド](/sql/t-sql/xml/xml-data-type-methods) は使用できません。 また、`xml` データ型では次の列およびテーブルの制約はサポートされません。  
  
-   PRIMARY KEY/ FOREIGN KEY  
  
-   UNIQUE  
  
-   COLLATE  
  
     XML では、独自のエンコードが使用されます。 照合順序は、文字列型にのみ適用されます。 `xml` データ型は文字列型ではありません。 ただし、文字列で表記され、文字列データ型との相互のキャストが可能です。  
  
-   RULE  
  
 ラップするラッパー、ユーザー定義関数を作成するのには、制約を使用する代わりに、`xml`データがメソッドを入力し、次の例で示すように、check 制約でユーザー定義関数を指定します。  
  
 次の例では、 `Col2` 列に対して、保存する各 XML インスタンスには `<ProductDescription>` 属性を持つ `ProductID` 要素が必要であるという制約を指定します。 この制約は、次のユーザー定義関数によって適用されます。  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 インスタンスの `exist()` 要素に `xml` 属性が含まれる場合、 `1` データ型の `<ProductDescription>` メソッドは `ProductID` を返します。 それ以外の場合は `0`を返します。  
  
 ここで、次のようにして列レベルの制約を定義したテーブルを作成できます。  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 次の挿入操作は成功します。  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 次の挿入操作は制約に違反するため失敗します。  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a>同じテーブルと別のテーブル  
 `xml`を他のリレーショナル列を含むテーブルまたは別のテーブルと、メインのテーブルに外部キー リレーションシップには、データ型の列を作成することができます。  
  
 作成、`xml`次の条件のいずれかが true の場合は、同じテーブル内のデータ型の列。  
  
-   XML 列のデータを取得するが、その列に XML インデックスは不要な場合。  
  
-   `xml` データ型の列に XML インデックスを作成するときに、メイン テーブルの主キーがクラスター化キーと同一である場合。 詳細については、「[XML インデックス &#40;SQL Server&#41;](xml-indexes-sql-server.md)」をご覧ください。  
  
 作成、`xml`場合は、次の条件に該当する別のテーブルにデータ型の列。  
  
-   XML インデックスを作成する、`xml`メイン テーブルの主キーですが、データ型の列がクラスター化キーと異なるかメイン テーブルには、主キーがありませんかメイン テーブルがヒープ (クラスター化キーがありません)。 メイン テーブルが既に存在する場合、これに該当している可能性があります。  
  
-   テーブルに XML 列が存在することでテーブル スキャンが遅くなるのを避ける場合。 テーブル スキャンは、XML が行内に保存されていても行外に保存されていても領域を消費します。  
  
  
