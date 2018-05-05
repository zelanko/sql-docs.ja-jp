---
title: min 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
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
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:min function
- min function [XQuery]
ms.assetid: db0b7d94-3fa6-488f-96d6-6a9a7d6eda23
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7491ef774ae0664432223af05e89ffdf57788540
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions---min"></a>集計関数の最小値
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  アトミック値のシーケンスを返します *$arg*、1 つの項目の値が他のすべての場合よりも小さいです。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 最小値の取得元になるアイテムのシーケンス。  
  
## <a name="remarks"></a>解説  
 すべての種類に渡されるアトミック値の**min()** 同じ基本型のサブタイプである必要があります。 受け付けられるベースの型をサポートする型は、 **gt**操作します。 この型には、3 つの組み込み数値基本データ型、date/time 基本データ型、xs:string、xs:boolean、および xdt:untypedAtomic が含まれます。 xdt:untypedAtomic 型の値は、xs:double にキャストされます。 これらの型の混在がある場合、またはその他の種類の他の値が渡された場合は、静的エラーが発生します。  
  
 結果**min()** xdt:untypedAtomic の場合は xs:double など、渡された型の基本型を受け取ります。 入力が静的に空の場合は、結果が暗黙的に空になり、静的エラーが返されます。  
  
 **Min()** 関数は、入力シーケンス内の他のよりも小さいする、シーケンスの 1 つの値を返します。 xs:string 値の場合は、既定の Unicode コードポイント照合順序が使用されます。 Xdt:untypedAtomic 値は、xs:double にキャストすることはできない場合、入力シーケンスで値が無視されます。 *$arg*です。 入力が、動的に計算された空のシーケンスである場合は、空のシーケンスが返されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>A. min() XQuery 関数を使用した、労働時間が最も短いワーク センター拠点の検索  
 次のクエリでは、製品モデル (ProductModelID=7) の製造プロセスに含まれるすべてのワーク センター拠点の中から、労働時間が最も短い拠点を取得します。 通常、次に示すように 1 つの拠点が返されます。 複数の拠点の労働時間が等しく最短である場合は、これらの拠点がすべて返されます。  
  
```  
select ProductModelID, Name, Instructions.query('  
  declare namespace AWMI=  
    "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  for   $Location in /AWMI:root/AWMI:Location  
  where $Location/@LaborHours =  
          min( /AWMI:root/AWMI:Location/@LaborHours )  
return  
  <Location WCID=     "{ $Location/@LocationID }"   
              LaborHrs= "{ $Location/@LaborHours }" />  
  ') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **名前空間**XQuery プロローグ内のキーワードは、名前空間プレフィックスを定義します。 このプレフィックスは、XQuery の本文で使用されます。  
  
 XQuery の本文を持つ XML の構築、\<場所 >; WCID を持つ要素および**LaborHrs**属性。  
  
-   クエリでは、ProductModelID 値と名前の値も取得されます。  
  
 結果を次に示します。  
  
```  
ProductModelID   Name              Result  
---------------  ----------------  ---------------------------------  
7                HL Touring Frame  <Location WCID="45" LaborHrs="0.5"/>   
```  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Min()** 関数では、すべての整数値を xs:decimal にマップします。  
  
-   **Min()** xs:duration 型の値に対して関数がサポートされていません。  
  
-   基本データ型の境界を超えて複数の型が混在するシーケンスはサポートされません。  
  
-   照合順序を指定する構文オプションはサポートされません。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
