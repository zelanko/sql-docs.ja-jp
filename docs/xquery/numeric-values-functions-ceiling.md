---
title: ceiling 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:ceiling function
- ceiling function [XQuery]
ms.assetid: 594f1dd0-3c27-41b3-b809-9ce6714c5a97
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a26fda3dc3edc1870b7a587d926d8e26d69f186e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667921"
---
# <a name="numeric-values-functions---ceiling"></a>数値関数 - ceiling 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  引数の値以上で、小数部を含まない最小の数値を返します。 引数が空のシーケンスの場合は、空のシーケンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:ceiling ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 関数を適用する数値。  
  
## <a name="remarks"></a>コメント  
 場合の種類 *$arg*は 3 つの数値基本データ型の 1 つ**xs:float**、 **xs:double**、または**xs:decimal**と同じ戻り値の型です *$arg*型。  
  
 場合の種類 *$arg* 、数値型のいずれかから派生した型は、戻り値の型が基本の数値型。  
  
 Fn:floor、fn:ceiling、または fn:round 関数への入力は場合**xdt:untypedAtomic**に暗黙的にキャストされた**xs:double**します。  
  
 その他の型のデータが入力されると、静的エラーが生成されます。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-using-the-ceiling-xquery-function"></a>A. ceiling() XQuery 関数の使用  
 次のクエリは、製品モデル 7 の製造にかかわりのあるワーク センターの場所一覧を返します。 ワーク センターの場所ごとに、場所 ID、労働時間、ロット サイズのデータが記録されている場合、これを返します。 クエリを使用して、 **ceiling**を労働時間を型の値を返す関数を**decimal**します。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
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
  
-   **手順については**は、 **xml**型の列。 そのため、 [query() メソッド (XML データ型)](../t-sql/xml/query-method-xml-data-type.md) XQuery を指定するために使用します。 query メソッドの引数には XQuery ステートメントを指定しています。  
  
-   **... 返す**はループ構造体です。 クエリで、**の**ループの一覧を識別する\<場所 > 要素。 各ワーク センター拠点の**返す**内のステートメント、**の**ループが生成される XML について説明します。  
  
    -   A\<場所 > を LocationID 属性と LaborHrs 属性を持つ要素。 中かっこ ({ }) 内の対応する式により、必要な値をドキュメントから取得しています。  
  
    -   {0} $i/@LotSize } 式が存在する場合、ドキュメントから LotSize 属性を取得します。  
  
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
  
-   **Ceiling()** 関数では、すべての整数値を xs:decimal にマップします。  
  
## <a name="see-also"></a>参照  
 [floor 関数&#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [round 関数&#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)  
  
  
