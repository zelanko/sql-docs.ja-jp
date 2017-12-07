---
title: "Expanded-qname() (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- expanded-QName function
- fn:expanded-QName function
ms.assetid: b8377042-95cc-467b-9ada-fe43cebf4bc3
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ea3ecf9c14ae49f14e6c22a4650c2dabe1ef431
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="functions-related-to-qnames---expanded-qname"></a>Qname - Expanded-qname に関連する関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  指定された URI 名前空間を持つ xs:QName 型の値を返します、 *$paramURI*とで指定されたローカル名、 *$paramLocal*です。 場合*$paramURI*空の文字列または空のシーケンスでは、名前空間を表すありません。  
  
## <a name="syntax"></a>構文  
  
```  
fn:expanded-QName($paramURI as xs:string?, $paramLocal as xs:string?) as xs:QName?  
```  
  
## <a name="arguments"></a>引数  
 *$paramURI*  
 QName の名前空間 URI です。  
  
 *$paramLocal*  
 QName のローカル名部分です。  
  
## <a name="remarks"></a>解説  
 次の状態、 **expanded-QName()**関数。  
  
-   場合、 *$paramLocal* xs:NCName 型の構文形式で指定された値がありませんが、空のシーケンスが返され、動的エラーを表します。  
  
-   は、xs:QName 型から他の型への変換はサポートされていない[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 このため、 **expanded-QName()**関数は、XML の構築では使用できません。 たとえば、`<e> expanded-QName(…) </e>` など、ノードを構築する場合、型指定なしの値を使用する必要があります。 これは、`expanded-QName()` で返される xs:QName の値を xdt:untypedAtomic に変換する必要性を意味します。 ところが、これはサポートされていません。 この件に関する解決策については、このトピック後半の例を参照してください。  
  
-   既存の QName 型の値を変更または比較できます。 たとえば、 `/root[1]/e[1] eq expanded-QName("http://nsURI" "myNS")` 、要素の値を比較し <`e`>、によって返される qname、 **expanded-QName()**関数。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml**内の列を入力、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース。  
  
### <a name="a-replacing-a-qname-type-node-value"></a>A. QName 型ノードの値を置換する  
 この例では、QName 型の要素ノードの値を変更する方法を示しています。 この例では、次の操作が実行されます。  
  
-   QName 型の要素を定義する XML スキーマ コレクションを作成します。  
  
-   テーブルを作成、 **xml** XML スキーマ コレクションを使用して型の列です。  
  
-   XML インスタンスを作成したテーブルに保存します。  
  
-   使用して、 **modify()** xml データ型のメソッド、インスタンスの QName 型要素の値を変更します。 **Expanded-QName()**関数を使用して、新しい QName 型の値を生成します。  
  
```  
-- If XML schema collection (if exists)  
-- drop xml schema collection SC  
-- go  
-- Create XML schema collection  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="QNameXSD"   
      xmlns:xqo="QNameXSD" elementFormDefault="qualified">  
      <element name="Root" type="xqo:rootType" />  
      <complexType name="rootType">  
            <sequence minOccurs="1" maxOccurs="1">  
                        <element name="ElemQN" type="xs:QName" />  
            </sequence>  
      </complexType>  
</schema>'  
go  
-- Create table.  
CREATE TABLE T( XmlCol xml(SC) )  
-- Insert sample XML instnace  
INSERT INTO T VALUES ('  
<Root xmlns="QNameXSD" xmlns:ns="http://myURI">  
      <ElemQN>ns:someName</ElemQN>  
</Root>')  
go  
-- Verify the insertion  
SELECT * from T  
go  
-- Result  
<Root xmlns="QNameXSD" xmlns:ns="http://myURI">  
  <ElemQN>ns:someName</ElemQN>  
</Root>   
```  
  
 次のクエリで、<`ElemQN`> を使用して要素の値を置き換えて、 **modify()**メソッドの xml データ型、および replace value of XML DML で示すようにします。  
  
```  
-- the value.  
UPDATE T   
SET XmlCol.modify('  
  declare default element namespace "QNameXSD";   
  replace value of /Root[1]/ElemQN   
  with expanded-QName("http://myURI", "myLocalName") ')  
go  
-- Verify the result  
SELECT * from T  
go  
```  
  
 結果は次のとおりです。 なお、要素 <`ElemQN`> QName の型には、新しい値。  
  
```  
<Root xmlns="QNameXSD" xmlns:ns="urn">  
  <ElemQN xmlns:p1="http://myURI">p1:myLocalName</ElemQN>  
</Root>  
```  
  
 次のステートメントは、この例で使用しているオブジェクトを削除します。  
  
```  
-- Cleanup  
DROP TABLE T  
go  
drop xml schema collection SC  
go  
```  
  
### <a name="b-dealing-with-the-limitations-when-using-the-expanded-qname-function"></a>B. expanded-QName() 関数を使用する際の制限事項に対処する  
 **Expanded-qname**関数は、XML の構築では使用できません。 次の例を使って説明します。 この制限を回避するために、この例では最初にノードを挿入してから、そのノードを変更しています。  
  
```  
-- if exists drop the table T  
--drop table T  
-- go  
-- Create XML schema collection  
-- DROP XML SCHEMA COLLECTION SC  
-- go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
 -- Create table T with a typed xml column (using the XML schema collection)  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- Insert an XML instance.  
insert into T values ('<root xmlns:a="http://someURI">a:b</root>')  
 go  
-- Verify  
SELECT *   
FROM T  
```  
  
 次の試行追加 <`root`> 要素が失敗すると、XML の構築では、expanded-QName() 関数はサポートされていないためです。  
  
```  
update T SET xmlCol.modify('  
insert <root>{expanded-QName("http://ns","someLocalName")}</root> as last into / ')  
go  
```  
  
 この解決方法は、まず <`root`> 要素に追加する値を保持するインスタンスを挿入し、その後これを変更します。 Nil 初期値を使用するこの例では、ときに、<`root`> 要素を挿入します。 この例では、XML スキーマ コレクションの nil 値を許可して、<`root`> 要素。  
  
```  
update T SET xmlCol.modify('  
insert <root xsi:nil="true"/> as last into / ')  
go  
-- now replace the nil value with another QName.  
update T SET xmlCol.modify('  
replace value of /root[last()] with expanded-QName("http://ns","someLocalName") ')  
go  
 -- verify   
SELECT * FROM T  
go  
-- result  
<root>b</root>  
```  
  
 `<root xmlns:a="http://someURI">a:b</root>`  
  
 `<root xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:p1="http://ns">p1:someLocalName</root>`  
  
 次のクエリで示すように、QName 値は比較できます。 だけを返す、クエリ、<`root`> によって返される値を型 QName と一致する要素、 **expanded-QName()**関数。  
  
```  
SELECT xmlCol.query('  
    for $i in /root  
    return  
       if ($i eq expanded-QName("http://ns","someLocalName") ) then  
          $i  
       else  
          ()')  
FROM T  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 1 つの制限がある: **expanded-QName()**関数が 2 番目の引数として空のシーケンスを受け入れるし、2 番目の引数が正しくない場合は、実行時エラーを生成する代わりに空白を返します。  
  
## <a name="see-also"></a>参照  
 [Qname &#40; に関連する関数XQuery と #41 です。](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
