---
title: "nodes() メソッド (xml データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nodes() method
- nodes method
ms.assetid: 7267fe1b-2e34-4213-8bbf-1c953822446c
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5fbbbd268398ab46b150f647a8d19689d198e6e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="nodes-method-xml-data-type"></a>nodes() メソッド (xml データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **Nodes()**メソッドは、細分化する場合に便利です、 **xml**リレーショナル データにデータ型のインスタンス。 また、このメソッドにより、新しい行にマップされるノードを特定できます。  
  
 各**xml**データ型のインスタンスが、暗黙的に指定されたコンテキスト ノードです。 列や変数に格納された XML インスタンスの場合は、ドキュメント ノードがコンテキスト ノードになります。 ドキュメント ノードには、暗黙のノードの上部にある各**xml**データ型のインスタンス。  
  
 結果、 **nodes()**メソッドは、元の XML インスタンスの論理コピーが格納された行セット。 このような論理コピーでは、クエリ式で識別されるいずれかのノードが、すべての行インスタンスのコンテキスト ノードに設定されます。その結果、その後に実行されるクエリはこのようなコンテキスト ノードへ相対移動できます。  
  
 行セットからは、複数の値を取得できます。 たとえば、適用することができます、 **value()**メソッドによって返される行セットを**nodes()**および元の XML インスタンスから複数の値を取得します。 なお、 **value()**メソッド、XML インスタンスに適用されるときに 1 つだけの値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
nodes (XQuery) as Table(Column)  
```  
  
## <a name="arguments"></a>引数  
 *XQuery*  
 XQuery 式の文字列リテラルです。 このクエリ式でノードが構築されると、構築されるノードが結果の行セットで公開されます。 クエリ式の結果が空のシーケンスの場合、結果の行セットは空になります。 クエリ式で、ノードではなくアトミック値が含まれたシーケンスが静的に返される場合は、静的エラーが発生します。  
  
 *テーブル*(*列*)  
 結果の行セットのテーブル名と列名です。  
  
## <a name="remarks"></a>解説  
 たとえば、次のテーブルがあるとします。  
  
```  
T (ProductModelID int, Instructions xml)  
```  
  
 次の製造手順ドキュメントがこのテーブルに格納されます。 記載しているのはドキュメントの一部のみです。 このドキュメントには 3 つの製造場所が含まれていることに注意してください。  
  
```  
<root>  
  <Location LocationID="10"...>  
     <step>...</step>  
     <step>...</step>  
      ...  
  </Location>  
  <Location LocationID="20" ...>  
       ...  
  </Location>  
  <Location LocationID="30" ...>  
       ...  
  </Location>  
</root>  
```  
  
 A`nodes()`メソッドを呼び出すと、クエリ式`/root/Location`は 3 つの行を含む行セットを返しますのいずれかに設定を含む各コンテキスト アイテムと、元の XML ドキュメントの論理コピー、`<Location>`ノード。  
  
```  
Product  
ModelID      Instructions  
----------------------------------  
1       <root>  
             <Location LocationID="20" ... />  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
             <Location LocationID="20" ... />  
             </root>  
```  
  
 使用して、この行セットをクエリすることができますし、 **xml**データ型のメソッドです。 次のクエリを実行すると、生成された行ごとにコンテキスト アイテムのサブツリーが抽出されます。  
  
```  
SELECT T2.Loc.query('.')  
FROM   T  
CROSS APPLY Instructions.nodes('/root/Location') as T2(Loc)   
```  
  
 結果を次に示します。  
  
```  
ProductModelID  Instructions  
----------------------------------  
1        <Location LocationID="10" ... />  
1        <Location LocationID="20" ... />  
1        <Location LocationID="30" .../>  
```  
  
 返された行セットでは型情報が保持されることに注意してください。 適用できる**xml**データ型のなどメソッド、 **query()**、 **value()**、 **exist()**、および**nodes()**、の結果に、 **nodes()**メソッドです。 ただし、適用することはできません、 **modify()** XML インスタンスを変更するメソッド。  
  
 また、行セットのコンテキスト ノードは具体化できません。 つまり、このコンテキスト ノードは SELECT ステートメントでは使用できません。 ただし、IS NULL と COUNT(*) では使用できます。  
  
 使用するシナリオ、 **nodes()**メソッドは、使用する場合と同じ[OPENXML & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/openxml-transact-sql.md). したがって、XML の行セット ビューが提供されます。 ただしを使用するときにカーソルを使用する必要はありません、 **nodes()**を XML ドキュメントの複数の行を含むテーブルでのメソッドです。  
  
 によって返される行セットを**nodes()**メソッドは、名前のない行セット。 したがって、別名を使用してこれらの行セットに明示的に名前を付ける必要があります。  
  
 **Nodes()**関数は、ユーザー定義関数の結果に直接適用できません。 使用する、 **nodes()**関数、スカラー ユーザー定義関数の結果で、ユーザー定義関数の結果を変数に割り当てるか、派生テーブルを使用して、ユーザー定義関数を列の別名を割り当てる戻り値とし、CROSS APPLY を使用して別名から選択します。  
  
 次の例は、使用方法を示しています。`CROSS APPLY`をユーザー定義関数の結果から選択します。  
  
```  
USE AdventureWorks;  
GO  
  
CREATE FUNCTION XTest()  
RETURNS xml  
AS  
BEGIN  
RETURN '<document/>';  
END;  
GO  
  
SELECT A2.B.query('.')  
FROM  
(SELECT dbo.XTest()) AS A1(X)   
CROSS APPLY X.nodes('.') A2(B);  
GO  
  
DROP FUNCTION XTest;  
GO  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="using-nodes-method-against-a-variable-of-xml-type"></a>xml 型の変数に対する nodes() メソッドの使用  
 次の例では、<`Root`> 最上位要素と 3 つの <`row`> 子要素が含まれる XML ドキュメントを使用します。 クエリを使用して、`nodes()`ごとに 1 つ別のコンテキスト ノードを設定するメソッドを <`row`> 要素。 `nodes()`メソッドは、次の 3 つの行を含む行セットを返します。 各行には元の XML の論理コピーが含まれ、それぞれのコンテキスト ノードで元のドキュメントの異なる <`row`> 要素が識別されます。  
  
 その後、次のクエリを実行すると、各行のコンテキスト ノードが返されます。  
  
```  
DECLARE @x xml   
SET @x='<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>'  
SELECT T.c.query('.') AS result  
FROM   @x.nodes('/Root/row') T(c)  
GO  
```  
  
 次に結果を示します。 この例では、クエリのメソッドでコンテキスト アイテムとそのコンテンツが返されます。  
  
```  
<row id="1"><name>Larry</name><oflw>some text</oflw></row>  
<row id="2"><name>moe</name></row>  
<row id="3"/>  
```  
  
 次のように、親アクセサーをコンテキスト ノードに適用すると、3 つのノードすべての <`Root`> 要素が返されます。  
  
```  
SELECT T.c.query('..') AS result  
FROM   @x.nodes('/Root/row') T(c)  
go  
```  
  
 結果を次に示します。  
  
```  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
```  
  
### <a name="specifying-the-nodes-method-against-a-column-of-xml-type"></a>xml 型の列に対する nodes() メソッドの指定  
 自転車の製造手順がこの例では使用し、指示に格納されて**xml**の型の列、 **ProductModel**テーブル。  
  
 次の例で、`nodes()`に対してメソッドを指定する、`Instructions`の列**xml**に入力、`ProductModel`テーブル。  
  
 `nodes()`メソッドのセット、<`Location`> 要素がコンテキスト ノードを指定して、`/MI:root/MI:Location`パス。 結果の行セットには、元のドキュメント、ごとに 1 つの論理コピーが含まれています。 <`Location`> コンテキスト ノードに設定と、ドキュメント内のノードの <`Location`> 要素。 したがって、`nodes()`関数は、一連の <`Location`> コンテキスト ノードです。  
  
 `query()`この行セットに対してメソッドを要求`self::node`し、そのためを返します、`<Location>`行ごとの要素。  
  
 この例のクエリでは、各 <`Location`> 要素が、特定の製品モデルの製造手順ドキュメントのコンテキスト ノードとして設定されます。 これらのコンテキスト ノードを使用して、次のような値を取得できます。  
  
-   各場所 Id を検索 <`Location`>  
  
-   製造手順の取得 (<`step`> 子要素) の各 <`Location`>  
  
 このクエリでは、`'.'` メソッドで `self::node()` に対する省略構文 `query()` を指定して、コンテキスト アイテムを返しています。  
  
 次のことを考慮してください。  
  
-   `nodes()`メソッドは Instructions 列に適用され、行セットを返す`T (C)`です。 この行セットには、元の論理コピーが含まれています。 製造手順ドキュメントの`/root/Location`コンテキスト アイテムとして。  
  
-   CROSS APPLY 次のように適用されます。`nodes()`内の行ごとに、`Instructions`テーブルが表示され、結果セットを生成する行だけを返します。  
  
    ```  
    SELECT C.query('.') as result  
    FROM Production.ProductModel  
    CROSS APPLY Instructions.nodes('  
    declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /MI:root/MI:Location') as T(C)  
    WHERE ProductModelID=7  
    ```  
  
     結果の一部を次に示します。  
  
    ```  
    <MI:Location LocationID="10"  ...>  
       <MI:step ... />  
          ...  
    </MI:Location>  
    <MI:Location LocationID="20"  ... >  
        <MI:step ... />  
          ...  
    </MI:Location>  
    ...  
    ```  
  
### <a name="applying-nodes-to-the-rowset-returned-by-another-nodes-method"></a>別の nodes() メソッドにより返された行セットに対する nodes() の適用  
 次のコードでは、XML ドキュメントに対し、`Instructions` テーブルの `ProductModel` 列に格納されている製造手順をクエリしています。 このクエリでは、製品モデル ID、製造場所、および製造手順が含まれた行セットが返されます。  
  
 次のことを考慮してください。  
  
-   `nodes()`メソッドに適用する、`Instructions`列を返す、`T1 (Locations)`行セット。 この行セットには、元の論理コピーが含まれています。 での製造手順ドキュメントの場合は、`/root/Location`コンテキスト アイテムとして要素。  
  
-   `nodes()`適用される、`T1 (Locations)`行セットを返します、`T2 (steps)`行セット。 この行セットには、元の論理コピーが含まれています。 での製造手順ドキュメントの場合は、`/root/Location/step`コンテキスト アイテムとして要素。  
  
```  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO         
```  
  
 結果を次に示します。  
  
```  
ProductModelID LocID Step         
----------------------------         
7      10   <step ... />         
7      10   <step ... />         
...         
7      20   <step ... />         
7      20   <step ... />         
7      20   <step ... />         
...         
```  
  
 クエリを宣言、`MI`プレフィックスを 2 回です。 代わりに `WITH XMLNAMESPACES` を使用し、このプレフィックスを 1 回宣言してクエリで使用することもできます。  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions'  AS MI)  
  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO    
```  
  
## <a name="see-also"></a>参照  
 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)  
  
  

