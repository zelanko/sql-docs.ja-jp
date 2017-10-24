---
title: "XQuery での名前空間の処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
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
- declaring namespaces
- namespaces [XQuery]
- XQuery, namespaces
ms.assetid: 542b63da-4d3d-4ad5-acea-f577730688f1
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4689645ffae5399894bd4208535527d528ccaefb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="handling-namespaces-in-xquery"></a>XQuery での名前空間の処理
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックでは、クエリ内での名前空間の処理のサンプルを提供します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-declaring-a-namespace"></a>A. 名前空間の宣言  
 次のクエリは、特定の製品モデルの製造工程を取得します。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        /AWMI:root/AWMI:Location[1]/AWMI:step  
    ') as x  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 結果の一部を次に示します。  
  
```  
<AWMI:step xmlns:AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions">Insert <AWMI:material>aluminum sheet MS-2341</AWMI:material> into the <AWMI:tool>T-85A framing tool</AWMI:tool>. </AWMI:step>  
…  
```  
  
 なお、**名前空間**新しい名前空間プレフィックスを定義するキーワードを使用"AWMI:"です。 このクエリでは、該当する名前空間のスコープ内にあるすべての要素に、このプレフィックスを使用する必要があります。  
  
### <a name="b-declaring-a-default-namespace"></a>B. 既定の名前空間を宣言します。  
 前のクエリでは、新しい名前空間プレフィックスが宣言されていました。 また、クエリでは目的の XML 構造を選択する場合、そのプレフィックスを使用する必要がありました。 代わりに、次のようにクエリを変更して、任意の名前空間を既定の名前空間として宣言できます。  
  
```  
SELECT Instructions.query('  
     declare default element namespace "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        /root/Location[1]/step  
    ') as x  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 結果  
  
```  
<step xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions">Insert <material>aluminum sheet MS-2341</material> into the <tool>T-85A framing tool</tool>. </step>  
…  
```  
  
 この例では、定義された名前空間 `"http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"` により、既定の (空の) 名前空間が上書きされています。 このため、クエリに使用するパス式内では名前空間プレフィックスが指定されていません。 また、結果に表示される要素名にも、名前空間プレフィックスはありません。 既定の名前空間は、すべての要素に適用されますが、属性には適用されません。  
  
### <a name="c-using-namespaces-in-xml-construction"></a>C. XML 構築時の名前空間の使用  
 新しい名前空間を定義すると、クエリだけではなく、XML の構築でも定義された名前空間が使用されます。 たとえば、XML の構築にすることができます、新しい名前空間を使用して定義、"`declare namespace ...`"宣言し、要素および属性をクエリ結果内に表示されるように構築することとその名前空間を使用します。  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     declare namespace myNS="uri:SomeNamespace";<myNS:Result>  
          { /ProductDescription/Summary }  
       </myNS:Result>  
  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 結果を次に示します。  
  
```  
  
      <myNS:Result xmlns:myNS="uri:SomeNamespace">  
  <Summary xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">  
     Our top-of-the-line competition mountain bike. Performance-enhancing   
     options include the innovative HL Frame, super-smooth front   
     suspension, and traction for all terrain.</p1:p>  
  </Summary>  
</myNS:Result>  
```  
  
 代わりに、次のクエリのように、XML 構築の一部として、名前空間を使用する各所で明示的に定義することもできます。  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       <myNS:Result xmlns:myNS="uri:SomeNamespace">  
          { /ProductDescription/Summary }  
       </myNS:Result>  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
### <a name="d-construction-using-default-namespaces"></a>D. 既定の名前空間を使用した構築  
 構築後の XML で既定の名前空間が使用されるように定義することもできます。 たとえば、次のクエリは、既定の名前空間"uri:SomeNamespace"を指定する方法を示します\\など、構築されるローカルで名前付きの要素の既定値として使用する、`<Result>`要素。  
  
```  
SELECT CatalogDescription.query('  
      declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      declare default element namespace "uri:SomeNamespace";<Result>  
          { /PD:ProductDescription/PD:Summary }  
       </Result>  
  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 結果を次に示します。  
  
```  
  
      <Result xmlns="uri:SomeNamespace">  
  <PD:Summary xmlns:PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">  
         Our top-of-the-line competition mountain bike. Performance-  
         enhancing options include the innovative HL Frame, super-smooth   
         front suspension, and traction for all terrain.</p1:p>  
  </PD:Summary>  
</Result>  
```  
  
 要素の既定の名前空間または空の名前空間を上書きすることで、構築された XML 内のすべてのローカル名付きの要素が、上書き後の既定の名前空間にバインドされます。 したがって、空の名前空間を利用して XML を柔軟に構築する必要がある場合は、要素の既定の名前空間を上書きしないようにします。  
  
## <a name="see-also"></a>参照  
 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  

