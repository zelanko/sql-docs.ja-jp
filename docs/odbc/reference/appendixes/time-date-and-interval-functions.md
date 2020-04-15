---
title: 時間、日付、および間隔の関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aec3d6b23383edcc9659ff884e8cd71b0595dae1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302823"
---
# <a name="time-date-and-interval-functions"></a>時刻、日付、および間隔を扱う関数
次の表は、ODBC スカラー関数セットに含まれる時刻と日付の関数の一覧です。 アプリケーションは、情報*型*のSQL_TIMEDATE_FUNCTIONSを使用して**SQLGetInfo**を呼び出すことによって、ドライバーがサポートする時刻と日付の関数を決定できます。  
  
 *timestamp_exp*として示される引数は、列の名前、別のスカラー関数の結果、または ODBC*時刻エスケープ**、ODBC-date-エスケープ*、または ODBC*タイムスタンプ*SQL_TYPE_TIMESTAMP SQL_TYPE_DATE SQL_TYPE_TIME SQL_VARCHAR SQL_CHAR エスケープです。  
  
 *date_exp*として示される引数は、列の名前、別のスカラー関数の結果、または SQL_TYPE_TIMESTAMP SQL_TYPE_DATE SQL_VARCHAR SQL_CHAR *ODBC 日付エスケープ*または*ODBC タイムスタンプエスケープ*です。  
  
 *time_exp*として示される引数は、列の名前、別のスカラー関数の結果、または SQL_TYPE_TIMESTAMP SQL_TYPE_TIME SQL_VARCHAR SQL_CHAR *ODBC タイム エスケープ*または*ODBC タイムスタンプ エスケープ*です。  
  
 CURRENT_DATE、CURRENT_TIME、およびCURRENT_TIMESTAMPのタイム・タイム・デイト・スカラー関数が、SQL-92 に合わせて ODBC 3.0 に追加されました。  
  
