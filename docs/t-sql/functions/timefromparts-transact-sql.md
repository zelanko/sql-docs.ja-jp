---
title: "TIMEFROMPARTS (TRANSACT-SQL) |Microsoft ドキュメント"
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

  返します、**時間**指定された有効桁数を使用して、指定した時間の値。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>引数  
 *1 時間*  
 時間を指定する整数式。  
  
 *1 分*  
 分を指定する整数式。  
  
 *seconds*  
 秒を指定する整数式。  
  
 *分数*  
 小数部分を指定する整数式。  
  
 *有効桁数 (precision)*  
 有効桁数を指定する整数リテラル、**時間**返される値。  
  
## <a name="return-types"></a>戻り値の型  
 **時間 (** *精度* **)**  
  
## <a name="remarks"></a>解説  
 TIMEROMPARTS は、完全に初期化された time 値を返します。 引数が無効な場合は、エラーが発生します。 パラメーターのいずれかが NULL の場合、NULL が返されます。 ただし場合、*精度*引数が null の場合、エラーが発生します。  
  
 *分数*引数によって異なります、*精度*引数。 たとえば場合、*精度*7 では、場合、小数部分はそれぞれが 100 ナノ秒を表す*精度*3 では、小数部分はそれぞれ 1 ミリ秒を表します。 場合の値*精度*がゼロの値*分数*もする必要がありますゼロです。 それ以外の場合、エラーが発生します。  
  
 この関数は、リモート処理は実行[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]サーバー以上です。 前のバージョンのサーバーにリモート処理は実行できない[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]です。  
  
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
 次の例での使用、*分数*と*精度*パラメーター。  
  
1.  ときに*分数*5 の値を持つと*精度*しの値の 1 の値を持つ*分数*5/10 秒を表します。  
  
2.  ときに*分数*50 の値を持つと*精度*しの値で、2 の値を持つ*分数*50/100 秒を表します。  
  
3.  ときに*分数*500 の値を持つと*精度*しの値の第 3 の値を持つ*分数*秒の 500/1000 を表します。  
  
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
  

