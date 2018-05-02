---
title: decimal 型と numeric 型 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- decimal
- decimal_TSQL
- numeric
- numeric_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decimal data type
- decimal data type, about decimal data type
- numeric data type
- numeric data type, about numeric data type
ms.assetid: 9d862a90-e6b7-4692-8605-92358dccccdf
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 629e74bfffef65546c15ea6aa4c3404bbdafa972
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="decimal-and-numeric-transact-sql"></a>decimal 型と numeric 型 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

固定長の有効桁数と小数点以下桁数を持つ数値データ型です。 decimal と numeric は同義であり、どちらを使ってもかまいません。
  
## <a name="arguments"></a>引数  
**decimal**[ **(***p*[ **,***s*] **)**] および **numeric**[ **(***p*[ **,***s*] **)**]  
固定長の有効桁数と小数点以下桁数を持つ数値です。 最大有効桁数を使用した場合、有効値は - 10^38 +1 ～ 10^38 - 1 です。 **decimal** の ISO のシノニムは、**dec** および **dec(***p*, *s***)** です。 **numeric** は機能的には **decimal** と同じです。
  
p (precision)  
小数点の右側および左側にある保存される最大文字 (数字) 数の合計です。 有効桁数の値は、1 ～ 38 (最大有効桁数) にする必要があります。 既定の有効桁数は 18 です。
  
> [!NOTE]  
>  Informatica では、有効桁数と小数点以下桁数の指定に関係なく、16 の有効桁数のみサポートされます。  
  
*s* (scale)  
小数点の右側にある保存される文字 (数字) 数です。 この数値が *p* から差し引かれ、小数点の左側の最大桁数が判別されます。 小数点の右側にある保存できる最大文字 (数字) 数です。 小数点以下桁数は、0 から *p* までの値でなければなりません。 小数点以下桁数は、有効桁数が指定された場合にのみ指定できます。 既定の小数点以下桁数は 0 です。したがって、0 <= *s* \<= *p* になります。 ストレージの最大サイズは有効桁数によって異なります。
  
|有効桁数|ストレージのバイト サイズ|  
|---|---|
|1 - 9|5|  
|10-19|9|  
|20-28|13|  
|29-38|17|  
  
> [!NOTE]  
>  Informatica (SQL Server PDW Informatica コネクタをによって接続されます) は、有効桁数と小数点以下桁数の指定に関係なく、16 桁の有効桁数のみをサポートします。  
  
## <a name="converting-decimal-and-numeric-data"></a>decimal 型データと numeric 型データの変換
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、**decimal** データ型と **numeric** データ型の場合、有効桁数と小数点以下桁数の組み合わせが異なる場合は、異なるデータ型と見なされます。 たとえば、**decimal(5,5)** と **decimal(5,0)** は異なるデータ型と見なされます。
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、小数点の付いた定数は、必要最小限の有効桁数と小数点以下桁数で自動的に **numeric** 型の値に変換されます。 たとえば、定数 12.345 は有効桁数が 5、小数点以下桁数が 3 の **numeric** 型に変換されます。
  
**decimal** または **numeric** から **float** または **real** への変換では、ある程度の有効桁数の損失が発生することがあります。 **int**、**smallint**、**tinyint**、**float**、**real**、**money**、または **smallmoney** から **decimal** または **numeric** への変換では、オーバーフローが発生することがあります。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、既定で、数値を **decimal** 型または **numeric** 型の値に変換する場合、有効桁数と小数点以下桁数が少なくなって丸められます。 ただし、SET ARITHABORT オプションが ON に設定されている場合は、オーバーフローが起こると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はエラーを生成します。 有効桁数と小数点以下桁数が失われただけではエラーは生成されません。
  
浮動小数値または実数値を小数値または数値に変換する場合、小数値が 17 桁を超えることはありません。 すべての浮動小数値 < 5E-18 は常に 0 として変換されます。
  
## <a name="examples"></a>使用例  
次の例では、**decimal** および **numeric** データ型を使用してテーブルを作成します。  値は各列に挿入され、結果は SELECT ステートメントを使用して返されます。
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyDecimalColumn decimal(5,2)  
,MyNumericColumn numeric(10,5)
  
);  
  
GO  
INSERT INTO dbo.MyTable VALUES (123, 12345.12);  
GO  
SELECT MyDecimalColumn, MyNumericColumn  
FROM dbo.MyTable;  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyDecimalColumn                         MyNumericColumn  
--------------------------------------- ---------------------------------------  
123.00                                  12345.12000  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
