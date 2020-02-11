---
title: sum 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sum function [XQuery]
- fn:sum function
ms.assetid: 12288f37-b54c-4237-b75e-eedc5fe8f96d
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e9095fdecf9bdf9782815c8b44c2131313568c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985745"
---
# <a name="aggregate-functions---sum"></a>集計関数 - sum
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  一連の数値の合計を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:sum($arg as xdt:anyAtomicType*) as xdt:anyAtomicType  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 合計を計算するアトミック値のシーケンス。  
  
## <a name="remarks"></a>解説  
 **Sum ()** に渡されるアトミック値のすべての型は、同じ基本型のサブタイプである必要があります。 使用できる基本データ型は、3 つの組み込みの数値基本データ型または xdt:untypedAtomic です。 Xdt: untypedAtomic 型の値は、xs: double にキャストされます。 これらの型が混在している場合、または他の型の他の値が渡された場合は、静的エラーが発生します。  
  
 **Sum ()** の結果は、入力が必要に応じて空のシーケンスであっても、Xdt: untypedAtomic の場合、xs: double など、渡された型の基本型を受け取ります。 入力が静的に空の場合、結果は静的な型および動的な型 xs:integer の 0 になります。  
  
 **Sum ()** 関数は、数値の合計を返します。 Xdt: untypedAtomic 値を xs: double にキャストできない場合、入力シーケンスの値は無視されます ( *$arg*)。 入力が動的に計算された空のシーケンスである場合は、使用されている基本データ型の値0が返されます。  
  
 オーバーフローまたは範囲外の例外が発生したとき、関数は実行時エラーを返します。  
  
## <a name="examples"></a>例  
 このトピックでは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベースのさまざまな**xml**型の列に格納されている xml インスタンスに対して XQuery の例を示します。  
  
### <a name="a-using-the-sum-xquery-function-to-find-the-total-combined-number-of-labor-hours-for-all-work-center-locations-in-the-manufacturing-process"></a>A. sum() XQuery 関数を使用した、製造プロセス内のすべてのワーク センターの場所での合計労働時間の計算  
 次のクエリでは、製造手順が格納されているすべての製品モデルの製造プロセスにおける、すべてのワーク センターの場所での合計労働時間を計算します。  
  
```  
SELECT Instructions.query('         
   declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
  <ProductModel PMID= "{ sql:column("Production.ProductModel.ProductModelID") }"         
  ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >         
   <TotalLaborHrs>         
     { sum(//AWMI:Location/@LaborHours) }         
   </TotalLaborHrs>         
 </ProductModel>         
    ') as Result         
FROM Production.ProductModel         
WHERE Instructions is not NULL         
```  
  
 次に結果の一部を示します。  
  
```  
<ProductModel PMID="7" ProductModelName="HL Touring Frame">  
   <TotalLaborHrs>12.75</TotalLaborHrs>  
</ProductModel>  
<ProductModel PMID="10" ProductModelName="LL Touring Frame">  
  <TotalLaborHrs>13</TotalLaborHrs>  
</ProductModel>  
...  
```  
  
 次のクエリに示すように、結果を XML として返すのではなく、リレーショナル結果を生成するクエリを記述できます。  
  
```  
SELECT ProductModelID,         
        Name,         
        Instructions.value('declare namespace   
      AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
    sum(//AWMI:Location/@LaborHours)', 'float') as TotalLaborHours         
FROM Production.ProductModel         
WHERE Instructions is not NULL          
```  
  
 結果の一部を次に示します。  
  
```  
ProductModelID Name                 TotalLaborHours         
-------------- -------------------------------------------------  
7              HL Touring Frame           12.75                   
10             LL Touring Frame           13                      
43             Touring Rear Wheel         3                       
...  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項は次のとおりです。  
  
-   1つの引数バージョンの**sum ()** のみがサポートされています。  
  
-   入力が動的に計算された空のシーケンスである場合は、xs: integer 型ではなく、使用された基本データ型の値0が返されます。  
  
-   **Sum ()** 関数では、すべての整数が xs: decimal にマップされます。  
  
-   Xs: duration 型の値の**sum ()** 関数はサポートされていません。  
  
-   基本データ型の境界を超えて複数の型が混在するシーケンスはサポートされません。  
  
-   Sum ((xs: double ("INF"), xs: double ("-INF"))) では、ドメインエラーが発生します。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
