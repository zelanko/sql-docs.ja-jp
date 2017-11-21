---
title: "decimal および numeric (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c6c8ec4ea2255e8496b6e5ed464fbff220d270e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="decimal-and-numeric-transact-sql"></a>decimal 型と numeric 型 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

固定長の有効桁数と小数点以下桁数を持つ数値データ型です。 Decimal および numeric シノニムし、同じ意味で使用できます。
  
## <a name="arguments"></a>引数  
**10 進**[ **(***p*[ **、***s*] **)**] と**数値**[ **(***p*[ **、***s*] **)**]  
固定長の有効桁数と小数点以下桁数を持つ数値です。 最大有効桁数を使用した場合、有効値は - 10^38 +1 ～ 10^38 - 1 です。 ISO シノニム**decimal**は**dec**と**年 12 月 (***p*、 *s***)**. **数値**は機能的に等価**decimal**です。
  
p (precision)  
小数点の右側および左側にある保存される最大文字 (数字) 数の合計です。 有効桁数の値は、1 ～ 38 (最大有効桁数) にする必要があります。 既定の有効桁数は 18 です。
  
> [!NOTE]  
>  Informatica では、有効桁数と小数点以下桁数の指定に関係なく、16 の有効桁数のみサポートされます。  
  
*s* (小数点以下桁数)  
小数点の右側にある保存される文字 (数字) 数です。 この数値を減算*p*を小数点の左側にある数字の最大数を決定します。 小数点の右側にある保存できる最大文字 (数字) 数です。 小数点以下桁数は 0 ~ 値である必要があります*p*です。 小数点以下桁数は、有効桁数が指定された場合にのみ指定できます。 既定のスケールは 0 になります。したがって、0 < = *s* \< =  *p*です。 ストレージの最大サイズは有効桁数によって異なります。
  
|有効桁数|ストレージのバイト サイズ|  
|---|---|
|1 - 9|5|  
|10-19|9|  
|20-28|13|  
|29-38|17|  
  
> [!NOTE]  
>  Informatica (SQL Server PDW Informatica コネクタを介して接続されている) は、有効桁数と小数点以下桁数の指定に関係なく、16 桁のみをサポートします。  
  
## <a name="converting-decimal-and-numeric-data"></a>Decimal および numeric のデータを変換します。
**Decimal**と**数値**データ型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別のデータ型としての有効桁数と小数点以下桁数の特定の各組み合わせと見なされます。 たとえば、 **decimal(5,5)**と**decimal(5,0)**は異なるデータ型と見なされます。
  
[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、小数点付きの定数が自動的に変換に、**数値**データ値、最小有効桁数を使用して、必要なスケールします。 たとえば、定数 12.345 に変換は、**数値**5 の有効桁数と小数点以下桁数は 3 を持つ値です。
  
変換**decimal**または**数値**に**float**または**実際**精度の損失が発生することができます。 変換**int**、 **smallint**、 **tinyint**、 **float**、**実際**、 **money**、または**smallmoney**いずれかに**decimal**または**数値**オーバーフローが発生することができます。
  
既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を数値に変換するときに丸め処理を使用して、 **decimal**または**数値**有効桁数と小数点以下桁数が少なく値。 ただし、SET ARITHABORT オプションが ON の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オーバーフローが発生したときにエラーが発生します。 有効桁数と小数点以下桁数が失われただけではエラーは生成されません。
  
浮動小数値または実数値を小数値または数値に変換する場合、小数値が 17 桁を超えることはありません。 すべての浮動小数値 < 5E-18 は常に 0 として変換されます。
  
## <a name="examples"></a>使用例  
次の例を使用してテーブルを作成、 **decimal**と**数値**データ型。  値は各列に挿入され、結果は SELECT ステートメントを使用して返されます。
  
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
[sys.types & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

