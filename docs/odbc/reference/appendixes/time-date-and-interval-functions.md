---
title: "日付、時刻、および間隔を扱う関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 64af89226e917b05c28f0c85500281fa84bc676c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="time-date-and-interval-functions"></a>時刻、日付、および間隔を扱う関数
次の表には、ODBC スカラー関数のセットに含まれている日付と時刻の関数が一覧表示します。 アプリケーションでは、どの日付と時刻の関数が呼び出すことによって、ドライバーでサポートされるを判断できます**SQLGetInfo**で、*情報の種類*SQL_TIMEDATE_FUNCTIONS のです。  
  
 として表される引数*timestamp_exp* 、別のスカラー関数の結果の列の名前を指定できますまたは*ODBC 時刻エスケープ*、 *ODBC 日付エスケープ*、または*ODBC タイムスタンプ エスケープ*SQL_CHAR、SQL_VARCHAR、SQL_TYPE_TIME、SQL_TYPE_DATE、または SQL_TYPE_TIMESTAMP と基になるデータ型を表すことができます。  
  
 として表される引数*date_exp* 、別のスカラー関数の結果の列の名前を指定できますまたは*ODBC 日付エスケープ*または*ODBC タイムスタンプ エスケープ*、ここで、基になるデータ型は、SQL_CHAR、SQL_VARCHAR、SQL_TYPE_DATE、または SQL_TYPE_TIMESTAMP として表すことができます。  
  
 として表される引数*time_exp* 、別のスカラー関数の結果の列の名前を指定できますまたは*ODBC 時刻エスケープ*または*ODBC タイムスタンプ エスケープ*、ここで、基になるデータ型は、SQL_CHAR、SQL_VARCHAR、SQL_TYPE_TIME、または SQL_TYPE_TIMESTAMP として表すことができます。  
  
 CURRENT_DATE、CURRENT_TIME、CURRENT_TIMESTAMP timedate スカラー関数、sql-92 に合うように ODBC 3.0 で追加されました。  
  
