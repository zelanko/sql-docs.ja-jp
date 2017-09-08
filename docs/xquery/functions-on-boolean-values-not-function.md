---
title: "not 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
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
- effective Boolean value [XQuery]
- fn:not function
- not function [XQuery]
- EBV
ms.assetid: 93dfc377-45f1-4384-9392-560d9331a915
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f64f286b59b67e31d0b49527a83409b81ba2210
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-boolean-values---not-function"></a>ブール値の not 関数に対する関数 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  True の場合の有効なブール値*$arg*が false になり、FALSE を返しますの有効なブール値*$arg*は true です。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:not($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 有効なブール値が指定されているアイテムのシーケンス。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-not-xquery-function-to-find-product-models-whose-catalog-descriptions-do-not-include-the-specifications-element"></a>A. Not() XQuery 関数を使用して、製品モデル カタログの説明を検索するは含めないでください、\<仕様 > 要素。  
 次のクエリを使用して、カタログの説明に <`Specifications`> 要素が含まれていない製品モデルの製品モデル ID を含む XML を作成します。  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
       <Product   
           ProductModelID="{ sql:column("ProductModelID") }"  
        />  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications/*)]  '  
     ) = 0  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   このドキュメントは名前空間を使用しているため、サンプルでは WITH NAMESPACES ステートメントを使用しています。 別のオプションは、使用する、**名前空間を宣言**キーワード、 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)プレフィックスを定義します。  
  
-   クエリを含む XML を構築し、<`Product`> 要素とその**ProductModelID**属性。  
  
-   WHERE 句を使用して、 [exist() メソッド (XML データ型)](../t-sql/xml/exist-method-xml-data-type.md)行をフィルター選択します。 **Exist()**メソッドがある場合、True を返します\<ProductDescription > 要素を持たない\<Specification > 子要素です。 使用に注意してください、 **not()**関数。  
  
 各製品モデル カタログの説明が含まれているために、この結果セットが空では、\<仕様 > 要素。  
  
### <a name="b-using-the-not-xquery-function-to-retrieve-work-center-locations-that-do-not-have-a-machinehours-attribute"></a>B. not() XQuery 関数を使用して、MachineHours 属性を持たないワーク センターの場所を取得する  
 次のクエリは、Instructions 列に対して指定されています。 この列には、製品モデルの製造手順が格納されています。  
  
 特定の製品モデルでは、MachineHours を指定しないワーク センターの場所がクエリによって取得されます。 属性は、 **MachineHours**が指定されていない、\<場所 > 要素。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in /AWMI:root/AWMI:Location[not(@MachineHours)]  
     return  
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ $i/@LaborHours }" >  
        </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7   
```  
  
 上記のクエリでは、次を注意してください。  
  
-   **Declarenamespace**で[XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)Adventure Works の製造手順の名前空間プレフィックスを定義します。 この定義は、製造手順ドキュメントで使用されているのと同じ名前空間を表しています。  
  
-   クエリで、**されません (@MachineHours)**述語がある場合、True を返しますありません**MachineHours**属性。  
  
 結果を次に示します。  
  
```  
ProductModelID Result   
-------------- --------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Not()**関数では、xs:boolean 型、node() *、または空のシーケンスの引数のみがサポートされます。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
