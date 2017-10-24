---
title: "xml DML (XML) の削除 |Microsoft ドキュメント"
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
- XML DML [SQL Server]
- delete keyword
- delete statement [XML DML]
- deleting nodes
ms.assetid: b22c93a4-b84d-4356-af4c-6013322a4b71
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57959308668cc5ea0455f6a4135c00482dbca15e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="delete-xml-dml"></a>delete (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML インスタンスのノードを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
delete Expression  
```  
  
## <a name="arguments"></a>引数  
 *[式]*  
 削除するノードを特定する XQuery 式です。 この式で選択されたすべてのノードと、これらの選択されたノード内にあるすべてのノードまたは値が削除されます。 」の説明に従って[xml DML (XML) を挿入](../../t-sql/xml/insert-xml-dml.md)ドキュメント内の既存のノードへの参照でなければなりません。 構築されたノードは使用できません。 また、この式をルート (/) ノードにすることもできません。 この式で空のシーケンスが返されると、削除が行われず、エラーも返されません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-deleting-nodes-from-a-document-stored-in-an-untyped-xml-variable"></a>A. 型指定されていない XML 変数に格納されているドキュメントからノードを削除する  
 次の例では、ドキュメントのさまざまなノードを削除する方法を示します。 変数に XML インスタンスが最初に、割り当てられている**xml**型です。 その後、これに続く delete XML DML ステートメントにより、ドキュメントの各種ノードを削除しています。  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<?Instructions for=TheWC.exe ?>   
<Root>  
 <!-- instructions for the 1st work center -->  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Some text 1  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
SELECT @myDoc  
  
-- delete an attribute  
SET @myDoc.modify('  
  delete /Root/Location/@MachineHours  
')  
SELECT @myDoc  
  
-- delete an element  
SET @myDoc.modify('  
  delete /Root/Location/step[2]  
')  
SELECT @myDoc  
  
-- delete text node (in <Location>  
SET @myDoc.modify('  
  delete /Root/Location/text()  
')  
SELECT @myDoc  
  
-- delete all processing instructions  
SET @myDoc.modify('  
  delete //processing-instruction()  
')  
SELECT @myDoc  
```  
  
### <a name="b-deleting-nodes-from-a-document-stored-in-an-untyped-xml-column"></a>B. 型指定されていない XML 列に格納されているドキュメントからノードを削除する  
 次の例で、**削除**XML DML ステートメントの 2 番目の子要素を削除する <`Features`> 列に格納されているドキュメントからです。  
  
```  
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
-- verify the contents before delete  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
-- delete the second feature  
UPDATE T  
SET x.modify('delete /Root/ProductDescription/Features/*[2]')  
-- verify the deletion  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   [Modify() メソッド (xml データ型)](../../t-sql/xml/modify-method-xml-data-type.md)指定に使用される、**削除**XML DML キーワードです。  
  
-   [Query() メソッド (xml データ型)](../../t-sql/xml/query-method-xml-data-type.md)ドキュメントのクエリに使用されます。  
  
### <a name="c-deleting-nodes-from-a-typed-xml-column"></a>C. 型指定された xml 列からノードを削除する  
 この例では、ノードを削除、製造手順の XML ドキュメントに保存されてから、型指定された**xml**列です。  
  
 例では、まずテーブルを作成する (T) で、型指定された**xml** AdventureWorks データベース内の列です。 続いて、ProductModel テーブルの Instructions 列から製造手順の XML インスタンスをテーブル T にコピーし、このコピーされたドキュメントから 1 つ以上のノードを削除します。  
  
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
select Instructions  
from T  
--1) insert <Location 1000/>. Note: <Root> must be singleton in the query  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  insert <MI:Location LocationID="1000"  LaborHours="1000" >  
           These are manu steps at location 1000.   
           <MI:step>New step1 instructions</MI:step>  
           Instructions for step 2 are here  
           <MI:step>New step 2 instructions</MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
  
-- delete an attribute  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/@LaborHours)   
')  
go  
select Instructions  
from T  
-- delete text in <location>  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/text())   
')  
go  
select Instructions  
from T  
-- delete 2nd manu step at location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/MI:step[2])   
')  
go  
select Instructions  
from T  
-- cleanup  
drop table T  
go  
```  
  
## <a name="see-also"></a>参照  
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 & #40 です。XML DML"&"#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

