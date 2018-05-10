---
title: float 型と real 型 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7a9980c471f81b00f4011b449a1dfcaf9a1f5c98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="float-and-real-transact-sql"></a>float 型と real 型 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

浮動小数点数値データで使用する概数型です。 浮動小数点データは概数であるため、データ型の範囲に含まれるすべての値を正確に表せるわけではありません。 ISO シノニムは、 **実際** は **float (24)** です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
**float** [ **(***n***)** ]。*n* は、科学的表記法で **float** 数の仮数部を格納するために使用されるビット数であるため、精度と格納サイズを指示します。 *n* を指定する場合、**1** から **53** までの値にする必要があります。 *n* の既定値は **53** です。
  
|*n* 値|有効桁数|ストレージのサイズ|  
|---|---|---|
|**1 ～ 24**|7 桁の数字|4 バイト|  
|**25-53**|15 桁|8 バイト|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、*n* は次の 2 つの値のいずれかの値として扱われます。 **1**<=n<=**24** の場合、*n* は **24** として処理されます。 **25**<=n<=**53** の場合、*n* は **53** として処理されます。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float****[(n)]** データ型は、*n* (**1** ～ **53**) のすべての値で ISO 標準に準拠しています。 シノニムは、 有効桁数を **2 倍** は **float (53)** です。
  
## <a name="remarks"></a>Remarks  
  
|データ型|範囲|ストレージ|  
|---|---|---|
|**float**|- 1.79E+308 ～ -2.23E-308、0、および 2.23E-308 ～ 1.79E+308|*n* の値により異なります|  
|**real**|- 3.40E+38 ～ -1.18E-38、0、および 1.18E-38 ～ 3.40E+38|4 バイト|  
  
##  <a name="converting-float-and-real-data"></a>float 型データと real 型データの変換  
値を **float** 任意の整数型への変換時に切り捨てられます。
  
変換するときに **float** または **実際** 文字データに、STR 文字列関数を使用する方が CAST () よりも便利です。 これは、STR 関数の方がより柔軟に形式を制御できるためです。 詳細については、「[STR &#40;Transact-SQL&#41;](../../t-sql/functions/str-transact-sql.md)」と「[関数 &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)」を参照してください。
  
変換 **float** 値を科学的表記法を使用する **decimal** または **数値** 17 桁のみを有効桁数の値に制限されます。 5E-18 未満のすべての値は 0 に切り捨てられます。
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
