---
title: "ceiling 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d950dbbb138160b5f95d0cf026bf09dc0b866a89
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="numeric-values-functions---ceiling"></a>Ceiling の数値の値関数 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  引数の値以上で、小数部を含まない最小の数値を返します。 引数が空のシーケンスの場合は、空のシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:ceiling ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 関数を適用する数値。  
  
## <a name="remarks"></a>解説  
 場合の種類*$arg*は 3 つの数値基本型の 1 つ**xs:float**、 **xs:double**、または**xs:decimal**と同じ戻り値の型です*$arg*型です。  
  
 場合の種類*$arg*数値型のいずれかから派生した型は、戻り値の型は、基本の数値型。  
  
 Fn:floor、fn:ceiling、または fn:round 関数への入力が場合**xdt:untypedAtomic**に暗黙的にキャスト**xs:double**です。  
  
 その他の型のデータが入力されると、静的エラーが生成されます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. ceiling() XQuery 関数の使用  
 次のクエリは、製品モデル 7 の製造にかかわりのあるワーク センターの場所一覧を返します。 ワーク センターの場所ごとに、場所 ID、労働時間、ロット サイズのデータが記録されている場合、これを返します。 クエリを使用して、 **ceiling**を型の値で労働時間を返す関数を**decimal**です。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
     for $i in /AWMI:root/AWMI:Location  
     return   
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ ceiling($i/@LaborHours) }" >  
                    {   
                      $i/@LotSize  
                    }    
       </Location>  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   AWMI 名前空間プレフィックスは、Adventure Works Manufacturing Instructions を表しています。 このプレフィックスは、クエリ対象のドキュメントで使用されるものと同じ名前空間を示しています。  
  
-   **指示**は、 **xml**型の列です。 したがって、 [query() メソッド (XML データ型)](../t-sql/xml/query-method-xml-data-type.md) XQuery を指定するために使用します。 query メソッドの引数には XQuery ステートメントを指定しています。  
  
-   **... 返す**ループ構造体です。 クエリで、**の**ループのリストを識別する\<場所 > の要素。 各ワーク センターの場所の**返す**内のステートメント、**の**ループを生成する XML の説明。  
  
    -   A\<場所 > を LocationID 属性と LaborHrs 属性を持つ要素。 中かっこ ({ }) 内の対応する式により、必要な値をドキュメントから取得しています。  
  
    -   {$i/@LotSize } 式が存在する場合、ドキュメントから LotSize 属性を取得します。  
  
    -   結果を次に示します。  
  
```  
ProductModelID Result    
-------------- ------------------------------------------------------  
7      <Location LocationID="10" LaborHrs="3" LotSize="100"/>  
       <Location LocationID="20" LaborHrs="2" LotSize="1"/>     
       <Location LocationID="30" LaborHrs="1" LotSize="1"/>     
       <Location LocationID="45" LaborHrs="1" LotSize="20"/>  
       <Location LocationID="60" LaborHrs="3" LotSize="1"/>     
       <Location LocationID="60" LaborHrs="4" LotSize="1"/>  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Ceiling()**関数では、すべての整数値を xs:decimal にマップします。  
  
## <a name="see-also"></a>参照  
 [floor 関数と #40 です。XQuery と #41 です。](../xquery/numeric-values-functions-floor.md)   
 [round 関数 & #40 です。XQuery と #41 です。](../xquery/numeric-values-functions-round.md)  
  
  
