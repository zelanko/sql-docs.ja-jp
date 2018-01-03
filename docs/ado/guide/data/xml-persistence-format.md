---
title: "永続化形式の XML |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d56fbae28f2c1d5192f2ac1e1c4f8939d7e4b027
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="xml-persistence-format"></a>XML の永続化の形式
ADO では、utf-8 が解決されない XML ストリームのエンコーディングを使用します。  
  
 ADO XML 形式は、2 つのセクションでは、データのセクションで後にスキーマ セクションに分割されます。 Northwind データベースから Shippers テーブルの XML ファイルの例を次に示します。 次の例では、XML のさまざまな部分を説明します。  
  
## <a name="remarks"></a>解説  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"   
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"   
xmlns:rs="urn:schemas-microsoft-com:rowset"   
xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="ShipperID" rs:number="1"   
        rs:basetable="shippers" rs:basecolumn="ShipperID"  
        rs:keycolumn="true">   
        <s:datatype dt:type="int" dt:maxLength="4" rs:precision="10"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="CompanyName" rs:number="2"   
        rs:nullable="true" rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="CompanyName">   
        <s:datatype dt:type="string" dt:maxLength="40" />   
      </s:AttributeType>   
      <s:AttributeType name="Phone" rs:number="3" rs:nullable="true"   
        rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="Phone">   
        <s:datatype dt:type="string" dt:maxLength="24"/>   
      </s:AttributeType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  
  <rs:data>   
    <z:row ShipperID="1" CompanyName="Speedy Express"   
      Phone="(503) 555-9831"/>   
    <z:row ShipperID="2" CompanyName="United Package"   
      Phone="(503) 555-3199"/>   
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>   
  </rs:data>   
</xml>  
```  
  
 スキーマは、名前空間、スキーマ」セクションのセクション「データの宣言を示します。 スキーマのセクションには、行、運送、CompanyName、および電話の定義が含まれています。  
  
 スキーマ定義に準拠している、 [W3C の XML データの指定](http://www.w3.org/TR/1998/NOTE-XML-data/)(ただし、検証は、Internet Explorer 5 では発生しません) に完全に検証することができます。 XML データは、現在のレコード セットの永続化にのみサポートされているスキーマ形式です。  
  
 データ セクションには、運送会社に関する情報を含む 3 つの行があります。 データのセクションが空である空の行セットのですが、 \<rs: データ > タグが存在する必要があります。 データのない、記述することも、タグの短縮形単に\<rs: データ/>。 "Rs"の付いたすべてのタグは、urn: スキーマで定義された名前空間内にあることを示す-microsoft-com:rowset です。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
