---
title: "float 型と real (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: dd20fe12af6f1dcaf378d737961bc2ba354aabe5
ms.openlocfilehash: 0ce2e3272c30057f533796e0822256c6235de0c1
ms.contentlocale: ja-jp
ms.lasthandoff: 10/04/2017

---
# <a name="float-and-real-transact-sql"></a>float 型と real 型 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

浮動小数点数値データで使用する概数型です。 浮動小数点データは概数であるため、データ型の範囲に含まれるすべての値を正確に表せるわけではありません。 ISO シノニムは、**実際**は**float (24)**です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
**float** [ **(***n***)** ] 場所 *n* の格納に使用されるビット数は、仮数、 **float**科学的表記法で数値と、そのため、有効桁数およびストレージのサイズに影響します。 場合 *n* の間の値をする必要があります指定**1**と**53**です。 既定値の *n* は**53**です。
  
|*n*値|有効桁数|ストレージのサイズ|  
|---|---|---|
|**1-24**|7 桁の数字|4 バイト|  
|**25-53**|15 桁|8 バイト|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]扱います *n* として 2 つの値のいずれか。 場合**1**<=n<=**24**、  *n* として扱われる**24**です。 場合**25**<=n<=**53**、  *n* として扱われる**53**です。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Float**[**(n)**] データ型は、のすべての値、ISO 標準に準拠している *n* から**1**を通じて**53**です。 シノニムは、**有効桁数を 2 倍**は**float (53)**です。
  
## <a name="remarks"></a>解説  
  
|データ型|範囲|ストレージ|  
|---|---|---|
|**float**|- 1.79E+308 ～ -2.23E-308、0、および 2.23E-308 ～ 1.79E+308|値に依存します。*n*|  
|**real**|- 3.40E+38 ～ -1.18E-38、0、および 1.18E-38 ～ 3.40E+38|4 バイト|  
  
##  <a name="converting-float-and-real-data"></a>浮動小数点数と実際のデータの変換  
値**float**任意の整数型への変換時に切り捨てられます。
  
変換するときに**float**または**実際**を文字データ、CAST () よりも便利な通常は、STR 文字列関数を使用します。 これは、STR 関数の方がより柔軟に形式を制御できるためです。 詳細については、次を参照してください。 [STR & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/str-transact-sql.md)と[関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/functions.md).
  
変換**float**値を科学的表記法を使用する**decimal**または**数値**17 桁のみを有効桁数の値に制限されます。 任意の値 < 5e-18 が 0 に切り捨てです。
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  

