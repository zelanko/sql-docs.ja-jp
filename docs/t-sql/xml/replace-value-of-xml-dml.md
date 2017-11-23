---
title: "xml DML (XML) の値を置き換える |Microsoft ドキュメント"
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
- update keyword
- replacement values [XML DML]
- updating node values
- replace value of XML DML statement
ms.assetid: c310f6df-7adf-493b-b56b-8e3143b13ae7
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2ac4a0a7f1e2dc5d5f268c306c0e1a92316c99da
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="replace-value-of-xml-dml"></a>replace value of (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ドキュメント内のノードの値を更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
replace value of Expression1   
with Expression2  
```  
  
## <a name="arguments"></a>引数  
 *Expression1*  
 値を更新するノードを特定します。 この引数では、ノードを 1 つだけ特定します。 つまり、 *Expression1*は静的なシングルトンにする必要があります。 XML が型指定されている場合、ノードの型は単純型でなければなりません。 複数のノードを選択すると、エラーが発生します。 場合*Expression1*を返します。 空のシーケンス値の置換が発生するとエラーのないが返されます。 *Expression1*が単に型指定された内容 (リストまたはアトミック型)、テキスト ノード、または属性ノードを単一の要素を返す必要があります。 *Expression1*共用体型、複合型、処理命令、ドキュメント ノード、またはコメント ノードにすることはできません。 これらのいずれかを指定すると、エラーが返されます。  
  
 *Expression2*  
 ノードの新しい値を特定します。 単に型指定されたノードを返す式を指定できます**data()**暗黙的に使用されます。 値が、値の一覧である場合、**更新**ステートメント リストと古い値が置き換えられます。 型指定された XML インスタンスを変更する*Expression2*と同じ型またはのサブタイプにする必要があります*式*1 です。 それ以外の式を指定すると、エラーが返されます。 変更する場合、型指定されていない XML インスタンス*Expression2*アトミック化可能な式を指定する必要があります。 それ以外の式を指定すると、エラーが返されます。  
  
## <a name="examples"></a>使用例  
 次の例の**の値を置き換える**XML DML ステートメントは、XML ドキュメント内のノードを更新する方法を示しています。  
  
### <a name="a-replacing-values-in-an-xml-instance"></a>A. XML インスタンスの値を置換する  
 ドキュメント インスタンスに最初の変数に割り当てられている次の例では、 **xml**型です。 その後、**の値を置き換える**XML DML ステートメントは、ドキュメント内の値を更新します。  
  
```  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Manufacturing steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>';  
SELECT @myDoc;  
  
-- update text in the first manufacturing step  
SET @myDoc.modify('  
  replace value of (/Root/Location/step[1]/text())[1]  
  with     "new text describing the manu step"  
');  
SELECT @myDoc;  
-- update attribute value  
SET @myDoc.modify('  
  replace value of (/Root/Location/@LaborHours)[1]  
  with     "100.0"  
');  
SELECT @myDoc;  
```  
  
 更新の対象ノードは 1 つだけにする必要があることに注意してください。パス式の末尾に "[1]" を追加して明示的に 1 つのノードを指定します。  
  
### <a name="b-using-the-if-expression-to-determine-replacement-value"></a>B. if 式を使用して置換値を決定する  
 指定することができます、**場合**の Expression2 内の式、 **XML DML の値を置き換える**ステートメントでは、次の例で示すようにします。 Expression1 では、最初のワーク センターの LaborHours 属性を更新することを特定します。 Expression2 を使用して、**場合**LaborHours 属性の新しい値を決定する式。  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours=".1"  
            MachineHours=".2" >Manu steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
--SELECT @myDoc  
  
SET @myDoc.modify('  
  replace value of (/Root/Location[1]/@LaborHours)[1]  
  with (  
       if (count(/Root/Location[1]/step) > 3) then  
         "3.0"  
       else  
          "1.0"  
      )  
')  
SELECT @myDoc  
```  
  
### <a name="c-updating-xml-stored-in-an-untyped-xml-column"></a>C. 型指定されていない XML 列に格納されている XML を更新する  
 次の例では、列に格納されている XML を更新します。  
  
```  
drop table T  
go  
CREATE TABLE T (i int, x xml)  
go  
INSERT INTO T VALUES(1,'<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>')  
go  
-- verify the current <ProductDescription> element  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
-- update the ProductName attribute value  
UPDATE T  
SET x.modify('  
  replace value of (/Root/ProductDescription/@ProductName)[1]  
  with "New Road Bike" ')  
-- verify the update  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
```  
  
### <a name="d-updating-xml-stored-in-a-typed-xml-column"></a>D. 型指定された XML 列に格納されている XML を更新する  
 この例では、型指定された XML 列に格納されている製造手順ドキュメント内の値を置換します。  
  
 この例では、まず、型指定された XML 列を含むテーブル (T) を AdventureWorks データベースに作成します。 次に、製造手順の XML インスタンスを ProductModel テーブルの Instructions 列からテーブル T にコピーします。続いて、テーブル T の XML に挿入が適用されます。  
  
```  
use AdventureWorks  
go  
drop table T  
go  
create table T(ProductModelID int primary key,   
Instructions xml (Production.ManuInstructionsSchemaCollection))  
go  
insert  T   
select ProductModelID, Instructions  
from Production.ProductModel  
where ProductModelID=7  
go  
--insert a new location - <Location 1000/>.   
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
insert <MI:Location LocationID="1000"  LaborHours="1000"  LotSize="1000" >  
           <MI:step>Do something using <MI:tool>hammer</MI:tool></MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
go  
-- Now replace manu. tool in location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/MI:step/MI:tool)[1]   
  with   "screwdriver"  
')  
go  
select Instructions  
from T  
-- Now replace value of lot size  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/@LotSize)[1]   
  with   500 cast as xs:decimal ?  
')  
go  
select Instructions  
from T  
```  
  
 使用に注意してください**キャスト**LotSize 値を置換します。 この処理は、値を特定の型にする必要がある場合に必要です。 この例では、値を 500 にした場合、明示的にキャストする必要はありません。  
  
## <a name="see-also"></a>参照  
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;です。XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
