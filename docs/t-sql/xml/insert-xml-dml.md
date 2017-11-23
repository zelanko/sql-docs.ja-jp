---
title: "xml DML (XML) を挿入 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- inserting nodes
- insert keyword [XML DML]
- insert XML DML statement
ms.assetid: 0c95c2b3-5cc2-4c38-9e25-86493096c442
caps.latest.revision: "38"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d3c534510b174ce98a4bff06b538e1f4dc8e62c6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="insert-xml-dml"></a>insert (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  によって識別される 1 つまたは複数のノードを挿入*Expression1*子ノードまたはで識別されるノードの兄弟として*Expression2*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
insert   
      Expression1 (  
                 {as first | as last} into | after | before  
                                    Expression2  
                )  
```  
  
## <a name="arguments"></a>引数  
 *Expression1*  
 挿入する 1 つ以上のノードを識別します。 XML の定数インスタンス; 指定できます。これで、modify メソッドが適用される。 同じ XML スキーマ コレクションの型指定された XML データ型インスタンスへの参照スタンドアロンを使用して型指定されていない XML データ型インスタンス**sql:column()**/**sql:variable()**関数、または XQuery 式です。 式の結果は、ノード、テキスト ノード、または順序付けられたノードのシーケンスになります。 式をルート (/) ノードに解決することはできません。 式の結果が 1 つの値または値のシーケンスになる場合、シーケンス内の各値がスペースで区切られた 1 つのテキスト ノードとして値が挿入されます。 を複数のノードを定数として指定する場合、ノードがかっこ内に含まれ、は、コンマで区切られます。 一連の要素、属性、値などの異種シーケンスは挿入できません。 場合*Expression1*挿入が行われず、エラーは返されませんが、空のシーケンスに解決します。  
  
 into  
 によって識別されるノード*Expression1*で識別されるノードの直接の子孫 (子ノード) として挿入されます*Expression2*です。 場合内のノード*Expression2* 1 つまたは複数の子ノードは既に、いずれかを使用する必要があります**として最初**または**最後として**に新しいノードを追加する場所を指定します。 たとえば、それぞれ子リストの先頭または末尾を指定します。 **として最初**と**最後として**属性が挿入されたときに、キーワードは無視されます。  
  
 after  
 によって識別されるノード*Expression1*で識別されるノードの後に、直接の兄弟として挿入される*Expression2*です。 **後**属性を挿入するキーワードを使用することはできません。 たとえば、このキーワードを指定して、属性コンストラクターを挿入したり、XQuery から属性を返すことはできません。  
  
 before  
 によって識別されるノード*Expression1*で識別されるノードの直前に兄弟として挿入されます*Expression2*です。 **する前に**属性が挿入されるときに、キーワードを使用できません。 たとえば、このキーワードを指定して、属性コンストラクターを挿入したり、XQuery から属性を返すことはできません。  
  
 *Expression2*  
 ノードを識別します。 識別されたノード*Expression1*で識別されるノードの基準とした挿入は*Expression2*です。 現在参照されているドキュメントに存在するノードへの参照を返す XQuery 式も使用できます。 複数のノードが返されると、挿入は失敗します。 場合*Expression2*を返します。 空のシーケンス、挿入が発生するとエラーのないが返されます。 場合*Expression2*シングルトンでは、静的には、静的エラーが返されます。 *Expression2*処理命令、コメント、または属性にすることはできません。 なお*Expression2*構築されたノードではなく、ドキュメント内の既存のノードへの参照にする必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-inserting-element-nodes-into-the-document"></a>A. ドキュメントへの要素ノードの挿入  
 次の例は、ドキュメントに要素を挿入する方法を示します。 変数に XML ドキュメントが最初に、割り当てられている**xml**型です。 その後、いくつかを通じて**挿入**XML DML ステートメント、例では、要素ノードがドキュメントに挿入する方法を示しています。 それぞれの挿入後、SELECT ステートメントによって結果が表示されます。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;         
SET @myDoc = '<Root>         
    <ProductDescription ProductID="1" ProductName="Road Bike">         
        <Features>         
        </Features>         
    </ProductDescription>         
</Root>'  ;       
SELECT @myDoc;     
-- insert first feature child (no need to specify as first or as last)         
SET @myDoc.modify('         
insert <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>   
into (/Root/ProductDescription/Features)[1]') ;  
SELECT @myDoc ;        
-- insert second feature. We want this to be the first in sequence so use 'as first'         
set @myDoc.modify('         
insert <Warranty>1 year parts and labor</Warranty>          
as first         
into (/Root/ProductDescription/Features)[1]         
')  ;       
SELECT @myDoc  ;       
-- insert third feature child. This one is the last child of <Features> so use 'as last'         
SELECT @myDoc         
SET @myDoc.modify('         
insert <Material>Aluminium</Material>          
as last         
into (/Root/ProductDescription/Features)[1]         
')         
SELECT @myDoc ;        
-- Add fourth feature - this time as a sibling (and not a child)         
-- 'after' keyword is used (instead of as first or as last child)         
SELECT @myDoc  ;       
set @myDoc.modify('         
insert <BikeFrame>Strong long lasting</BikeFrame>   
after (/Root/ProductDescription/Features/Material)[1]         
')  ;       
SELECT @myDoc;  
GO  
```  
  
 この例のさまざまなパス式では、静的な型指定要件ごとに "[1]" が指定されています。 これにより、対象ノードを 1 つにしています。  
  
### <a name="b-inserting-multiple-elements-into-the-document"></a>B. ドキュメントへの複数の要素の挿入  
 次の例では、ドキュメントが最初の変数に代入**xml**型です。 次に、製品の機能を表す 2 つの要素のシーケンスは変数に割り当て、2 番目の**xml**型です。 その後、このシーケンスが最初の変数に挿入されます。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = N'<Root>             
<ProductDescription ProductID="1" ProductName="Road Bike">             
    <Features> </Features>             
</ProductDescription>             
</Root>';  
DECLARE @newFeatures xml;  
SET @newFeatures = N'<Warranty>1 year parts and labor</Warranty>            
<Maintenance>3 year parts and labor extended maintenance is available</Maintenance>';           
-- insert new features from specified variable            
SET @myDoc.modify('             
insert sql:variable("@newFeatures")             
into (/Root/ProductDescription/Features)[1] ')             
SELECT @myDoc;  
GO  
```  
  
### <a name="c-inserting-attributes-into-a-document"></a>C. ドキュメントへの属性の挿入  
 次の例では、属性をドキュメントに挿入する方法を示しています。ドキュメントが最初に、割り当てられた、 **xml**型の変数です。 次に、一連の**挿入**XML DML ステートメントは、ドキュメントに属性を挿入するために使用します。 各属性の挿入後、SELECT ステートメントによって結果が表示されます。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml ;            
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;  
SELECT @myDoc  ;          
-- insert LaborHours attribute             
SET @myDoc.modify('             
insert attribute LaborHours {".5" }             
into (/Root/Location[@LocationID=10])[1] ') ;           
SELECT @myDoc  ;          
-- insert MachineHours attribute but its value is retrived from a sql variable @Hrs             
DECLARE @Hrs float ;            
SET @Hrs =.2   ;          
SET @myDoc.modify('             
insert attribute MachineHours {sql:variable("@Hrs") }             
into   (/Root/Location[@LocationID=10])[1] ');            
SELECT @myDoc;             
-- insert sequence of attribute nodes (note the use of ',' and ()              
-- around the attributes.             
SET @myDoc.modify('             
insert (              
           attribute SetupHours {".5" },             
           attribute SomeOtherAtt {".2"}             
        )             
into (/Root/Location[@LocationID=10])[1] ');             
SELECT @myDoc;  
GO  
```  
  
### <a name="d-inserting-a-comment-node"></a>D. コメント ノードの挿入  
 XML ドキュメントに最初の変数に割り当てられているこのクエリで**xml**型です。 最初の後にコメント ノードを挿入する XML DML を使用して、<`step`> 要素。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;           
SELECT @myDoc;             
SET @myDoc.modify('             
insert <!-- some comment -->             
after (/Root/Location[@LocationID=10]/step[1])[1] ');            
SELECT @myDoc;  
GO  
```  
  
### <a name="e-inserting-a-processing-instruction"></a>E. 処理命令の挿入  
 XML ドキュメントに最初の変数に割り当てられている次のクエリで**xml**型です。 次に、XML DML キーワードを使用して、ドキュメントの先頭に処理命令が挿入されます。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>   
    <Location LocationID="10" >   
        <step>Manufacturing step 1 at this work center</step>   
        <step>Manufacturing step 2 at this work center</step>   
    </Location>   
</Root>' ;  
SELECT @myDoc ;  
SET @myDoc.modify('   
insert <?Program = "Instructions.exe" ?>   
before (/Root)[1] ') ;  
SELECT @myDoc ;  
GO  
```  
  
### <a name="f-inserting-data-using-a-cdata-section"></a>F. CDATA セクションを使用したデータの挿入  
 < や > など、XML では無効な文字が含まれるテキストを挿入するときは、次のクエリに示すように、CDATA セクションを使用してデータを挿入できます。 クエリでは CDATA セクションが指定されていますが、無効な文字はエンティティに変換され、テキスト ノードとして追加されます。 たとえば、' <' として保存&lt;です。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <ProductDescription ProductID="1" ProductName="Road Bike">             
        <Features> </Features>             
    </ProductDescription>             
</Root>' ;            
SELECT @myDoc ;            
SET @myDoc.modify('             
insert <![CDATA[ <notxml> as text </notxml> or cdata ]]>   
into  (/Root/ProductDescription/Features)[1] ') ;   
SELECT @myDoc ;  
GO  
```  
  
 クエリ内にテキスト ノードの挿入、<`Features`> 要素。  
  
```  
<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features> <notxml> as text </notxml> or cdata </Features>  
</ProductDescription>  
</Root>       
```  
  
### <a name="g-inserting-text-node"></a>G. テキスト ノードの挿入  
 XML ドキュメントに最初の変数に割り当てられているこのクエリで**xml**型です。 次に、XML DML が使用され、<`Root`> 要素の最初の子としてテキスト ノードが挿入されます。 テキスト コンストラクターを使用して、テキストを指定します。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc;  
set @myDoc.modify('  
 insert text{"Product Catalog Description"}   
 as first into (/Root)[1]  
');  
SELECT @myDoc;  
```  
  
### <a name="h-inserting-a-new-element-into-an-untyped-xml-column"></a>H. 型指定されていない xml 列への新しい要素の挿入  
 次の例に格納されている XML インスタンスを更新する XML DML を適用する、 **xml**型の列。  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE T (i int, x xml);  
go  
INSERT INTO T VALUES(1,'<Root>  
    <ProductDescription ProductID="1" ProductName="Road Bike">  
        <Features>  
            <Warranty>1 year parts and labor</Warranty>  
            <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
        </Features>  
    </ProductDescription>  
</Root>');  
go  
-- insert a new element  
UPDATE T  
SET x.modify('insert <Material>Aluminium</Material> as first  
  into   (/Root/ProductDescription/Features)[1]  
');  
GO  
```  
  
 この場合も、<`Material`> 要素ノードが挿入されるときは、パス式が 1 つの対象を返す必要があります。 これは、式の最後に [1] を追加することにより、明示的に指定します。  
  
```  
-- check the update  
SELECT x.query(' //ProductDescription/Features')  
FROM T;  
GO  
```  
  
### <a name="i-inserting-based-on-an-if-condition-statement"></a>I. IF 条件ステートメントに基づいた挿入  
 次の例では、IF 条件が内の Expression1 の一部として指定されて、**挿入**XML DML ステートメント。 条件が True の場合、<`WorkCenter`> 要素に属性が追加されます。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
    <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc  
SET @myDoc.modify('  
insert  
if (/Root/Location[@LocationID=10])  
then attribute MachineHours {".5"}  
else ()  
    as first into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 次の例は、類似する点を除いて、**挿入**XML DML ステートメントでは、条件が True の場合、ドキュメントに要素を挿入します。 つまり場合、<`WorkCenter`> 要素にはより小さいが 2 または <`step`> 子要素です。  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
        <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc;  
SET @myDoc.modify('  
insert  
if (count(/Root/Location/step) <= 2)  
then element step { "This is a new step" }  
else ()  
    as last into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 結果を次に示します。  
  
```  
<Root>  
 <WorkCenter WorkCenterID="10" LaborHours="1.2">  
  <step>Manufacturing step 1 at this work center</step>  
  <step>Manufacturing step 2 at this work center</step>  
  <step>This is a new step</step>  
 </WorkCenter>  
```  
  
### <a name="j-inserting-nodes-in-a-typed-xml-column"></a>J. 型指定された xml 列へのノードの挿入  
 この例では型指定された XML が格納された製造手順に、要素と属性が挿入**xml**列です。  
  
 例では、まずテーブルを作成する (T) で、型指定された**xml** AdventureWorks データベース内の列です。 次に、製造手順の XML インスタンスを ProductModel テーブルの Instructions 列からテーブル T にコピーします。続いて、テーブル T の XML に挿入が適用されます。  
  
```  
USE AdventureWorks;  
GO            
DROP TABLE T;  
GO             
CREATE TABLE T(ProductModelID int primary key,    
Instructions xml (Production.ManuInstructionsSchemaCollection));  
GO  
INSERT T              
    SELECT ProductModelID, Instructions             
    FROM Production.ProductModel             
    WHERE ProductModelID=7;  
GO             
SELECT Instructions             
FROM T;  
-- now insertion begins             
--1) insert a new manu. Location. The <Root> specified as              
-- expression 2 in the insert() must be singleton.      
UPDATE T   
set Instructions.modify('   
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
insert <MI:Location LocationID="1000" >   
           <MI:step>New instructions go here</MI:step>   
         </MI:Location>   
as first   
into   (/MI:root)[1]   
') ;  
  
SELECT Instructions             
FROM T ;  
-- 2) insert attributes in the new <Location>             
UPDATE T             
SET Instructions.modify('             
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";             
insert attribute LaborHours { "1000" }             
into (/MI:root/MI:Location[@LocationID=1000])[1] ');   
GO             
SELECT Instructions             
FROM T ;  
GO             
--cleanup             
DROP TABLE T ;  
GO             
```  
  
## <a name="see-also"></a>参照  
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;です。XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
