---
title: "DATETIME2FROMPARTS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: f54170fc9f17ff7eb69f5de8cfdf865fd31bd4d8
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

返します、 **datetime2**指定された有効桁数を使用して、指定した日付と時刻の値。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>引数  
*1 年*  
年を指定する整数式。
  
*月*  
月を指定する整数式。
  
*1 日*  
日を指定する整数式。
  
 *1 時間*  
時間を指定する整数式。
  
*分*分を指定する整数式です。
  
*seconds*  
秒を指定する整数式。
  
*分数*  
小数部分を指定する整数式。
  
*有効桁数 (precision)*  
有効桁数を指定する整数リテラル、 **datetime2**返される値。
  
## <a name="return-types"></a>戻り値の型
**datetime2 (** *精度* **)**
  
## <a name="remarks"></a>解説  
**DATETIME2FROMPARTS**返しますが完全に初期化された**datetime2**値。 引数が有効でない場合、エラーが発生します。 必要な引数が NULL の場合は、NULL が返されます。 ただし場合、*精度*引数が null の場合、エラーが発生します。
  
*分数*引数によって異なります、*精度*引数。 たとえば場合、*精度*7 では、場合、小数部分はそれぞれが 100 ナノ秒を表す*精度*3 では、小数部分はそれぞれ 1 ミリ秒を表します。 場合の値*精度*がゼロの値*分数*もする必要がありますゼロです。 それ以外の場合、エラーが発生します。
  
この関数は、リモート処理は実行することのできる[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]サーバー上とします。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] より前のバージョンをインストールしているサーバーには、リモート処理が行われません。
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. 秒の小数部を使用しない場合の簡単な例  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. 秒の小数部を使用する場合の例  
次の例での使用、*分数*と*精度*パラメーター。
  
1.  ときに*分数*5 の値を持つと*精度*しの値の 1 の値を持つ*分数*5/10 秒を表します。  
  
2.  ときに*分数*50 の値を持つと*精度*しの値で、2 の値を持つ*分数*50/100 秒を表します。  
  
3.  ときに*分数*500 の値を持つと*精度*しの値の第 3 の値を持つ*分数*秒の 500/1000 を表します。  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  


