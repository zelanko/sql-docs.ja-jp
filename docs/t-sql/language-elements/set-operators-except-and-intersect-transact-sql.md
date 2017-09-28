---
title: "EXCEPT および INTERSECT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INTERSECT_TSQL
- EXCEPT_TSQL
- INTERSECT
- EXCEPT
dev_langs:
- TSQL
helpviewer_keywords:
- EXCEPT operator [Transact-SQL]
- queries [SQL Server], comparing
- comparing queries
- INTERSECT operator
ms.assetid: b1019300-171a-4a1a-854f-e1e751de3565
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d8bff51308e9b8dbf02066d56b73829bc1658c2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-operators---except-and-intersect-transact-sql"></a>以外の集合演算子のおよび INTERSECT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つのクエリの結果を比較して、個別の行を返します。  
  
 EXCEPT は、左の入力クエリからの行のうち、右の入力クエリから出力されないものを、重複を除去した上で返します。  
  
 INTERSECT は、両方の左辺と右辺の入力クエリ演算子によって出力される個別の行を返します。  
  
 EXCEPT と INTERSECT を使用して 2 つのクエリの結果セットを結合する場合の基本的な規則は、次のとおりです。  
  
-   列の数と順番は、すべてのクエリで同じであること  
  
-   データ型に互換性があること  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
{ <query_specification> | ( <query_expression> ) }   
{ EXCEPT | INTERSECT }  
{ <query_specification> | ( <query_expression> ) }  
```  
  
## <a name="arguments"></a>引数  
 \<*query_specification*> |( \< *query_expression*>)  
 データを返すクエリ定義またはクエリ式を指定します。このデータが、別のクエリ定義またはクエリ式で返されるデータと比較されます。 EXCEPT または INTERSECT 演算の一部である列の定義は同じである必要はありませんが、暗黙的な変換によって比較できる定義であることが必要です。 比較を実行して結果を確認を返すために使用する型がの規則に基づくデータ型が異なる場合、[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)です。  
  
 型が同じで、有効桁数、小数点以下桁数、長さが異なる場合、結果は式の結合と同じ規則に基づいて決定されます。 詳しくは、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」をご覧ください。  
  
 クエリ仕様または式を返すことはできません**xml**、**テキスト**、 **ntext**、**イメージ**、またはバイナリ以外の CLR ユーザー定義型列これらのデータ型が同等でないためです。  
  
 EXCEPT  
 右のクエリからも返されない、EXCEPT 演算子の左側には、クエリから個別の値を返します。  
  
 INTERSECT  
 INTERSECT 演算子の左右両方のクエリによって返される個別の値を返します。  
  
## <a name="remarks"></a>解説  
 規則に従って、必要な比較が実行される場合、EXCEPT の右側と左側に、クエリによって返される比較可能な列のデータ型または INTERSECT 演算子は照合順序が異なる文字データ型、 [照合順序の優先順位](../../t-sql/statements/collation-precedence-transact-sql.md)です。 この変換が実行できない場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ではエラーが返されます。  
  
 DISTINCT 行を決定するために列の値を比較するとき、2 つの NULL 値は等しいと見なされます。  
  
 EXCEPT または INTERSECT で返される結果セットの列名は、演算子の左のクエリで返されるものと同じ名前になります。  
  
 ORDER BY 句の列名または列の別名は、左のクエリで返される列名を参照している必要があります。  
  
 EXCEPT または INTERSECT で返される結果セットの列で NULL 値が許容されるかどうかは、演算子の左のクエリで返される対応する列の設定と同じになります。  
  
 EXCEPT または INTERSECT を、他の演算子と共に 1 つの式で使用する場合、評価は次の優先順で行われます。  
  
1.  かっこで囲まれた式  
  
2.  INTERSECT 演算子  
  
3.  EXCEPT と UNION (式の中の位置に基づいて、左から右の順に評価)  
  
 EXCEPT または INTERSECT を使用して 2 つ以上のクエリのセットを比較する場合、データ型の変換は、2 つのクエリを一度比較し、前に説明した式の評価の規則に従って決定されます。  
  
 EXCEPT と INTERSECT は、分散パーティション ビュー定義やクエリ通知では使用できません。  
  
 EXCEPT と INTERSECT は分散クエリで使用できますが、この場合ローカル サーバーでのみ実行され、リンク サーバーにはプッシュされません。 したがって、EXCEPT と INTERSECT を分散クエリで使用すると、パフォーマンスに影響が生じる可能性があります。  
  
 高速順方向専用カーソルと静的カーソルを、EXCEPT または INTERSECT 演算で使用した場合、これらのカーソルは結果セットで完全にサポートされます。 キーセットドリブン カーソルまたは動的カーソルを、EXCEPT または INTERSECT 演算で使用した場合、演算の結果セットのカーソルは静的カーソルに変換されます。  
  
 EXCEPT 演算がグラフィカルなプラン表示機能を使用して表示される場合[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、として、操作が表示されます、[左反半結合](../../relational-databases/showplan-logical-and-physical-operators-reference.md)、として、INTERSECT 演算が表示され、[左半結合](../../relational-databases/showplan-logical-and-physical-operators-reference.md)です。  
  
## <a name="examples"></a>使用例  
 次の例を使用して、`INTERSECT`と`EXCEPT`演算子。 最初のクエリからのすべての値を返します、`Production.Product`された結果との比較表`INTERSECT`と`EXCEPT`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product ;  
--Result: 504 Rows  
```  
  
 次のクエリは、左辺と右辺の両方のクエリによって返される個別の値を返します、`INTERSECT`演算子。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
INTERSECT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 238 Rows (products that have work orders)  
```  
  
 次のクエリでは、クエリから個別の値を返しますの左側に、`EXCEPT`上、右のクエリにも存在しない演算子。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
EXCEPT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 266 Rows (products without work orders)  
```  
  
 次のクエリでは、クエリから個別の値を返しますの左側に、`EXCEPT`上、右のクエリにも存在しない演算子。 テーブルは、前の例と逆になります。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.WorkOrder  
EXCEPT  
SELECT ProductID   
FROM Production.Product ;  
--Result: 0 Rows (work orders without products)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、`INTERSECT` 演算子と `EXCEPT` 演算子の使用方法を示しています。 最初のクエリからのすべての値を返します、`FactInternetSales`された結果との比較表`INTERSECT`と`EXCEPT`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales;  
--Result: 60398 Rows  
```  
  
 次のクエリは、左辺と右辺の両方のクエリによって返される個別の値を返します、`INTERSECT`演算子。  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
INTERSECT   
SELECT CustomerKey   
FROM DimCustomer   
WHERE DimCustomer.Gender = 'F'  
ORDER BY CustomerKey;  
--Result: 9133 Rows (Sales to customers that are female.)  
```  
  
 次のクエリでは、クエリから個別の値を返しますの左側に、`EXCEPT`上、右のクエリにも存在しない演算子。  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
EXCEPT   
SELECT CustomerKey   
FROM DimCustomer   
WHERE DimCustomer.Gender = 'F'  
ORDER BY CustomerKey;  
--Result: 9351 Rows (Sales to customers that are not female.)  
```  
  
  


