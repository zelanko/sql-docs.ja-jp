---
title: "PERCENTILE_DISC (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERCENTILE_DISC
- PERCENTILE_DISC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PERCENTILE_DISC function
- analytic functions,PERCENTILE_DISC
ms.assetid: b545413d-c4f7-4c8e-8617-607599a26680
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a70610ecc826cda363cc0eea25baf090b24acc08
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="percentiledisc-transact-sql"></a>PERCENTILE_DISC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の行セット全体または行セットの別個のパーティション内で並べ替えられた値の特定の百分位数を計算します。 指定された百分位の値を*P*PERCENTILE_DISC は ORDER BY 句の式の値を並べ替えおよびよりも大きい、(並べ替え仕様は同じ) についての CUME_DIST の最小値を含む値を返しますまたは等しい*P*です。たとえば、PERCENTILE_DISC (0.5) は式の 50 番目の百分位数 (つまり、中央値) を計算します。 PERCENTILE_DISC は、列値の離散型分布に基づく百分位数を計算します。結果は列の特定の値と等しくなります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
PERCENTILE_DISC ( numeric_literal ) WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>引数  
 *リテラル*  
 計算する百分位数です。 値は 0.0 ～ 1.0 で指定してください。  
  
 グループ内で**(** ORDER BY *order_by_expression* [ **ASC** |DESC]**)**  
 並べ替えし、経由で、百分位数を計算する値の一覧を指定します。 1 つだけ*order_by_expression*は許可されています。 既定の並べ替え順は昇順です。 並べ替え操作に対して有効なデータ型のいずれかの値の一覧を指定できます。  
  
 経由で**(** \<partition_by_clause > **)**  
 FROM 句で生成された結果セットをパーティションに分割します。このパーティションにパーセンタイル関数が適用されます。 詳細については、次を参照してください。 [OVER 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-over-clause-transact-sql.md). \<ORDER BY 句 > と\<行または範囲句 > PERCENTILE_DISC 関数で指定することはできません。  
  
## <a name="return-types"></a>戻り値の型  
 戻り値の型によって決定されます、 *order_by_expression*型です。  
  
## <a name="compatibility-support"></a>互換性サポート  
 互換性レベル 110 以上では、WITHIN GROUP は予約されたキーワードです。 詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  
  
## <a name="general-remarks"></a>全般的な解説  
 データセット内の NULL はすべて無視されます。  
  
 PERCENTILE_DISC は非決定的です。 詳細については、「 [決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-basic-syntax-example"></a>A. 基本構文例  
 次の例では、PERCENTILE_CONT と PERCENTILE_DISC を使用して、各部門の従業員給与の中央値を検索します。 これらの関数は同じ値を返さない可能性があります。 これは、データセットに存在するかどうかに関係なく PERCENTILE_CONT では適切な値が挿入されるためですが、PERCENTILE_DISC では常にセットから実際の値を返します。  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 部分的な結果セットを次に示します。  
  
 `DepartmentName        MedianCont    MedianDisc`  
  
 `--------------------   ----------   ----------`  
  
 `Document Control       16.8269      16.8269`  
  
 `Engineering            34.375       32.6923`  
  
 `Executive              54.32695     48.5577`  
  
 `Human Resources        17.427850    16.5865`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-basic-syntax-example"></a>B. 基本構文例  
 次の例では、PERCENTILE_CONT と PERCENTILE_DISC を使用して、各部門の従業員給与の中央値を検索します。 これらの関数は同じ値を返さない可能性があります。 これは、データセットに存在するかどうかに関係なく PERCENTILE_CONT では適切な値が挿入されるためですが、PERCENTILE_DISC では常にセットから実際の値を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
       ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianCont  
       ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 部分的な結果セットを次に示します。  
  
 `DepartmentName        MedianCont    MedianDisc`  
  
 `--------------------   ----------   ----------`  
  
 `Document Control       16.826900    16.8269`  
  
 `Engineering            34.375000    32.6923`  
  
 `Human Resources        17.427850    16.5865`  
  
 `Shipping and Receiving  9.250000     9.0000`  
  
## <a name="see-also"></a>参照  
 [PERCENTILE_CONT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/percentile-cont-transact-sql.md)  
  
  



