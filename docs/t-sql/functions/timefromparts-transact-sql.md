---
title: TIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5e046e203e7ebd5243cdfc6f10948dfd353b2dd3
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  指定された有効桁数を使用して、指定された時刻を表す **time** 値を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>引数  
 *hour*  
 時間を指定する整数式。  
  
 *minute*  
 分を指定する整数式。  
  
 *seconds*  
 秒を指定する整数式。  
  
 *fractions*  
 小数部分を指定する整数式。  
  
 *有効桁数 (precision)*  
 返される **time** 値の有効桁数を指定する整数リテラル。  
  
## <a name="return-types"></a>戻り値の型  
 **time(** *precision* **)**  
  
## <a name="remarks"></a>Remarks  
 TIMEROMPARTS は、完全に初期化された time 値を返します。 引数が無効な場合は、エラーが発生します。 パラメーターのいずれかが NULL の場合、NULL が返されます。 ただし、*precision* 引数が NULL の場合は、エラーが発生します。  
  
 *fractions* 引数によって異なります、 *precision* 引数。 たとえば、*precision* が 7 の場合、小数部分はそれぞれ 100 ナノ秒を表します。*precision* が 3 の場合、小数部分はそれぞれ 1 ミリ秒を表します。 *precision* の値が 0 の場合、*fractions* の値も 0 にする必要があります。そうしないと、エラーが発生します。  
  
 この関数は、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以上のサーバーに対してリモート処理が可能です。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] より前のバージョンのサーバーには、リモート処理は実行できません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. 秒の小数部を使用しない場合の簡単な例  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. 秒の小数部を使用する場合の例  
 以下の例は、*fractions* パラメーターと *precision* パラメーターの使用方法を示しています。  
  
1.  ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
  
2.  ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 50/100 秒を表します。  
  
3.  ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 500/1000 秒を表します。  
  
```sql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  

