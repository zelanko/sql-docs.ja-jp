---
title: "% (剰余) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- modulo
- modulus
- '% (Modulo)'
- '% (Modulus)'
- MOD_TSQL
dev_langs: TSQL
helpviewer_keywords:
- '% (modulo operator)'
- '% (modulus operator)'
- remainder of division operation
- modulo operator (%)
- modulus operator (%)
ms.assetid: f93c662e-f405-486e-bf23-a2d03907b5bd
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 927b993e2b93ef670633ae1594c86178662ebabb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="-modulus-transact-sql"></a>% (剰余) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ある値を別の値で除算した結果の余りを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>引数  
 *dividend*  
 除算される数値式です。 *被除数*は有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)、整数および通貨のデータ型カテゴリ内のデータ型のいずれかのまたは**数値**データ型。  
  
 *divisor*  
 被除数を除算する数値式です。 *除数*、整数および通貨のデータ型カテゴリ内のデータ型のいずれかの有効な式にする必要がありますまたは**数値**データ型。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数のデータ型によって決まります。  
  
## <a name="remarks"></a>解説  
 使用することができます、剰余列名の任意の組み合わせを含む SELECT ステートメントの選択リストでの算術演算子、数値定数、または、整数および通貨のデータの有効な式を入力カテゴリまたは**数値**データ入力します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example"></a>A. 簡単な例  
 次の例では、38 を 5 で割ります。 これは、結果の整数部分としての結果を 7 でおよび例示す方法 modulo 3 の残りの部分を返します。  
  
```  
SELECT 38 / 5 AS Integer, 38 % 5 AS Remainder ;  
  
```  
  
### <a name="b-example-using-columns-in-a-table"></a>B. テーブルの列を使用した例  
 次の例では、製品 ID 番号、製品の単価、および注文された製品数を各製品の価格で割った余り (剰余) を整数値に変換した値を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(100)ProductID, UnitPrice, OrderQty,  
   CAST((UnitPrice) AS int) % OrderQty AS Modulo  
FROM Sales.SalesOrderDetail;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example"></a>C: 簡単な例  
 次の例の結果を示しています、`%`演算子が 3 を 2 を除算したときにします。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) 3%2 FROM dimEmployee;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
1         
```  
  
## <a name="see-also"></a>参照  
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [ような &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [% = &#40;です。剰余代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/modulo-equals-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


