---
title: "id 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:id function
- id function
ms.assetid: de99fc60-d0ad-4117-a17d-02bdde6512b4
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 963e5eb2c2b0ddaec5674f2f7c5f930ed6c34806
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-sequences---id"></a>シーケンスの機能 id
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  提供された xs:IDREF 値の 1 つ以上の値と一致する xs:ID 値を持つ要素ノードのシーケンスを返します*$arg*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:id($arg as xs:IDREF*) as element()*  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 1 つ以上の xs:IDREF 値。  
  
## <a name="remarks"></a>解説  
 関数の結果は、XML インスタンス内の要素をドキュメント順に示したシーケンスです。シーケンスを形成する要素の xs:ID 値は、候補となる xs:IDREF のリストに含まれている 1 つ以上の xs:IDREF のいずれかに一致します。  
  
 xs:IDREF 値がどの要素とも一致しない場合は、空のシーケンスを返します。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml**内の列を入力、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース。  
  
### <a name="a-retrieving-elements-based-on-the-idref-attribute-value"></a>A. IDREF 属性値に基づいて要素を取得する  
 次の例では、fn:id を使用し、IDREF マネージャー属性に基づいて <`employee`> 要素を取得します。 この例では、マネージャー属性は IDREF 型の属性で、eid 属性は ID 型の属性です。  
  
 特定のマネージャー属性値に対して、 **id()**検索の機能、<`employee`> ID 型属性の値が入力の IDREF 値に一致する要素。 つまり、特定の従業員、 **id()**関数は、従業員のマネージャーを返します。  
  
 この例では次のことが行われます。  
  
-   XML スキーマ コレクションが作成されます。  
  
-   型指定された**xml** XML スキーマ コレクションを使用して変数を作成します。  
  
-   クエリによって参照される ID 属性値を持つ要素を取得する、 **manager**の IDREF 属性、<`employee`> 要素。  
  
```  
-- If exists, drop the XML schema collection (SC).  
-- drop xml schema collection SC  
-- go  
  
create xml schema collection SC as  
'<schema xmlns="http://www.w3.org/2001/XMLSchema" xmlns:e="emp" targetNamespace="emp">  
            <element name="employees" type="e:EmployeesType"/>  
            <complexType name="EmployeesType">  
                 <sequence>  
                      <element name="employee" type="e:EmployeeType" minOccurs="0" maxOccurs="unbounded" />  
                 </sequence>  
            </complexType>    
  
            <complexType name="EmployeeType">  
                        <attribute name="eid" type="ID" />  
                        <attribute name="name" type="string" />  
                        <attribute name="manager" type="IDREF" />  
            </complexType>         
</schema>'  
go  
```  
  
```  
declare @x xml(SC)  
set @x='<e:employees xmlns:e="emp">  
<employee eid="e1" name="Joe" manager="e10" />  
<employee eid="e2" name="Bob" manager="e10" />  
<employee eid="e10" name="Dave" manager="e10" />  
</e:employees>'  
  
select @x.value(' declare namespace e="emp";   
 (fn:id(e:employees/employee[@name="Joe"]/@manager)/@name)[1]', 'varchar(50)')   
Go  
```  
  
 クエリは値として "Dave" を返します。 これは、Dave が Joe のマネージャーであることを示します。  
  
### <a name="b-retrieving-elements-based-on-the-orderlist-idrefs-attribute-value"></a>B. OrderList IDREFS 属性値に基づいて要素を取得する  
 次の例では、OrderList 属性では、<`Customer`> 要素属性は IDREFS 型属性です。 この例では特定の顧客に対応する注文 ID がリストされます。 各注文 id の場合は、<`Order`> 下の子要素、<`Customer`> 順序の値を指定します。  
  
 クエリ式 `data(CustOrders:Customers/Customer[1]/@OrderList)[1]` では、最初の顧客の最初の値が IDRES 一覧から取得されます。 この値に渡され、 **id()**関数。 関数で検索し、<`Order`> 要素の OrderID 属性値に一致する入力、 **id()**関数。  
  
```  
drop xml schema collection SC  
go  
create xml schema collection SC as  
'<schema xmlns="http://www.w3.org/2001/XMLSchema" xmlns:Customers="Customers" targetNamespace="Customers">  
            <element name="Customers" type="Customers:CustomersType"/>  
            <complexType name="CustomersType">  
                        <sequence>  
                            <element name="Customer" type="Customers:CustomerType" minOccurs="0" maxOccurs="unbounded" />  
                        </sequence>  
            </complexType>  
             <complexType name="OrderType">  
                <sequence minOccurs="0" maxOccurs="unbounded">  
                            <choice>  
                                <element name="OrderValue" type="integer" minOccurs="0" maxOccurs="unbounded"/>  
                            </choice>  
                </sequence>                                             
                <attribute name="OrderID" type="ID" />  
            </complexType>  
  
            <complexType name="CustomerType">  
                <sequence minOccurs="0" maxOccurs="unbounded">  
                            <choice>  
                                <element name="spouse" type="string" minOccurs="0" maxOccurs="unbounded"/>  
                                <element name="Order" type="Customers:OrderType" minOccurs="0" maxOccurs="unbounded"/>  
                            </choice>  
                </sequence>                                             
                <attribute name="CustomerID" type="string" />  
                <attribute name="OrderList" type="IDREFS" />  
            </complexType>  
 </schema>'  
go  
declare @x xml(SC)  
set @x='<CustOrders:Customers xmlns:CustOrders="Customers">  
                <Customer CustomerID="C1" OrderList="OrderA OrderB"  >  
                              <spouse>Jenny</spouse>  
                                <Order OrderID="OrderA"><OrderValue>11</OrderValue></Order>  
                                <Order OrderID="OrderB"><OrderValue>22</OrderValue></Order>  
  
                </Customer>  
                <Customer CustomerID="C2" OrderList="OrderC OrderD" >  
                                <spouse>John</spouse>  
                                <Order OrderID="OrderC"><OrderValue>33</OrderValue></Order>  
                                <Order OrderID="OrderD"><OrderValue>44</OrderValue></Order>  
  
                        </Customer>  
                <Customer CustomerID="C3"  OrderList="OrderE OrderF" >  
                                <spouse>Jane</spouse>  
                                <Order OrderID="OrderE"><OrderValue>55</OrderValue></Order>  
                                <Order OrderID="OrderF"><OrderValue>55</OrderValue></Order>  
                </Customer>  
                <Customer CustomerID="C4"  OrderList="OrderG"  >  
                                <spouse>Tim</spouse>  
                                <Order OrderID="OrderG"><OrderValue>66</OrderValue></Order>  
                        </Customer>  
                <Customer CustomerID="C5"  >  
                </Customer>  
                <Customer CustomerID="C6" >  
                </Customer>  
                <Customer CustomerID="C7"  >  
                </Customer>  
</CustOrders:Customers>'  
select @x.query('declare namespace CustOrders="Customers";  
  id(data(CustOrders:Customers/Customer[1]/@OrderList)[1])')  
  
-- result  
<Order OrderID="OrderA">  
  <OrderValue>11</OrderValue>  
</Order>  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]2 つの引数バージョンをサポートしていない**id()**です。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]引数の型を必要と**id()** xs:idref のサブタイプであります。  
  
## <a name="see-also"></a>参照  
 [シーケンスの関数](http://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)  
  
  

