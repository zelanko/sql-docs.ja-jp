---
title: "数値関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f41ae1e8ad665da3db472941ee47afebefa63dd3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="numeric-functions"></a>数値関数
次の表では、ODBC スカラー関数のセットに含まれている数値の関数について説明します。 呼び出して**SQLGetInfo**で、*情報の種類*する数値関数は、ドライバーでサポートされる SQL_NUMERIC_FUNCTIONS のアプリケーションを決定できます。  
  
 すべての数値関数の戻り値のデータ型を除く ABS、使用できます ROUND、TRUNCATE、記号、FLOOR、関数と CEILING、これと同じデータの値が返されますが、入力パラメーターとして入力します。  
  
 として表される引数*numeric_exp* 、別のスカラー関数の結果の列の名前を指定できますも*数値 litera*l、SQL_NUMERIC、sql _ として基になるデータ型を表すことができます10 進数、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、使用できます、SQL_REAL、または SQL_DOUBLE です。  
  
 として表される引数*float_exp* 、別のスカラー関数の結果の列の名前を指定できますまたは*数値リテラル*、基になるデータ型を使用できますとして表すことができます。  
  
 として表される引数*integer_exp* 、別のスカラー関数の結果の列の名前を指定できますも*数値リテラル*SQL_TINYINT、sql _ として基になるデータ型を表すことができます、SMALLINT、SQL_INTEGER、または SQL_BIGINT します。  
  
 CURRENT_DATE、CURRENT_TIME、CURRENT_TIMESTAMP スカラー関数は、ODBC 3.0 では、sql-92 に合うように追加されました。  
  
|関数|Description|  
|--------------|-----------------|  
|**ABS (** *numeric_exp* **)** (ODBC 1.0)|絶対値を返します。 *numeric_exp*です。|  
|**ACOS (** *float_exp* **)** (ODBC 1.0)|コサインを返します*float_exp*ラジアンの角度で表されます。|  
|**ASIN (** *float_exp* **)** (ODBC 1.0)|逆正弦を返します*float_exp*ラジアンの角度で表されます。|  
|**ATAN (** *float_exp* **)** (ODBC 1.0)|タンジェントを返します*float_exp*ラジアンの角度で表されます。|  
|**ATAN2 (** *float_exp1*、 *float_exp2***)** (ODBC 2.0)|タンジェントを返します、 *x*と*y*によって指定された座標*float_exp1*と*float_exp2*、それぞれの角度で、ラジアンで表されます。|  
|**CEILING (** *numeric_exp* **)** (ODBC 1.0)|大きいか等しいに最小の整数を返します*numeric_exp*です。 戻り値は、入力パラメーターと同じデータ型です。|  
|**COS (** *float_exp* **)** (ODBC 1.0)|コサインを返します*float_exp*ここで、 *float_exp*角度をラジアン単位で表されます。|  
|**COT (** *float_exp* **)** (ODBC 1.0)|コタンジェントの値を返します*float_exp*ここで、 *float_exp*角度をラジアン単位で表されます。|  
|**度 (** *numeric_exp* **)** (ODBC 2.0)|変換された度の数を返します*numeric_exp*ラジアンします。|  
|**EXP (** *float_exp* **)** (ODBC 1.0)|指数値を返します*float_exp*です。|  
|**FLOOR (** *numeric_exp* **)** (ODBC 1.0)|以下に最大の整数を返します*numeric_exp*です。 戻り値は、入力パラメーターと同じデータ型です。|  
|**ログ (** *float_exp* **)** (ODBC 1.0)|自然対数を返します*float_exp*です。|  
|**LOG10 (** *float_exp* **)** (ODBC 2.0)|対数の底が 10 を返します。 *float_exp*です。|  
|**MOD (** *integer_exp1*、 *integer_exp2***)** (ODBC 1.0)|(剰余) の残りの部分を返します*integer_exp1*で割った値*integer_exp2*です。|  
|**PI()** (ODBC 1.0)|浮動小数点値として pi の定数値を返します。|  
|**電源 (** *numeric_exp*、 *integer_exp***)** (ODBC 2.0)|値を返します*numeric_exp*のべき乗に*integer_exp*です。|  
|**ラジアン (** *numeric_exp* **)** (ODBC 2.0)|変換されたラジアン単位の数を返します*numeric_exp*度。|  
|**RAND (**[*integer_exp*]**)** (ODBC 1.0)|使用して、ランダムな浮動小数点値を返します*integer_exp*省略可能なシード値として。|  
|**ROUND (** *numeric_exp*、 *integer_exp***)** (ODBC 2.0)|返します*numeric_exp*に丸められます*integer_exp*小数点の右側に配置します。 場合*integer_exp*が負の値、 *numeric_exp*に丸められます &#124;*integer_exp*(& a) #124; 小数点の左側の桁数。|  
|**記号 (** *numeric_exp* **)** (ODBC 1.0)|符号を示すインジケーターを返す*numeric_exp*です。 場合*numeric_exp* 0、-1 未満が返されます。 場合*numeric_exp*が 0 に等しい、0 が返されます。 場合*numeric_exp*はゼロより大きく、1 が返されます。|  
|**SIN (** *float_exp* **)** (ODBC 1.0)|サインを返します*float_exp*ここで、 *float_exp*角度をラジアン単位で表されます。|  
|**SQRT (** *float_exp* **)** (ODBC 1.0)|平方根を返します*float_exp*です。|  
|**TAN (** *float_exp* **)** (ODBC 1.0)|タンジェントを返します*float_exp*ここで、 *float_exp*角度をラジアン単位で表されます。|  
|**TRUNCATE (** *numeric_exp*、 *integer_exp***)** (ODBC 2.0)|返します*numeric_exp*に切り捨て*integer_exp*小数点の右側に配置します。 場合*integer_exp*が負の値、 *numeric_exp*に切り捨てられます (& m); #124*integer_exp*(& a) #124; 小数点の左側の桁数。|

