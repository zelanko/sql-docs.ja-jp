---
title: "Xml データ型メソッドの使用に関するガイドライン |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
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
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: 1a483aa1-42de-4c88-a4b8-c518def3d496
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79f10b22ba88d6dd860c608c9468e20a27615650
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="guidelines-for-using-xml-data-type-methods"></a>xml データ型メソッドの使用に関するガイドライン
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックの使用に関するガイドラインを説明します、 **xml**データ型のメソッドです。  
  
## <a name="the-print-statement"></a>PRINT ステートメント  
 **Xml**データ型のメソッドの次の例に示すように、PRINT ステートメントでは使用できません。 **Xml**データ型のメソッドはサブクエリとして扱われ、PRINT ステートメントでは、サブクエリは許可されません。 このため、次の例では、エラーが返されます。  
  
```  
DECLARE @x xml  
SET @x = '<root>Hello</root>'  
PRINT @x.value('/root[1]', 'varchar(20)') -- will not work because this is treated as a subquery (select top 1 col from table)   
```  
  
 最初の結果に割り当てるには、ソリューション、 **value()**の変数にメソッド**xml**を入力し、クエリで変数を指定します。  
  
```  
DECLARE @x xml  
DECLARE @c varchar(max)  
SET @x = '<root>Hello</root>'  
SET @c = @x.value('/root[1]', 'varchar(11)')  
PRINT @c                                                        
```  
  
## <a name="the-group-by-clause"></a>GROUP BY 句  
 **Xml**データ型のメソッドは、内部的にサブクエリとして扱われます。 指定することはできませんので GROUP BY はスカラーを必要と、集計やサブクエリではできません、 **xml** GROUP BY 句にデータ型のメソッドです。 解決方法としては、XML メソッドを内部で使用するユーザー定義関数を呼び出します。  
  
## <a name="reporting-errors"></a>エラーの報告  
 エラーを報告するときに**xml**データ型のメソッドは、次の形式で単一のエラーを発生させます。  
  
```  
Msg errorNumber, Level levelNumber, State stateNumber:  
XQuery [database.table.method]: description_of_error  
```  
  
 例:  
  
```  
Msg 2396, Level 16, State 1:  
XQuery [xmldb_test.xmlcol.query()]: Attribute may not appear outside of an element  
```  
  
## <a name="singleton-checks"></a>シングルトンの確認  
 実行時にシングルトンであることが確実かどうかをコンパイラで判断できない場合、シングルトンを必要とするロケーション ステップ、関数パラメーター、および演算子はエラーを返します。 型指定されていないデータではこの問題が頻繁に発生します。 たとえば、属性の参照には単一の親要素が必要ですが、 単一の親ノードを選択する序数があれば問題を回避できます。 評価、 **node()**-**value()**属性値を抽出するための組み合わせには、序数を指定は不要です。 これにより、次の例を示します。  
  
### <a name="example-known-singleton"></a>例 : 既知のシングルトン  
 この例では、 **nodes()**メソッドごとに個別の行が生成されます <`book`> 要素。 **Value()**メソッド上で評価される、<`book`> ノードの値を抽出する@genreと、属性が必要ですが、シングルトンです。  
  
```  
SELECT nref.value('@genre', 'varchar(max)') LastName  
FROM   T CROSS APPLY xCol.nodes('//book') AS R(nref)  
```  
  
 型指定された XML の型の確認には XML スキーマが使用されます。 XML スキーマでノードがシングルトンとして指定されている場合、その情報がコンパイラで使用され、エラーは発生しません。 その指定がない場合は、単一のノードを選択する序数が必要です。 特に、子孫または self 軸の使用 (//)/book など、軸/タイトル、シングルトンの基数推定を失うと、\<タイトル > 要素、偶数の場合は、XML スキーマを示すようにします。 したがって、この部分は「(/book//title)[1]」と書き換えます。  
  
 型の確認のときは、//first-name[1] と (//first-name)[1] の違いを常に認識することが重要です。 前者のシーケンスを返す\<名 > の各ノードで、左端のノード\<名 > 兄弟間でのノードです。 後者に最初のシングルトンを返す\<名 > のドキュメント順で、XML インスタンス内のノードです。  
  
### <a name="example-using-value"></a>例 : value() の使用  
 型指定されていない XML 列には、次のクエリは、静的にコンパイル エラーになります。これは、ため**value()**ように最初の引数と、コンパイラは、1 つだけかどうかを決定できません、シングルトン ノードが必要ですが\<姓 > ノードは実行時に発生します。  
  
```  
SELECT xCol.value('//author/last-name', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 次のような解決策が考えられます。  
  
```  
SELECT xCol.value('//author/last-name[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 ただし、この解決しませんエラーのため複数 <`author`> ノードに各 XML インスタンスで発生する可能性があります。 次のように書き換えると、正常に動作します。  
  
```  
SELECT xCol.value('(//author/last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 このクエリは、最初の値を返します`<last-name>`各 XML インスタンス内の要素。  
  
## <a name="see-also"></a>参照  
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)  
  
  