|関数|Description|  
|--------------|-----------------|  
|**CURRENT_DATE に関するページ ()** (ODBC 3.0)|現在の日付を返します。|  
|**CURRENT_TIME [(** *時間精度* **)]** (ODBC 3.0)|現在のローカル時間を返します。 *時間精度*引数は、戻り値の秒の有効桁数を決定します。|  
|**CURRENT_TIMESTAMP**<br /> **[(** *タイムスタンプ精度* **)]** (ODBC 3.0)|タイムスタンプ値として現在の日付と現地時刻を返します。 *タイムスタンプ精度*引数が返されたタイムスタンプの秒の有効桁数を決定します。|  
|**CURDATE に関するページ ()** (ODBC 1.0)|現在の日付を返します。|  
|**CURTIME に関するページ ()** (ODBC 1.0)|現在のローカル時間を返します。|  
|**DAYNAME (** *date_exp* **)** (ODBC 2.0)|(たとえば、Sunday ~ Saturday または Sun 1 日のデータ ソース固有名を含む文字列を返しますです。 ～ Sat.、 ドイツ語を使ったデータ ソースの英語版、または Sonntag ~ samstag などを使用するデータ ソース) 用の日の部分の*date_exp*です。|  
|**DAYOFMONTH (** *date_exp* **)** (ODBC 1.0)|月のフィールドに基づき、月の日を返します*date_exp* 1 ~ 31 の範囲の整数値として。|  
|**DAYOFWEEK (** *date_exp* **)** (ODBC 1.0)|週のフィールドに基づく週の日を返します*date_exp*の範囲の整数値として 1 ~ 7 の場合、1 は日曜日を表します。|  
|**DAYOFYEAR (** *date_exp* **)** (ODBC 1.0)|[Year] フィールドに基づき、年の日を返します*date_exp* 1 ~ 366 の範囲の整数値として。|  
|**抽出 (** *抽出フィールド FROM* *抽出ソース* **)** (ODBC 3.0)|返します、*抽出フィールド*の部分、*抽出ソース*です。 *抽出ソース*引数は、datetime または間隔式。 *抽出フィールド*引数には、次のキーワードのいずれかを指定できます。<br /><br /> 年、月 1 日の時間分の 1 秒<br /><br /> 戻り値の精度は、実装定義です。 桁数が 0 秒が指定されていない場合、小数点以下桁数がより小さくありませんの秒の小数部の有効桁数、*抽出ソース*フィールドです。|  
|**時間 (** *time_exp* **)** (ODBC 1.0)|時間のフィールドに基づいて時間を返します*time_exp* 0 ~ 23 の範囲の整数値として。|  
|**分 (** *time_exp* **)** (ODBC 1.0)|分単位のフィールドに基づく分が返されます*time_exp* 0 ~ 59 の範囲の整数値として。|  
|**月 (** *date_exp* **)** (ODBC 1.0)|月のフィールドに基づき、月を返します*date_exp* 1 ~ 12 の範囲の整数値として。|  
|**MONTHNAME (** *date_exp* **)** (ODBC 2.0)|月の部分をデータ ソース固有の月の名前 (たとえば、January ~ December または Jan. ~ dec.、英語を使用するデータ ソースのドイツ語を使ったデータ ソースの場合は Januar ~) を含む文字列を返します*date_exp*です。|  
|**今すぐに関するページ ()** (ODBC 1.0)|現在の日付と時刻のタイムスタンプ値として返します。|  
|**四半期 (** *date_exp* **)** (ODBC 1.0)|における四半期を返します*date_exp*の範囲の整数値として 1 ~ 4、ここで、1 を表す年 1 月 1 日 ~ 3 月 31 日です。|  
|**2 番目 (** *time_exp* **)** (ODBC 1.0)|2 番目のフィールドに基づく秒を返します*time_exp* 0 ~ 59 の範囲の整数値として。|
|**TIMESTAMPADD (** *間隔*、 *integer_exp*、 *timestamp_exp* **)** (ODBC 2.0)|追加することによって計算のタイムスタンプを返す*integer_exp*型の間隔*間隔*に*timestamp_exp*です。 有効な値の*間隔*は次のキーワード。<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> ここで秒の小数部は、10億分の 1 秒で表現されます。 たとえば、次の SQL ステートメントは、各従業員と自分の 1 年間の記念日の名前を返します。<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> 場合*timestamp_exp*時刻の値と*間隔*日、週、月、四半期、または年の日付部分を指定*timestamp_exp*する前に、現在の日付に設定されています。結果として得られるタイムスタンプを計算しています。<br /><br /> 場合*timestamp_exp*日付の値と*間隔*小数部を指定します (秒)、秒、分、または時間単位の時間部分*timestamp_exp*する前に 0 に設定されています。結果として得られるタイムスタンプを計算しています。<br /><br /> アプリケーションを呼び出すことによって、データ ソースをサポートする間隔を決定**SQLGetInfo** SQL_TIMEDATE_ADD_INTERVALS オプションを使用します。|  
|**TIMESTAMPDIFF (** *間隔*、 *timestamp_exp1*、 *timestamp_exp2* **)** (ODBC 2.0)|整数型の間隔の数を返します*間隔*する*timestamp_exp2*がより大きい*timestamp_exp1*です。 有効な値の*間隔*は次のキーワード。<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> ここで秒の小数部は、10億分の 1 秒で表現されます。 たとえば、次の SQL ステートメントは、各従業員とそのユーザーが使用されている年の数の名前を返します。<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> タイムスタンプのいずれかの式が時間の値の場合と*間隔*日、週、月、四半期、または年、そのタイムスタンプの日付部分は、タイムスタンプの差を計算する前に現在の日付に設定を指定します。<br /><br /> タイムスタンプのいずれかの式が日付値の場合と*間隔*小数部を指定します、タイムスタンプの差を計算する前に、そのタイムスタンプの時刻部分が 0 に設定されて秒、秒、分、または時間、します。<br /><br /> アプリケーションを呼び出すことによって、データ ソースをサポートする間隔を決定**SQLGetInfo** SQL_TIMEDATE_DIFF_INTERVALS オプションを使用します。|  
|**週 (** *date_exp* **)** (ODBC 1.0)|週のフィールドに基づき、年の週を返します*date_exp* 1 ~ 53 の範囲の整数値として。|  
|**年 (** *date_exp* **)** (ODBC 1.0)|[Year] フィールドに基づき、年を返します*date_exp*整数値として。 範囲は、データ ソースに依存します。|
