---
title: "STR (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STR
- STR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- converting numbers to characters
- characters [SQL Server], converting
- character data [SQL Server]
- STR function
ms.assetid: de03531b-d9e7-4c3c-9604-14e582ac20c6
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 7cddf1af7eba56824e41ad1ebaedb9aecdc37074
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="str-transact-sql"></a>STR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  数値データから変換された文字データを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STR ( float_expression [ , length [ , decimal ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *float_expression*  
 概数型の式です (**float**) 小数点付きのデータ型。  
  
 *length*  
 全体の長さを指定します。 これには小数点、負号、数字、空白文字も含まれます。 既定値は、10 です。  
  
 *decimal*  
 小数点以下の桁数を指定します。 *10 進*16 以下である必要があります。 場合*decimal* 16 を超える場合、結果は小数点の右側に 16 桁に切り捨てられます。  
  
## <a name="return-types"></a>戻り値の型  
 **varchar**  
  
## <a name="remarks"></a>解説  
 指定した場合、値を*長さ*と*decimal* STR には正の値にする必要があります。 数は、既定値または 0 は、10 進数のパラメーターが整数に丸められます。 指定する長さは、その数字の小数点より前の桁数に、符号があればその符号部分を加えた数以上にする必要があります。 短い*float_expression*は右揃えの指定した長さと、時間の長い*float_expression*は指定された小数点以下桁数に切り捨てられます。 たとえば、STR (12**、**10) は 12 の結果を生成します。 これは結果セットの中で右揃えされます。 ただし、STR (1223**、**2) に結果セットを切り捨てます。 * *。 文字列関数は入れ子にすることができます。  
  
> [!NOTE]  
>  Unicode データに変換する場合、変換中で STR を使用または[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)変換関数。  
  
## <a name="examples"></a>使用例  
 次の例では、5 つの数字と小数点で構成される式を、6 桁の文字列に変換します。 値の小数部は、小数点以下 1 桁になるように丸められます。  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 返される文字列に指定された長さを超えると、式`**`指定された長さに対してです。  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 `STR` の中で数値データが入れ子にされていても、結果は指定した形式の文字データになります。  
  
```  
SELECT STR (FLOOR (123.45), 8, 3;)  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


