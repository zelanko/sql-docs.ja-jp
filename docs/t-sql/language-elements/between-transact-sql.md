---
title: "(TRANSACT-SQL) の間で |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/28/2017
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
- BETWEEN
- BETWEEN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- inclusive ranges
- testing range
- exclusive ranges
- NOT BETWEEN operator
- BETWEEN operator
- range to test [SQL Server]
ms.assetid: a5d5b050-203e-4355-ac85-e08ef5ca7823
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 8ff77a998bba76af8a1fdfb728e613158a5c478b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="between-transact-sql"></a>BETWEEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テスト範囲を指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
test_expression [ NOT ] BETWEEN begin_expression AND end_expression  
```  
  
## <a name="arguments"></a>引数  
 *な任意*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)で定義された範囲内でテストする*で有効*と*式*です。 *な任意*両方と同じデータ型にする必要があります*で有効*と*式*です。  
  
 [NOT]  
 述語の結果を否定することを指定します。  
  
 *有効*  
 有効な式を指定します。 *有効*両方と同じデータ型にする必要があります*な任意*と*式*です。  
  
 *式*  
 有効な式を指定します。 *式*両方と同じデータ型にする必要があります*な任意*と*で有効*です。  
  
 [AND]  
 示すプレース ホルダーとして*な任意*によって示される範囲内である必要があります*で有効*と*式*です。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="result-value"></a>結果の値  
 リターンの間で**TRUE**場合の値*な任意*より大きいかの値に等しい*で有効*の値以下*式*です。  
  
 返します間ではなく**TRUE**場合の値*な任意*がの値より小さい*で有効*かの値より大きい*式。*.  
  
## <a name="remarks"></a>解説  
 両端を除いた範囲を指定するには、より大きいことを表す演算子 (>) と、より小さいことを表す演算子 (<) を使用します。 BETWEEN または NOT BETWEEN の述語に対する入力が NULL の場合、結果は UNKNOWN になります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-between"></a>A. BETWEEN を使用する  
 次の例では、データベースのデータベース ロールに関する情報を返します。 最初のクエリでは、すべてのロールを返します。 2 番目の例では、`BETWEEN`句を指定したロールを制限する`database_id`値。  
  
```sql  
SELECT principal_id, name 
FROM sys.database_principals
WHERE type = 'R';

SELECT principal_id, name 
FROM sys.database_principals
WHERE type = 'R'
AND principal_id BETWEEN 16385 AND 16390;
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]   
```  
principal_id    name
------------  ---- 
0               public
16384           db_owner
16385           db_accessadmin
16386           db_securityadmin
16387           db_ddladmin
16389           db_backupoperator
16390           db_datareader
16391           db_datawriter
16392           db_denydatareader
16393           db_denydatawriter
```  
```  
principal_id    name
------------  ---- 
16385           db_accessadmin
16386           db_securityadmin
16387           db_ddladmin
16389           db_backupoperator
16390           db_datareader
```  
  
### <a name="b-using--and--instead-of-between"></a>B. BETWEEN の代わりに > と < を使用する  
 次の例では、より大きいことを表す演算子 (`>`) と、より小さいことを表す演算子 (`<`) を使用します。どちらも両端を含まないため、前の例の 10 行とは異なり、9 行が返されます。  
  
```sql  
-- Uses AdventureWorks  
  
SELECT e.FirstName, e.LastName, ep.Rate  
FROM HumanResources.vEmployee e   
JOIN HumanResources.EmployeePayHistory ep   
    ON e.BusinessEntityID = ep.BusinessEntityID  
WHERE ep.Rate > 27 AND ep.Rate < 30  
ORDER BY ep.Rate;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 FirstName   LastName             Rate  
 ---------   -------------------  ---------  
 Paula       Barreto de Mattos    27.1394  
 Janaina     Bueno                27.4038  
 Dan         Bacon                27.4038  
 Ramesh      Meyyappan            27.4038  
 Karen       Berg                 27.4038  
 David       Bradley              28.7500  
 Hazem       Abolrous             28.8462  
 Ovidiu      Cracium              28.8462  
 Rob         Walters              29.8462  
 ```    
  
### <a name="c-using-not-between"></a>C. NOT BETWEEN を使用する  
 次の例では、指定した範囲 `27` ～ `30` に該当しないすべての行を検索します。  
  
```sql  
-- Uses AdventureWorks  
  
SELECT e.FirstName, e.LastName, ep.Rate  
FROM HumanResources.vEmployee e   
JOIN HumanResources.EmployeePayHistory ep   
    ON e.BusinessEntityID = ep.BusinessEntityID  
WHERE ep.Rate NOT BETWEEN 27 AND 30  
ORDER BY ep.Rate;  
GO  
```  
  
### <a name="d-using-between-with-datetime-values"></a>D. BETWEEN を datetime 値と共に使用する  
 次の例では、ある行**datetime**値は、`'20011212'`と`'20020105'`、包括的です。  
  
```sql  
-- Uses AdventureWorks  
  
SELECT BusinessEntityID, RateChangeDate  
FROM HumanResources.EmployeePayHistory  
WHERE RateChangeDate BETWEEN '20011212' AND '20020105';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 BusinessEntityID RateChangeDate  
 ----------- -----------------------  
 3           2001-12-12 00:00:00.000  
 4           2002-01-05 00:00:00.000  
 ```  
 
 日付値のクエリであるために、クエリが予測される行を取得し、 **datetime**に格納された値、`RateChangeDate`日付の時刻部分なしの列が指定されています。 時刻部分は、指定されていなければ、既定で午前 12 時になります。 時刻部分として 2002 年 1 月 5 日の午前 12 時よりも後の値が格納されている行は、 2002-01-05 では返されませんこのクエリによって、範囲外になるためです。  
  
  
## <a name="see-also"></a>参照  
 [&#62;です。&#40;です。大きい (& a) #41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/greater-than-transact-sql.md)   
 [(& m); 60&#40;です。小さい (& a) #41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/less-than-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  


