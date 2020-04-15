---
title: 文字列関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], string functions
- string functions [ODBC]
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d9323809028ad170a4811b1af8b6e276cdbb4293
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302843"
---
# <a name="string-functions"></a>文字列関数
次の表は、文字列操作関数の一覧です。 アプリケーションは、*情報型*のSQL_STRING_FUNCTIONSを使用して**SQLGetInfo**を呼び出すことによって、ドライバーでサポートされる文字列関数を決定できます。  
  
## <a name="remarks"></a>解説  
 *string_exp*として示される引数は、列の名前、*文字ストリングリテラル*、または別のスカラー関数の結果であり、基になるデータ型をSQL_CHAR、SQL_VARCHAR、またはSQL_LONGVARCHARとして表すことができます。  
  
 *character_exp*として示される引数は、可変長の文字列です。  
  
 *開始*、*長さ*、または*count*として示される引数は *、数値リテラル*または別のスカラー関数の結果で、基になるデータ型をSQL_TINYINT、SQL_SMALLINT、またはSQL_INTEGERとして表すことができます。  
  
 ここにリストされている文字列関数は 1 から順に実行されます。つまり、文字列の最初の文字は文字 1 です。  
  
 BIT_LENGTH、CHAR_LENGTH、CHARACTER_LENGTH、OCTET_LENGTH、および位置文字列のスカラー関数が SQL-92 に合わせて ODBC 3.0 に追加されました。  
  