|機能|説明|  
|--------------|-----------------|  
|**CURRENT_DATE( )** (ODBC 3.0)|現在の日付を返します。|  
|**CURRENT_TIME[(***時間精度***)]** (ODBC 3.0)|現在のローカル時間を返します。 *時間精度*引数は、戻り値の秒精度を決定します。|  
|**CURRENT_TIMESTAMP**<br /> **[(***タイムスタンプ精度***)]** (ODBC 3.0)|現在のローカル日付とローカル時刻をタイムスタンプ値として返します。 *timestamp-precision*引数は、返されるタイム・スタンプの秒精度を決定します。|  
|**カーデート( )** (ODBC 1.0)|現在の日付を返します。|  
|**時間時間( )** (ODBC 1.0)|現在のローカル時間を返します。|  
|**(date_exp)** *date_exp* **)** (ODBC 2.0)|データ ソース固有の曜日 (たとえば、日曜日から土曜日、または日) を含む文字列を返します。 - Sat. 英語を使用するデータ ソースの場合、またはドイツ語を使用するデータ ソースの Sstag を使用する Sonntag) の場合*は、date_exp*の日の部分を使用します。|  
|**日の月(** *date_exp)* **)** (ODBC 1.0)|*date_exp*の月フィールドに基づいて、1 から 31 の範囲の整数値として月の日を返します。|  
|**曜日のdate_exp** *date_exp* **)** (ODBC 1.0)|date_expの週フィールドに基づいて曜日を、1 から 7 の範囲の*整数値として返*します。|  
|**デイオブイヤー(** *date_exp* **)** (ODBC 1.0)|date_exp年フィールドに基づいて、1 ~ 366 の範囲の*整数値として年*の日を返します。|  
|**抽出 (***抽出元からの抽出フィールド**extract-source* **)** (ODBC 3.0)|抽出元*の抽出フィールド*部分を返*します*。 *抽出元引数*は、日時式または間隔式です。 *抽出フィールド引数*は、次のいずれかのキーワードにすることができます。<br /><br /> 年月日時分秒<br /><br /> 戻り値の精度は実装定義です。 SECOND が指定されていない限り、スケールは 0 で、その場合、スケールは*抽出元*フィールドの秒の小数部の精度より小さくなります。|  
|**時(** *time_exp* **)** (ODBC 1.0)|*time_exp*の時間フィールドに基づいて時間を 0 ~ 23 の整数値として返します。|  
|**分(** *time_exp* **)** (ODBC 1.0)|*time_exp*の分フィールドに基づいて分を 0 ~ 59 の整数値で返します。|  
|**月 (** *date_exp* **)** (ODBC 1.0)|*date_exp*月フィールドに基づいて、1 ~ 12 の整数値として月を返します。|  
|**月名 (** *date_exp* **)** (ODBC 2.0)|*date_exp*の月の部分に対して、その月のデータ ソース固有の名前 (英語を使用するデータ ソースの場合は 1 月から 12 月、1 月 1 月、1 月から 12 月から 12 月まで) を含む文字列date_exp返します。|  
|**NOW( )** (ODBC 1.0)|現在の日付と時刻をタイムスタンプ値として返します。|  
|**クォーター(** *date_exp* **)** (ODBC 1.0)|*date_exp*の四半期を 1 ~ 4 の範囲の整数値として返します。|  
|**2 番目の (** *time_exp* **)** (ODBC 1.0)|time_expの 2*番目のフィールド*に基づいて、2 番目のフィールドを 0 ~ 59 の整数値として返します。|
|**タイムスタンプ追加(** *間隔*、 *integer_exp*、 *timestamp_exp* **)** (ODBC 2.0)|timestamp_expに、型*の間隔**integer_exp*追加することによって計算されるタイムスタンプ*を返*します。 *区間*の有効な値は、次のキーワードです。<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> 端数の秒は 10 億分の 1 秒で表されます。 たとえば、次の SQL ステートメントは、各従業員の名前と、その従業員の 1 年の記念日を返します。<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> *timestamp_exp*が時間値で、*間隔*で日、週、月、四半期、または年を指定する場合 *、timestamp_exp*の日付部分は、結果のタイムスタンプを計算する前に現在の日付に設定されます。<br /><br /> *timestamp_exp*が日付値で、*間隔*で秒、秒、分、または時間の小数部を指定する場合 *、timestamp_exp*の時間部分は、結果のタイムスタンプを計算する前に 0 に設定されます。<br /><br /> アプリケーションは、SQL_TIMEDATE_ADD_INTERVALS オプションを指定して**SQLGetInfo**を呼び出すことによって、データ ソースがサポートする間隔を決定します。|  
|**タイムスタンプディフ(** *間隔*、 *timestamp_exp1*、 *timestamp_exp2* **)** (ODBC 2.0)|*timestamp_exp2*が*timestamp_exp1*より大きい場合の、型*の間隔*の整数を返します。 *区間*の有効な値は、次のキーワードです。<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> 端数の秒は 10 億分の 1 秒で表されます。 たとえば、次の SQL ステートメントは、各従業員の名前と、雇用された年数を返します。<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> いずれかのタイム・スタンプ式が時刻値で、*間隔*で日、週、月、四半期、または年を指定する場合、タイム・スタンプの差分を計算する前に、そのタイム・スタンプの日付部分が現在の日付に設定されます。<br /><br /> いずれかのタイムスタンプ式が日付値で、*間隔*で秒、秒、分、または時間の小数部を指定する場合、タイム・スタンプの差を計算する前に、そのタイム・スタンプの時間部分が 0 に設定されます。<br /><br /> アプリケーションは、SQL_TIMEDATE_DIFF_INTERVALS オプションを指定して**SQLGetInfo**を呼び出すことによって、データ ソースがサポートする間隔を決定します。|  
|**週 (** *date_exp* **)** (ODBC 1.0)|date_expの週フィールドに基づいて、1 ~ 53 の範囲の*整数値として年*の週を返します。|  
|**年(** *date_exp* **)** (ODBC 1.0)|date_expの年フィールドに基づいて年を*整数値として返*します。 範囲はデータ ソースに依存します。|
