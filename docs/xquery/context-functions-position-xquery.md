---
title: position 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- position function
- fn:position function
ms.assetid: f1bab9e4-1715-4c06-9cb0-06c7e0c9c97f
author: rothja
ms.author: jroth
ms.openlocfilehash: de9f30c3c63030aa956366c222b7cbda94e2becb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038982"
---
# <a name="context-functions---position-xquery"></a>コンテキスト関数 - position (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在処理されているアイテムのシーケンス内のコンテキスト アイテムの位置を示す整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:position() as xs:integer  
```  
  
## <a name="remarks"></a>Remarks  
 で[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は、 **fn: position ()** は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([]) 内でのみ使用できます。この関数と比較しても、静的な型の推論時にカーディナリティが減少することはありません。  
  
## <a name="examples"></a>使用例  
 このトピックでは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベースのさまざまな**xml**型の列に格納されている xml インスタンスに対して XQuery の例を示します。  
  
### <a name="a-using-the-position-xquery-function-to-retrieve-the-first-two-product-features"></a>A. Position () XQuery 関数を使用した最初の2つの製品機能の取得  
 次のクエリでは、製品モデルカタログの説明から、最初の2つ`Features`の機能、<> 要素の最初の2つの子要素を取得します。 その他の機能がある場合は、<`there-is-more/`> 要素を結果に追加します。  
  
```  
SELECT CatalogDescription.query('  
     declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)内の**namespace**キーワードは、クエリ本文で使用される名前空間プレフィックスを定義します。  
  
-   クエリ本文は、 **Productmodelid**属性\<と**ProductModelName**属性を持つ product> 要素を持つ XML を構築し、子要素として返される製品機能を持ちます。  
  
-   **Position ()** 関数は、コンテキストでの\<機能> 子要素の位置を決定するために、述語で使用されます。 最初または2番目の機能の場合は、それが返されます。  
  
-   製品カタログに3つ\<以上の機能がある場合、if ステートメントによって、その結果には、more/> 要素が追加されます。  
  
-   カタログの記述がテーブルに保持されていない製品モデルもあるので、WHERE 句を使用して CatalogDescriptions が NULL の行を破棄しています。  
  
 結果の一部を次に示します。  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  <p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
  </p1:Warranty>  
  <p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer or  
                    any AdventureWorks retail store.</p2:Description>  
  </p2:Maintenance>  
  <there-is-more/>  
</Product>   
...  
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