|機能|説明|  
|--------------|-----------------|  
|**ASCII(** _string_exp_ **)** (ODBC 1.0)|*string_exp*の左端の文字の ASCII コード値を整数として返します。|  
|**BIT_LENGTH(** _string_exp_ **)** (ODBC 3.0)|文字列式の長さ (ビット単位) を返します。<br /><br /> 文字列データ型に対してのみ機能しないため *、string_exp*を暗黙的に文字列に変換せず、指定されたデータ型の (内部) サイズを返します。|  
|**CHAR(** _コード_ **)** (ODBC 1.0)|*コード*で指定された ASCII コード値を持つ文字を返します。 *コード*の値は 0 ~ 255 の間にする必要があります。それ以外の場合、戻り値はデータ ソースに依存します。|  
|**CHAR_LENGTH(** _string_exp_ **)** (ODBC 3.0)|文字列式が文字データ型の場合は、文字列式の長さを文字数で返します。それ以外の場合は、文字列式の長さをバイト単位で返します (最小の整数は 8 で割ったビット数より小さい整数)。 (この関数はCHARACTER_LENGTH関数と同じです。|  
|**CHARACTER_LENGTH(** _string_exp_ **)** (ODBC 3.0)|文字列式が文字データ型の場合は、文字列式の長さを文字数で返します。それ以外の場合は、文字列式の長さをバイト単位で返します (最小の整数は 8 で割ったビット数より小さい整数)。 (この関数はCHAR_LENGTH関数と同じです。|  
|**コンキャット(** _string_exp1_,_string_exp2_**)** (ODBC 1.0)|*string_exp2*を連結した結果string_exp1*文字列を返*します。 結果の文字列は DBMS に依存します。 たとえば *、string_exp1*で表される列に NULL 値が含まれている場合、DB2 は NULL を返しますが、SQL Server は NULL 以外の文字列を返します。|  
|**差(** _string_exp1_,_string_exp2_**)** (ODBC 2.0)|*string_exp1*と*string_exp2*の SOUNDEX 関数によって返される値の差を示す整数値を返します。|  
|**INSERT(** _string_exp1_、*開始*、*長さ*、 _string_exp2_**)** (ODBC 1.0)|string_exp1*から**長さ*文字が削除された文字列を返し、*先頭*から始まる位置から*string_exp2*が*挿入*string_expから*開始*します。|  
|**LCASE(** _string_exp_ **)** (ODBC 1.0)|*string_exp*の文字列を返し、大文字はすべて小文字に変換されます。|  
|**左(** _string_exp_、_カウント_**)** (ODBC 1.0)|string_expの左端の*文字数*を返*string_exp*します。|  
|**長さ(** _string_exp_ **)** (ODBC 1.0)|末尾の空白を除く *、string_exp*の文字数を返します。<br /><br /> **LENGTH は**文字列のみを受け入れます。 したがって、*暗黙的にstring_exp*を文字列に変換し、この文字列の長さを返します (データ型の内部サイズではありません)。|  
|**場所を指定する(** _string_exp1_、 *string_exp2*[,*開始*]**)** (ODBC 1.0)|string_exp2内で最初に出現する*string_exp1*の開始位置*を*返します。 string_exp1*の最初*の出現箇所の検索*は、オプション*の引数 start が指定されていない限り *、string_exp2*の最初の文字位置から始まります。 *start*を指定すると、start の値で示される文字位置から検索が*開始*されます。 *string_exp2*の最初の文字位置は、値 1 で示されます。 string_exp2*内**にstring_exp1*が見つからない場合は、値 0 が返されます。<br /><br /> アプリケーションが *、string_exp1* *、string_exp2、* および*開始*引数を指定して LOCATE スカラー関数を呼び出すことができる場合、オプションが SQL_STRING_FUNCTIONS の*オプション*を指定して**SQLGetInfo**が呼び出されると、ドライバーはSQL_FN_STR_LOCATEを返します。 アプリケーションが *、string_exp1*と*string_exp2*引数のみを指定して LOCATE スカラー関数を呼び出すことができる場合、ドライバーは、SQL_STRING_FUNCTIONSの*オプション*を指定して**SQLGetInfo**を呼び出すとSQL_FN_STR_LOCATE_2を返します。 2 つまたは 3 つの引数を指定して LOCATE 関数の呼び出しをサポートするドライバーは、SQL_FN_STR_LOCATEとSQL_FN_STR_LOCATE_2の両方を返します。|  
|**LTRIM(** _string_exp_ **)** (ODBC 1.0)|先頭のブランクを除去した*状態で、 string_exp*の文字を戻します。|  
|**OCTET_LENGTH(** _string_exp_ **)** (ODBC 3.0)|文字列式の長さ (バイト単位) を返します。 結果は、ビット数を 8 で割った値以上の最小の整数になります。<br /><br /> 文字列データ型に対してのみ機能しないため *、string_exp*を暗黙的に文字列に変換せず、指定されたデータ型の (内部) サイズを返します。|  
|**位置(** _character_exp_ **IN** _character_exp_**)** (ODBC 3.0)|2 番目の文字式の最初の文字式の位置を返します。 結果は、実装で定義された精度と 0 のスケールを持つ正確な数値です。|  
|**繰り返し**_(string_exp、__カウント_**)(ODBC** 1.0)|繰り返し*カウント*回数で構成される文字列*string_exp*返します。|  
|**置換(** _string_exp1_、 *string_exp2*、 _string_exp3_**)** (ODBC 1.0)|*string_exp1*でstring_exp2*の出現*を検索し、 *string_exp3*に置き換えます。|  
|**右(** _string_exp_、_カウント_**)** (ODBC 1.0)|*string_exp*の右端の*文字数*を返します。|  
|**RTRIM(** _string_exp_ **)** (ODBC 1.0)|末尾ブランクが除去された*string_exp*の文字を戻します。|  
|**サウンド**_(string_exp)_ **)** (ODBC 2.0)|*string_exp*の単語のサウンドを表すデータ ソースに依存する文字列を返します。 たとえば、SQL Server は 4 桁の SOUNDEX コードを返します。Oracle は、各単語のふりがなを返します。|  
|**スペース(** _カウント_ **)** (ODBC 2.0)|*カウント*スペースで構成される文字列を返します。|  
|**サブストリング (** _string_exp_、*開始*、 長さ **) (ODBC** 1.0)|*長さ*文字の*start*で指定された文字位置から始まる*string_exp*から派生した文字列を返します。|  
|**UCASE(** _string_exp_ **)** (ODBC 1.0)|*string_exp*の文字列と同じ文字列を返し、すべての小文字を大文字に変換します。|
