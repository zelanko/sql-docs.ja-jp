---
title: コンス トラクター関数 (XQuery) |Microsoft ドキュメント
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
- constructor functions [XQuery]
ms.assetid: 98562d0e-d0e0-4f62-b001-90acbac67277
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6db36cc2dbd664869633d1d2f198684098ba29b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="constructor-functions-xquery"></a>コンストラクター関数 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  コンストラクター関数は、指定された入力から、XSD の組み込みのアトミック型またはユーザー定義のアトミック型のインスタンスを生成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TYP($atomicvalue as xdt:anyAtomicType?  
  
) as TYP?  
  
```  
  
## <a name="arguments"></a>引数  
 *$strval*  
 変換される文字列。  
  
 *TYP*  
 任意の組み込み XSD 型。  
  
## <a name="remarks"></a>解説  
 コンストラクターは基本データ型、および派生されたアトミック XSD 型に対してサポートされています。 ただしのサブタイプ**xs:duration**が含まれている**xdt:yearMonthDuration と xdt:dayTimeDuration**、および**xs:QName**、 **xs:NMTOKEN**、および**xs:NOTATION**はサポートされていません。 関連するスキーマ コレクションで利用可能なユーザー定義のアトミック型も使用できます。ただし、それらは次に示す型から直接または間接的に派生されている必要があります。  
  
#### <a name="supported-base-types"></a>サポートされている基本データ型  
 サポートされている基本データ型を次に示します。  
  
-   xs:string  
  
-   xs:boolean  
  
-   xs:decimal  
  
-   xs:float  
  
-   xs:double  
  
-   xs:duration  
  
-   xs:dateTime  
  
-   xs:time  
  
-   xs:date  
  
-   xs:gYearMonth  
  
-   xs:gYear  
  
-   xs:gMonthDay  
  
-   xs:gDay  
  
-   xs:gMonth  
  
-   xs:hexBinary  
  
-   xs:base64Binary  
  
-   xs:anyURI  
  
#### <a name="supported-derived-types"></a>サポートされている派生型  
 サポートされている派生型を次に示します。  
  
-   xs:normalizedString  
  
-   xs:token  
  
-   xs:language  
  
-   xs:Name  
  
-   xs:NCName  
  
-   xs:ID  
  
-   xs:IDREF  
  
-   xs:ENTITY  
  
-   xs:integer  
  
-   xs:nonPositiveInteger  
  
-   xs:negativeInteger  
  
-   xs:long  
  
-   xs:int  
  
-   xs:short  
  
-   xs:byte  
  
-   xs:nonNegativeInteger  
  
-   xs:unsignedLong  
  
-   xs:unsignedInt  
  
-   xs:unsignedShort  
  
-   xs:unsignedByte  
  
-   xs:positiveInteger  
  
 SQL Server では、次に示す方法で、コンストラクター関数の呼び出しの際に定数の組み合わせもサポートしています。  
  
-   引数が文字列リテラルの場合、式はコンパイル時に評価されます。 値が型に関する制約を満たしていない場合、静的エラーが発生します。  
  
-   引数が別の型のリテラルである場合、式はコンパイル時に評価されます。 値が型に関する制約を満たしていない場合、空のシーケンスが返されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-datetime-xquery-function-to-retrieve-older-product-descriptions"></a>A. dateTime() XQuery 関数を使用して、製品の説明の古いバージョンを取得する  
 この例ではサンプルの XML ドキュメントが最初に割り当てられた、 **xml**型の変数です。 このドキュメントには 3 つのサンプル <`ProductDescription`> 要素が含まれます。各要素には <`DateCreated`> 子要素が含まれています。  
  
 次に、その変数がクエリされ、指定された日時より前に作成された製品の説明だけを取得します。 比較の目的で、クエリを使用して、 **xs:dateTime()** コンス トラクター関数を日付を入力します。  
  
```  
declare @x xml  
set @x = '<root>  
<ProductDescription ProductID="1" >  
  <DateCreated DateValue="2000-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
<ProductDescription  ProductID="2" >  
  <DateCreated DateValue="2001-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
<ProductDescription ProductID="3" >  
  <DateCreated DateValue="2002-01-01T00:00:00Z" />  
  <Summary>Some Summary description</Summary>  
</ProductDescription>  
</root>'  
  
select @x.query('  
     for $PD in  /root/ProductDescription  
     where xs:dateTime(data( ($PD/DateCreated/@DateValue)[1] )) < xs:dateTime("2001-01-01T00:00:00Z")  
     return  
        element Product  
       {   
        ( attribute ProductID { data($PD/@ProductID ) },  
        attribute DateCreated { data( ($PD/DateCreated/@DateValue)[1] ) } )  
        }  
 ')  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   FOR ... WHERE ループ構造を使用して、取得、 \<ProductDescription > WHERE 句で指定された条件を満たす要素。  
  
-   **DateTime()** コンス トラクター関数を構築するために使用**dateTime**適切に比較できるように、値を入力します。  
  
-   この後、クエリは結果の XML を出力します。 一連の属性を構成しているため、XML の構造にコンマとかっこが使用されています。  
  
 結果を次に示します。  
  
```  
<Product   
   ProductID="1"   
   DateCreated="2000-01-01T00:00:00Z"/>  
```  
  
## <a name="see-also"></a>参照  
 [XML の構築&#40;XQuery&#41;](../xquery/xml-construction-xquery.md)   
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
