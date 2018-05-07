---
title: substring 関数 (XQuery) |Microsoft ドキュメント
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
- substring function [XQuery]
- fn:substring function
ms.assetid: 2b3b8651-de51-46dc-af82-c86c45eac871
caps.latest.revision: 42
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4bf01599d3144ca6eb3ebbfa74435ab16b25176a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="functions-on-string-values---substring"></a>文字列値の部分文字列に関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  値の一部を返します *$sourceString*の値で示される位置から *$startingLoc、*しの値で示される文字数の続行 *$長さ*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc  as as xs:decimal?) as xs:string?  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?,  
                          $length as xs:decimal?) as xs:string?  
```  
  
## <a name="arguments"></a>引数  
 *$sourceString*  
 取得対象の文字列です。  
  
 *$startingLoc*  
 取得対象文字列中で取得を開始する場所を示します。 この値が負の値や 0 の場合、0 より後の位置にある文字のみが返されます。 長さより大きい場合に、 *$sourceString*、長さゼロの文字列が返されます。  
  
 *$length*  
 [オプション] 取得する文字数です。 指定された場所からすべての文字を返します、指定しない場合、 *$startingLoc*文字列の末尾までです。  
  
## <a name="remarks"></a>解説  
 この関数で引数を 3 つとも指定した場合、`$sourceString` 内で、次の範囲内の位置 `$p` から文字列が返されます。  
  
 `fn:round($startingLoc) <= $p < fn:round($startingLoc) + fn:round($length)`  
  
 値 *$length*の値の文字数よりも大きくすることは *$sourceString*開始位置以降します。 この場合、部分文字列がの末尾までの文字を返します *$sourceString*です。  
  
 文字列の最初の文字の位置は 1 です。  
  
 場合の値 *$sourceString*空のシーケンスでは、長さゼロの文字列として扱われます。 それ以外の場合は、いずれか *$startingLoc*または *$length*空のシーケンスでは、空のシーケンスが返されます。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 XQuery 関数におけるサロゲート ペアの動作は、データベースの互換性レベルに左右されます。場合によっては、関数の既定の名前空間 URI に左右されることもあります。 詳細については、のトピックでは、「XQuery 関数はサロゲート対応」のセクションを参照して[SQL Server 2016 におけるデータベース エンジン機能の重大な変更](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)です。 参照してください[ALTER DATABASE 互換性レベル&#40;TRANSACT-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)と[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md)です。  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 SQL Server が必要です、 *$startingLoc*と *$length パラメーター*型が xs:double ではなく xs:decimal であります。  
  
 SQL Server では *$startingLoc*と *$length*空のシーケンスが () にマップされる動的エラーの結果として使用可能な値であるため、空のシーケンスであります。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例**xml**内の列を入力、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース。  
  
### <a name="a-using-the-substring-xquery-function-to-retrieve-partial-summary-product-model-descriptions"></a>A. XQuery の substring() 関数を使用して製品モデルの説明の概要の一部を取得する  
 クエリは、製品モデルを説明するテキストの最初の 50 文字の取得、<`Summary`> ドキュメント内の要素。  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Prod>{ substring(string((/pd:ProductDescription/pd:Summary)[1]), 1, 50) }</Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('/pd:ProductDescription')  = 1;  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **String()** 関数の文字列値を返します、<`Summary`> 要素。 この関数を使用、<`Summary`> 要素には、テキストとサブ要素 (html 要素を書式設定、) の両方が含まれています。 これらの要素をスキップし、すべてのテキストを取得するためです。  
  
-   **Substring()** 関数によって取得された文字列値からの最初の 50 文字の取得、 **string()** です。  
  
 これは、結果の一部です。  
  
```  
ProductModelID Result  
-------------- ----------------------------------------------------  
19      <Prod>Our top-of-the-line competition mountain bike.</Prod>   
23      <Prod>Suitable for any type of riding, on or off-roa</Prod>  
...  
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
