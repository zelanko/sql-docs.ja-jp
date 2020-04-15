---
title: 数値関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 03da5b6644e0f7df3dc4e5e16a211cb503023bad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299872"
---
# <a name="numeric-functions"></a>数値関数
次の表は、ODBC スカラー関数セットに含まれる数値関数を示しています。 *情報型*SQL_NUMERIC_FUNCTIONSで**SQLGetInfo**を呼び出すことで、アプリケーションは、ドライバーでサポートされている数値関数を決定できます。  
  
 すべての数値関数は、入力パラメーターと同じデータ型の値を返す ABS、ROUND、TRUNCATE、符号、FLOOR、および CEILING を除き、データ型の値をSQL_FLOAT返します。  
  
 *numeric_exp*として示される引数は、列の名前、別のスカラー関数の結果、または基になるデータ型をSQL_NUMERIC、SQL_DECIMAL、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_FLOAT、SQL_REAL、またはSQL_DOUBLEとして表すことができる*数値の l*です。  
  
 *float_exp*として示される引数は、列の名前、別のスカラー関数の結果、または基になるデータ型をSQL_FLOATとして表すことができる*数値リテラル*です。  
  
 *integer_exp*として示される引数は、列の名前、別のスカラー関数の結果、または基になるデータ型をSQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、またはSQL_BIGINTとして表すことができる*数値リテラル*です。  
  
 CURRENT_DATE、CURRENT_TIME、CURRENT_TIMESTAMPスカラー関数が ODBC 3.0 で追加され、SQL-92 に合わせて調整されました。  
  
|機能|説明|  
|--------------|-----------------|  
|**ABS(** _numeric_exp_ **)** (ODBC 1.0)|*numeric_exp*の絶対値を返します。|  
|**ACOS(** _float_exp_ **)** (ODBC 1.0)|float_expのアークコサインを、ラジアンで表した*角度で返*します。|  
|**ASIN(** _float_exp_ **)** (ODBC 1.0)|float_expのアークシンをラジアンで表した*角度で返*します。|  
|**ATAN(** _float_exp_ **)** (ODBC 1.0)|*float_exp*のアークタンジェントを、ラジアンで表した角度で返します。|  
|**ATAN2(** _float_exp1_, _float_exp2_**)** (ODBC 2.0)|*float_exp1*と*float_exp2*で指定された*x*座標と*y*座標のアークタンジェントを、それぞれ角度としてラジアンで返します。|  
|**天井(** _numeric_exp_ **)** (ODBC 1.0)|*numeric_exp*以上の最小整数を返します。 戻り値は入力パラメーターと同じデータ型です。|  
|**COS(** _float_exp_ **)** (ODBC 1.0)|float_expのコ*サインを返*します*float_exp。*|  
|**COT(** _float_exp_ **)** (ODBC 1.0)|*float_exp*のコタンジェントを返します( *float_exp*はラジアンで表される角度です)。|  
|**度(** _numeric_exp_ **)** (ODBC 2.0)|numeric_expラジアンから変換された度数*を*返します。|  
|**EXP(** _float_exp_ **)** (ODBC 1.0)|*float_exp*の指数値を返します。|  
|**フロア(** _numeric_exp_ **)** (ODBC 1.0)|*numeric_exp*以下の最大の整数を返します。 戻り値は入力パラメーターと同じデータ型です。|  
|**ログ(** _float_exp_ **)** (ODBC 1.0)|*float_exp*の自然対数を返します。|  
|**LOG10(** _float_exp_ **)** (ODBC 2.0)|*float_exp*の底数 10 の対数を返します。|  
|**MOD(** _integer_exp1_, _integer_exp2_**)** (ODBC 1.0)|*integer_exp1*の剰余を*integer_exp2*で除算した剰余 (モジュラス) を返します。|  
|**PI( )** (ODBC 1.0)|pi の定数値を浮動小数点値として返します。|  
|**電源(** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|*numeric_exp*の値を integer_exp の累乗に戻*します*。|  
|**ラジアン(** _numeric_exp_ **)** (ODBC 2.0)|numeric_exp度から変換されたラジアンの数*を*返します。|  
|**ランド(**[*integer_exp*]**)** (ODBC 1.0)|オプションのシード値として*integer_exp*を使用して、ランダムな浮動小数点値を返します。|  
|**ROUND(** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|小数点*numeric_exp**右integer_exp四*捨五入して戻します。 *integer_exp*が負の場合 *、numeric_exp*小数点の左側の&#124;&#124;*integer_exp&#124;* に丸められます。|  
|**符号 (** _numeric_exp_ **)** (ODBC 1.0)|*numeric_exp*の符号を示すインジケーターを返します。 *numeric_exp*が 0 未満の場合は、-1 が返されます。 *numeric_exp*がゼロに等しい場合は、0 が返されます。 *numeric_exp*がゼロより大きい場合は、1 が返されます。|  
|**シン(** _float_exp_ **)** (ODBC 1.0)|float_expのを返します*float_exp**float_exp。*|  
|**SQRT(** _float_exp_ **)** (ODBC 1.0)|*float_exp*の平方根を返します。|  
|**タン(** _float_exp_ **)** (ODBC 1.0)|*float_exp*のタンジェントを返します*float_exp。*|  
|**切り捨て (** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|小数点*numeric_exp**右integer_exp切*り捨てられた値を返します。 *integer_exp*が負の場合 *、numeric_exp*小数点 &#124;の左側にある*integer_exp&#124;* の桁数に切り捨てられます。|
