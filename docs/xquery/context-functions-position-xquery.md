---
title: position 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- position function
- fn:position function
ms.assetid: f1bab9e4-1715-4c06-9cb0-06c7e0c9c97f
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0c2bcb078026fc66fc3d783543a1a81edb9fb458
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="context-functions---position-xquery"></a>コンテキスト関数の位置 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在処理されているアイテムのシーケンス内のコンテキスト アイテムの位置を示す整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:position() as xs:integer  
```  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、 **Fn:position()** コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。この関数との比較を行っても、静的な型の推定中にカーディナリティが減少することはありません。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml**内の列を入力、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース。  
  
### <a name="a-using-the-position-xquery-function-to-retrieve-the-first-two-product-features"></a>A. position() XQuery 関数を使用して、先頭 2 つの製品特徴を取得する  
 次のクエリは、最初の 2 つの機能の最初の 2 つの子要素を取得、<`Features`> 製品モデル カタログの説明からの要素。 かどうかより多くの機能を追加、<`there-is-more/`> 要素が結果にします。  
  
```  
SELECT CatalogDescription.query('  
     declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
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
  
-   **名前空間**キーワード、 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)クエリ本文で使用される名前空間プレフィックスを定義します。  
  
-   クエリ本文が XML を構築します、\<製品 > を持つ要素**ProductModelID**と**ProductModelName**子要素として返された製品の機能があり、します。  
  
-   **Position()** の位置を決定する、述語で使用される関数、\<機能 > 子要素のコンテキストでします。 最初または 2 番目の特徴の場合は、これが返されます。  
  
-   IF ステートメントを追加、\<そこがより/> 製品カタログに 3 つ以上の特徴がある場合、結果の要素。  
  
-   カタログの記述がテーブルに保持されていない製品モデルもあるので、WHERE 句を使用して CatalogDescriptions が NULL の行を破棄しています。  
  
 これは、結果の一部です。  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  <p1:Warranty xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
  </p1:Warranty>  
  <p2:Maintenance xmlns:p2="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer or  
                    any AdventureWorks retail store.</p2:Description>  
  </p2:Maintenance>  
  <there-is-more/>  
</Product>   
…  
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
