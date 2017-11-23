---
title: "int、bigint、smallint 型、および tinyint (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 9/8/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bigint_TSQL
- smallint
- bigint
- smallint_TSQL
- tinyint_TSQL
- int_TSQL
- int
- tinyint
dev_langs: TSQL
helpviewer_keywords:
- exact numeric data [SQL Server]
- numeric data
- tinyint data type
- int data type
- smallint data type
ms.assetid: 9bda5b0b-2380-4931-a1c8-f362fdefa99b
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2e99ccb97dc5c36f8b7870a042963d6302b3f1eb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="int-bigint-smallint-and-tinyint-transact-sql"></a>int、bigint、smallint、および tinyint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

整数データを使用する実数データ型です。 データベースの容量を節約するには、すべての値を確実に含めることができる最小のデータ型を使用します。 たとえば、255 歳以上である誰に住んでいるために、tinyint は人物の年齢のための十分ななります。 建物として使用できるは、255 年を超えるので tinyint は建物の経過時間のための十分なはできません。
  
|データ型|範囲|ストレージ|  
|---|---|---|
|**bigint**|-2^63 (-9,223,372,036,854,775,808) ～ 2^63-1 (9,223,372,036,854,775,807)|8 バイト|  
|**int**|-2^31 (-2,147,483,648) ～ 2^31-1 (2,147,483,647)|4 バイト|  
|**smallint**|-2^15 (-32,768) ～ 2^15-1 (32,767)|2 バイト|  
|**tinyint**|0 ～ 255|1 バイト|  
  
## <a name="remarks"></a>解説  
**Int**データ型は、主要な整数データ型で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 **Bigint**データ型が使用するための整数値でサポートされている範囲を超える可能性があるときに、 **int**データ型。
  
**bigint**間に位置**smallmoney**と**int**データ型の優先順位表でします。
  
関数を返します**bigint**パラメーター式が場合にのみ、 **bigint**データ型。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]他の整数データ型を自動的に昇格しません (**tinyint**、 **smallint**、および**int**) に**bigint**です。
  
> [!CAUTION]  
>  使用する場合、+、-、 \*、/、% 算術演算子を暗黙的または明示的な変換を実行または**int**、 **smallint**、 **tinyint**、または**bigint**定数値を**float**、**実際**、 **decimal**または**数値**データ型はの規則[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]計算式の結果の有効桁数とデータ型かどうか、クエリが自動かに応じて異なる場合に適用されます。  
>   
>  したがって、クエリで同じ式を使用しても異なる結果が得られることがあります。 クエリが自動でないと、定数値が最初に変換**数値**の有効桁数が指定されたデータ型に変換する前に、定数の値を保持する大規模だけです。 たとえば、定数の値 1 に変換**numeric (1, 0)**、定数値 250 に変換し、 **numeric (3, 0)**です。  
>   
>  定数値が常に変換するクエリが自動、 **numeric (10, 0)**最終的なデータ型に変換する前にします。 / 演算子を使用すると、同様のクエリで結果の型の有効桁数が異なるだけでなく、結果の値も異なる場合があります。 たとえば、式を含む自動クエリの結果値`SELECT CAST (1.0 / 7 AS float)`に収まるように自動パラメーター化クエリの結果は切り捨てられますので、自動ではないの同じクエリの結果値と異なる**numeric (10, 0)**データ型。  
  
## <a name="converting-integer-data"></a>整数型のデータを変換します。
文字のフィールドに収まるように、整数が大きすぎる整数も、文字データ型に暗黙的に変換と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ASCII 文字コード 42、アスタリスク (*) を入力します。
  
2,147, 483,647 に変換よりも大きい整数の定数、 **decimal**データ型ではなく、 **bigint**データ型。 次の例は、しきい値を超えたときに、結果のデータ型変更から、 **int**を**decimal**です。
  
```sql
SELECT 2147483647 / 2 AS Result1, 2147483649 / 2 AS Result2 ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result1      Result2  
1073741823   1073741824.500000  
```  
  
## <a name="examples"></a>使用例  
次の例を使用してテーブルを作成、 **bigint**、 **int**、 **smallint**、および**tinyint**データ型。 値は各列に挿入され、SELECT ステートメントで返されます。
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyBigIntColumn bigint  
,MyIntColumn  int
,MySmallIntColumn smallint
,MyTinyIntColumn tinyint
);  
  
GO  
  
INSERT INTO dbo.MyTable VALUES (9223372036854775807, 2147483647,32767,255);  
 GO  
SELECT MyBigIntColumn, MyIntColumn, MySmallIntColumn, MyTinyIntColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyBigIntColumn       MyIntColumn MySmallIntColumn MyTinyIntColumn  
-------------------- ----------- ---------------- ---------------  
9223372036854775807  2147483647  32767            255  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
