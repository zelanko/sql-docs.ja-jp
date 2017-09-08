---
title: "count 関数 (XQuery) |Microsoft ドキュメント"
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
- fn:count function
- count function [XQuery]
ms.assetid: a9f7131f-23e1-4d4d-a36c-180447543926
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be2b9f8f359e5325e7f1f40a062b45499b05b1c3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="aggregate-functions---count"></a>集計関数の数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  指定されたシーケンス内に含まれる項目数を返します*$arg*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:count($arg as item()*) as xs:integer  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 カウントするアイテム。  
  
## <a name="remarks"></a>解説  
 場合 0 を返します*$arg*は空のシーケンス。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-count-xquery-function-to-count-the-number-of-work-center-locations-in-the-manufacturing-of-a-product-model"></a>A. count() XQuery 関数を使用して、ある製品モデルを製造するワーク センターの場所の数をカウントする  
 次のクエリでは、ある製品モデル (ProductModelID=7) の製造プロセスでのワーク センターの場所の数をカウントします。  
  
```  
SELECT Production.ProductModel.ProductModelID,   
       Production.ProductModel.Name,   
       Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations>  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID=7  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **名前空間**キーワード[XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)名前空間プレフィックスを定義します。 このプレフィックスは XQuery の本文で使用されます。  
  
-   <`NoOfWorkStations`> 要素を含んだ XML が構成されます。  
  
-   **Count()**関数の数、XQuery の本文のカウント <`Location`> 要素。  
  
 結果を次に示します。  
  
```  
ProductModelID   Name                 WorkCtrCount       
-------------- ---------------------------------------------------  
7             HL Touring Frame  <NoOfWorkStations>6</NoOfWorkStations>     
```  
  
 次のクエリで示すように、製品モデルの ID および名前を含むように XML を構成することもできます。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations  
             ProductModelID= "{ sql:column("Production.ProductModel.ProductModelID") }"   
             ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID= 7  
```  
  
 結果を次に示します。  
  
```  
<NoOfWorkStations ProductModelID="7"   
                  ProductModelName="HL Touring Frame">6</NoOfWorkStations>  
```  
  
 XML 以外にも、次のクエリで示すように xml 以外の型で値を返すことができます。 クエリを使用して、 [value() メソッド (xml データ型)](../t-sql/xml/value-method-xml-data-type.md)作業センターの場所の数を取得します。  
  
```  
SELECT  ProductModelID,   
        Name,   
        Instructions.value('declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
           count(/AWMI:root/AWMI:Location)', 'int' ) as WorkCtrCount  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
ProductModelID    Name            WorkCtrCount  
-------------- ---------------------------------  
7              HL Touring Frame        6     
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
