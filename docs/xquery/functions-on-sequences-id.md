---
title: id 関数 (XQuery) |マイクロソフトドキュメント
description: XQuery id 関数を使用して、指定された xs:IDREF 値を使用して、XML インスタンス内の要素のシーケンスをドキュメント順に返す方法について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:id function
- id function
ms.assetid: de99fc60-d0ad-4117-a17d-02bdde6512b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b7f9f7ee9fa301b10c29fafb663c3a307509d7
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388515"
---
# <a name="functions-on-sequences---id"></a>シーケンスの関数 - id
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  *$arg*で提供される xs:IDREF 値の 1 つ以上の値と一致する xs:ID 値を持つ要素ノードのシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:id($arg as xs:IDREF*) as element()*  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 1 つ以上の xs:IDREF 値。  
  
## <a name="remarks"></a>解説  
 関数の結果は、XML インスタンス内の一連の要素であり、ドキュメント順に、xs:ID 値が、候補 xs:IDREFs のリスト内の 1 つ以上の xs:IDREFs に等しい。  
  
 xs:IDREF 値がどの要素とも一致しない場合は、空のシーケンスを返します。  
  
## <a name="examples"></a>例  
 このトピックでは、データベース内のさまざまな**xml**型列に格納されている XML インスタンスに[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]対する XQuery の例を示します。  
  
### <a name="a-retrieving-elements-based-on-the-idref-attribute-value"></a>A. IDREF 属性値に基づく要素の取得  
 次の例では、idref マネージャー属性に`employee`基づいて、fn:id を使用して、<>要素を取得します。 この例では、マネージャー属性は IDREF 型の属性で、eid 属性は ID 型の属性です。  
  
 特定のマネージャー属性値の**場合、id()** 関数は、ID タイプ属性値が入力 IDREF 値と一致する <`employee`> 要素を検索します。 つまり、特定の従業員に対して**は、id()** 関数は従業員マネージャを返します。  
  
 この例では次のことが行われます。  
  
-   XML スキーマ コレクションが作成されます。  
  
-   型指定された**xml**変数は、XML スキーマ コレクションを使用して作成されます。  
  
-   クエリは、<`employee`>要素の**マネージャー** IDREF 属性によって参照される ID 属性値を持つ要素を取得します。  
  
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
 次の例では、<>`Customer`要素の OrderList 属性は IDREFS 型属性です。 この例では特定の顧客に対応する注文 ID がリストされます。 各注文 ID に対して、<の下に`Order`<>`Customer`要素子>、注文値を提供します。  
  
 クエリ式 `data(CustOrders:Customers/Customer[1]/@OrderList)[1]` では、最初の顧客の最初の値が IDRES 一覧から取得されます。 この値は **、id()** 関数に渡されます。 次に、この関数は`Order`、orderID 属性値が**id()** 関数への入力と一致する<>要素を検索します。  
  
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
 制限事項は次のとおりです。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]**は、2**つの引数のバージョンの id() をサポートしていません。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]**は、id()** の引数タイプが xs:IDREF* のサブタイプである必要があります。  
  
## <a name="see-also"></a>参照  
 [シーケンス上の関数](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)  
  
  
