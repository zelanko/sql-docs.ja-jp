---
title: concat 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:concat function
- concat function [XQuery]
ms.assetid: d50afd20-a297-445e-be9e-13b48017e7ca
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8be65777bb65ad54735ad6bdf43ea88608355c5b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="functions-on-string-values---concat"></a>文字列値 - concat に関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  0 個以上の文字列を引数として受け取り、それらの値を結合した文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:concat ($string as xs:string?  
           ,$string as xs:string?  
           [, ...]) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$string*  
 連結する文字列 (省略可能)。  
  
## <a name="remarks"></a>解説  
 この関数には少なくとも 2 つの引数が必要です。 空のシーケンスを引数として渡した場合、長さゼロの文字列として処理されます。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 XQuery 関数におけるサロゲート ペアの動作は、データベースの互換性レベルに左右されます。場合によっては、関数の既定の名前空間 URI に左右されることもあります。 詳細については、のトピックでは、「XQuery 関数はサロゲート対応」のセクションを参照して[SQL Server 2016 におけるデータベース エンジン機能の重大な変更](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)です。 参照してください[ALTER DATABASE 互換性レベル&#40;TRANSACT-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)と[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md)です。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks サンプル データベース内の列を入力します。  
  
### <a name="a-using-the-concat-xquery-function-to-concatenate-strings"></a>A. concat() XQuery 関数を使用した文字列の連結  
 特定の製品モデルについて、保証期間と保証内容を連結した文字列を返します。 カタログの説明ドキュメントで、<`Warranty`> の要素から成る <`WarrantyPeriod`> と <`Description`> 子要素です。  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"  
        ProductModelName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE  PD.ProductModelID=28  
  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   CatalogDescription、SELECT 句では、 **xml**型の列です。 したがって、 [query() メソッド (XML データ型)](../t-sql/xml/query-method-xml-data-type.md)Instructions.query() を使用します。 query メソッドの引数には XQuery ステートメントを指定しています。  
  
-   クエリを実行する対象のドキュメントには名前空間を使用します。 したがって、**名前空間**キーワードの使用を名前空間のプレフィックスを定義します。 詳細については、次を参照してください。 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)です。  
  
 結果を次に示します。  
  
```  
<Product ProductModelID="28" ProductModelName="Road-450">1 year-parts and labor</Product>  
```  
  
 上のクエリでは、特定の製品の情報を取得しました。 次のクエリは、XML のカタログの説明が保存されているすべての製品について同じ情報を取得します。 **Exist()** のメソッド、 **xml**データ型の場合は、行に XML ドキュメントには、WHERE 句が True を返しますで、<`ProductDescription`> 要素。  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"   
        ProductName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE CatalogDescription.exist('//pd:ProductDescription ') = 1  
  
```  
  
 によって返されるブール値を**exist()** のメソッド、 **xml**型が 1 と比較されます。  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Concat()** SQL Server の関数は xs:string 型の値のみを受け入れます。 それ以外の値は、明示的に xs:string または xdt:untypedAtomic にキャストする必要があります。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
