---
title: EXCEPT および INTERSECT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: b9c519ca1595ed9831a88549bea58d8c16477a3e
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39453236"
---
# <a name="set-operators---except-and-intersect-transact-sql"></a>セット演算子 - EXCEPT および INTERSECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

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
 \<*query_specification*> | ( \<*query_expression*> )  
 データを返すクエリ定義またはクエリ式を指定します。このデータが、別のクエリ定義またはクエリ式で返されるデータと比較されます。 EXCEPT または INTERSECT 演算の一部である列の定義は同じである必要はありませんが、暗黙的な変換によって比較できる定義であることが必要です。 データ型が異なる場合、比較を実行するときと結果を返すときに使用される型は、[データ型の優先順位の規則](../../t-sql/data-types/data-type-precedence-transact-sql.md)に基づいて決定されます。  
  
 型が同じで、有効桁数、小数点以下桁数、長さが異なる場合、結果は式の結合と同じ規則に基づいて決定されます。 詳しくは、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」をご覧ください。  
  
 **xml**、**text**、**ntext**、**image**、またはバイナリ以外の CLR ユーザー定義型の列は比較できないため、クエリ定義またはクエリ式では返されません。  
  
 EXCEPT  
 右のクエリからも返されない、EXCEPT 演算子の左側には、クエリから個別の値を返します。  
  
 INTERSECT  
 INTERSECT 演算子の左右両方のクエリによって返される個別の値を返します。  
  
## <a name="remarks"></a>Remarks  
 EXCEPT または INTERSECT 演算子の左と右のクエリで返される比較可能な列のデータ型が、照合順序の異なる文字データ型の場合は、[照合順序の優先順位](../../t-sql/statements/collation-precedence-transact-sql.md)の規則に基づいて、必要な比較が実行されます。 この変換が実行できない場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ではエラーが返されます。  
  
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
  
 EXCEPT 演算が、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のグラフィカル プラン表示機能を使用して表示される場合、この演算は [left anti semi join](../../relational-databases/showplan-logical-and-physical-operators-reference.md) として表示され、INTERSECT 演算は [left semi join](../../relational-databases/showplan-logical-and-physical-operators-reference.md) として表示されます。  
  
## <a name="examples"></a>使用例  
 次の例は、`INTERSECT` 演算子と `EXCEPT` 演算子の使用方法を示しています。 最初のクエリでは、`INTERSECT` および `EXCEPT` の結果と比較するため、`Production.Product` テーブルからすべての値を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product ;  
--Result: 504 Rows  
```  
  
 次のクエリでは、`INTERSECT` 演算子の左右両方のクエリによって返される個別の値が返されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
INTERSECT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 238 Rows (products that have work orders)  
```  
  
 次のクエリでは、`EXCEPT` 演算子の左のクエリにあって、右のクエリにない個別の値が返されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
EXCEPT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 266 Rows (products without work orders)  
```  
  
 次のクエリでは、`EXCEPT` 演算子の左のクエリにあって、右のクエリにない個別の値が返されます。 テーブルは、前の例と逆になります。  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.WorkOrder  
EXCEPT  
SELECT ProductID   
FROM Production.Product ;  
--Result: 0 Rows (work orders without products)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、`INTERSECT` 演算子と `EXCEPT` 演算子の使用方法を示しています。 最初のクエリでは、`INTERSECT` および `EXCEPT` の結果と比較するため、`FactInternetSales` テーブルからすべての値を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales;  
--Result: 60398 Rows  
```  
  
 次のクエリでは、`INTERSECT` 演算子の左右両方のクエリによって返される個別の値が返されます。  
  
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
  
 次のクエリでは、`EXCEPT` 演算子の左のクエリにあって、右のクエリにない個別の値が返されます。  
  
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
  
  

