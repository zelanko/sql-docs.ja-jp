---
title: "選択@local_variable(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- variable_TSQL
- '@loca_variable'
- '@local'
- variable
- '@loca_variable_TSQL'
- '@local_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- variables [SQL Server], assigning
- SELECT statement [SQL Server], @local_variable
- '@local_variable'
- local variables [SQL Server]
ms.assetid: 8e1a9387-2c5d-4e51-a1fd-a2a95f026d6f
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 56303a563bce3def564fe3b92067eb6f4c6a2177
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="select-localvariable-transact-sql"></a>選択@local_variable(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  式の値をローカル変数を設定します。  
  
 使用することお勧めを変数に割り当てる場合[設定@local_variable ](../../t-sql/language-elements/set-local-variable-transact-sql.md) @ SELECT ではなく*local_variable*です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SELECT { @local_variable { = | += | -= | *= | /= | %= | &= | ^= | |= } expression } 
    [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>引数  
@*local_variable*  
 値を割り当てる宣言された変数です。  
  
{= | += | -= | \*= | /= | %= | &= | ^= | |= }   
右側の値を左側の変数に代入します。  
  
複合代入演算子です。  
  |演算子 (operator) |アクション (action) |   
  |-----|-----|  
  | = | これに続く、式を変数に代入します。 |  
  | += | 追加し、割り当てます |   
  | -= | 減算して代入 |  
  | \*= | 乗算し、割り当てください |  
  | /= | 除算して代入 |  
  | %= | 剰余を割り当てると |  
  | &= | ビットごとの AND と割り当て |  
  | ^= | ビットごとの XOR と割り当て |  
  | \|= | ビットごとの OR と割り当て |  
  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 これには、スカラー サブクエリが含まれます。  
  
## <a name="remarks"></a>解説  
 SELECT @*local_variable*は通常、変数に 1 つの値を返すに使用します。 ただし、*式*名前は、列の複数の値を返すことです。 SELECT ステートメントが複数の値を返した場合は、最後に返された値が変数に割り当てられます。  
  
 SELECT ステートメントが行を返さない場合、変数は現在の値を保ちます。 場合*式*スカラー サブクエリを NULL に変数の値が設定されていないことを返します。  
  
 1 つの SELECT ステートメントで複数のローカル変数を初期化できます。  
  
> [!NOTE]  
>  変数の割り当てを含む SELECT ステートメントを、同時に通常の結果セットの取得に使用することはできません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-use-select-localvariable-to-return-a-single-value"></a>A. Select を使用して@local_variableを 1 つの値を返す  
 次の例では、変数`@var1`が割り当てられている`Generic Name`としてその値。 に対してクエリを`Store`テーブル行が返されなかったため、値が指定されているため`CustomerID`テーブルに存在しません。 変数が保持、`Generic Name`値。  
  
```sql  
-- Uses AdventureWorks    
  
DECLARE @var1 varchar(30);         
SELECT @var1 = 'Generic Name';         
SELECT @var1 = Name         
FROM Sales.Store         
WHERE CustomerID = 1000 ;        
SELECT @var1 AS 'Company Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Company Name  
 ------------------------------  
 Generic Name  
 ```  
  
### <a name="b-use-select-localvariable-to-return-null"></a>B. Select を使用して@local_variablenull を返します  
 次の例では、`@var1` に値を割り当てるのにサブクエリを使用しています。 指定された値ため`CustomerID`が存在しない、サブクエリを返します。 値はありませんし、変数に設定されている`NULL`です。  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @var1 varchar(30)   
SELECT @var1 = 'Generic Name'   
SELECT @var1 = (SELECT Name   
FROM Sales.Store   
WHERE CustomerID = 1000)   
SELECT @var1 AS 'Company Name' ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Company Name  
----------------------------  
NULL  
```  
  
## <a name="see-also"></a>参照  
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
