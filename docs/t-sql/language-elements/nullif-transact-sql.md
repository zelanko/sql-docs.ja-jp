---
title: "NULLIF (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULLIF
- NULLIF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], equivalent expressions
- expressions [SQL Server], null values
- NULLIF function
- equivalent expressions [SQL Server]
ms.assetid: 44c7b67e-74c7-4bb9-93a4-7a3016bd2feb
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8e4663688ce510d9600ebeba9d3c30703ee3aa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="nullif-transact-sql"></a>NULLIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定された 2 つの式が等しい場合に NULL 値を返します。 たとえば、 `SELECT NULLIF(4,4) AS Same, NULLIF(5,7) AS Different;` 2 つの入力値が同じなので、(4 および 4) は、最初の列の NULL を返します。 2 番目の列は、2 つの入力値が異なるために、最初の値 (5) を返します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
NULLIF ( expression , expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 任意の有効なスカラー[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
## <a name="return-types"></a>戻り値の型  
 最初と同じ型を返します*式*です。  
  
 NULLIF は最初を返します*式*2 つの式が等しくない場合。 NULLIF は最初の型の null 値を返しますの式が等しい場合は、*式*です。  
  
## <a name="remarks"></a>解説  
 NULLIF は、2 つの式を比較し、その 2 つが等価な場合に NULL を返す検索 CASE 式と同じです。  
  
 NULLIF 関数の中では、RAND() など時間に依存する関数は使用しないことをお勧めします。 これには、関数に 2 回評価されると、2 つの呼び出しから異なる結果を返す可能性があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-budget-amounts-that-have-not-changed"></a>A. 変更のない予算額を返す  
 次の例を作成、`budgets`部門を表示するテーブル (`dept`)、現在の予算 (`current_year`) とその前の予算 (`previous_year`)。 現在の年の`NULL`は部門に予算が前の年から変更されていないためと`0`予算がまだ決定されていないためです。 平均値を予算を受け取った部門についてだけを検索し、前年度の予算の値を追加する (を使用して、`previous_year`値、場所、`current_year`は`NULL`)、結合、`NULLIF`と`COALESCE`関数。  
  
```sql  
CREATE TABLE dbo.budgets  
(  
   dept            tinyint   IDENTITY,  
   current_year      decimal   NULL,  
   previous_year   decimal   NULL  
);  
INSERT budgets VALUES(100000, 150000);  
INSERT budgets VALUES(NULL, 300000);  
INSERT budgets VALUES(0, 100000);  
INSERT budgets VALUES(NULL, 150000);  
INSERT budgets VALUES(300000, 250000);  
GO    
SET NOCOUNT OFF;  
SELECT AVG(NULLIF(COALESCE(current_year,  
   previous_year), 0.00)) AS 'Average Budget'  
FROM budgets;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Average Budget  
 --------------  
 212500.000000  
 (1 row(s) affected)
 ```  
  
### <a name="b-comparing-nullif-and-case"></a>B. NULLIF と CASE を比較する  
 間の類似性を表示する`NULLIF`と`CASE`、次のクエリを評価するかどうかの値、`MakeFlag`と`FinishedGoodsFlag`列が同じです。 最初のクエリでは `NULLIF` を使用します。 2 番目のクエリでは `CASE` 式を使用します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,   
   NULLIF(MakeFlag,FinishedGoodsFlag)AS 'Null if Equal'  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,'Null if Equal' =  
   CASE  
       WHEN MakeFlag = FinishedGoodsFlag THEN NULL  
       ELSE MakeFlag  
   END  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
```  

### <a name="c-returning-budget-amounts-that-contain-no-data"></a>C: は、データがない予算額を返す  
 次の例を作成、`budgets`テーブル、データを読み込んでを使用して`NULLIF`、どちらの場合、null を返す`current_year`も`previous_year`データが含まれています。  
  
```sql  
CREATE TABLE budgets (  
   dept           tinyint,  
   current_year   decimal(10,2),  
   previous_year  decimal(10,2)  
);  
  
INSERT INTO budgets VALUES(1, 100000, 150000);  
INSERT INTO budgets VALUES(2, NULL, 300000);  
INSERT INTO budgets VALUES(3, 0, 100000);  
INSERT INTO budgets VALUES(4, NULL, 150000);  
INSERT INTO budgets VALUES(5, 300000, 300000);  
  
SELECT dept, NULLIF(current_year,  
   previous_year) AS LastBudget  
FROM budgets;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 dept   LastBudget  
 ----   -----------  
 1      100000.00  
 2      null 
 3      0.00  
 4      null  
 5      null
 ```  
  
## <a name="see-also"></a>参照  
 [場合 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [decimal および numeric 型 &#40;TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


