---
title: 文字列関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], string functions
- string functions [ODBC]
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03f783cbc287d9c315844e1a9df53187e4e2ba28
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="string-functions"></a>文字列関数
次の表は、文字列操作関数を一覧表示します。 文字列関数が呼び出すことによって、ドライバーでサポートされる、アプリケーションを判別**SQLGetInfo**で、*情報の種類*SQL_STRING_FUNCTIONS のです。  
  
## <a name="remarks"></a>解説  
 として表される引数*string_exp* 、列の名前にすることができます、*文字文字列リテラル*、または基になるデータ型を SQL_CHAR、sql _ として表すことができます、別のスカラー関数の結果VARCHAR、または SQL_LONGVARCHAR します。  
  
 として表される引数*character_exp*可変長の文字の文字列です。  
  
 として表される引数*開始*、*長さ*、または*カウント*できます、*数値リテラル*または別のスカラー関数の結果を基になるデータ型は、SQL_TINYINT、SQL_SMALLINT、または SQL_INTEGER として表現できます。  
  
 ここで示す文字列関数は 1 ベースです。その文字列の最初の文字は 1 文字です。  
  
 BIT_LENGTH、CHAR_LENGTH、CHARACTER_LENGTH、OCTET_LENGTH、および位置の文字列のスカラー関数、sql-92 に合うように ODBC 3.0 で追加されました。  
  
|関数|Description|  
|--------------|-----------------|  
|**ASCII (** *string_exp* **)** (ODBC 1.0)|左端の文字の ASCII コード値を返します*string_exp*整数として。|  
|**BIT_LENGTH (** *string_exp* **)** (ODBC 3.0)|文字列式の長さ (ビット単位) を返します。<br /><br /> 文字列データ型に対してのみは機能には、変換は暗黙的にない*string_exp*代わりに文字列にはどのようなデータ型が指定の (内部) のサイズを返します。|  
|**CHAR (** *コード* **)** (ODBC 1.0)|持つ、ASCII 文字のコードで指定された値を返します*コード*です。 値*コード*0 ~ 255 の範囲にする必要があります。 それ以外の場合、戻り値は、データ ソースに依存します。|  
|**CHAR_LENGTH (** *string_exp* **)** (ODBC 3.0)|文字列式が文字データ型以外の場合、文字列式の文字の長さを返しますそれ以外の場合、文字列式 (最小の整数 8 で割った値のビット数より小さくない) のバイト単位の長さを返します。 (この関数は CHARACTER_LENGTH 関数と同じ) です。|  
|**CHARACTER_LENGTH (** *string_exp* **)** (ODBC 3.0)|文字列式が文字データ型以外の場合、文字列式の文字の長さを返しますそれ以外の場合、文字列式 (最小の整数 8 で割った値のビット数より小さくない) のバイト単位の長さを返します。 (この関数は CHAR_LENGTH 関数と同じ) です。|  
|**CONCAT (** *string_exp1*、*string_exp2 * * *)** (ODBC 1.0)|連結の結果である文字列を返します*string_exp2*に*string_exp1*です。 結果の文字列は DBMS に依存します。 たとえば、次の列として表さ*string_exp1*は戻り値の NULL が SQL Server が返す NULL 以外の文字列を NULL 値を DB2 に格納されています。|  
|**相違点 (** *string_exp1*、*string_exp2 * * *)** (ODBC 2.0)|SOUNDEX 関数によって返される値の差を示す整数値を返します*string_exp1*と*string_exp2*です。|  
|**挿入 (** *string_exp1*、*開始*、*長さ*、 *string_exp2 * * *)** (ODBC 1.0)|Where を文字列で文字を返します*長さ*文字はから削除されている*string_exp1*で始まる、*開始*、どこで*string_exp2*が挿入されている*string_exp、*始点*開始*です。|  
|**LCASE (** *string_exp* **)** (ODBC 1.0)|文字列を以下にするを返します*string_exp*、すべて大文字を小文字に変換します。|  
|**左 (** *string_exp*、*数 * * *)** (ODBC 1.0)|返します、左端*カウント*の文字*string_exp*です。|  
|**長さ (** *string_exp* **)** (ODBC 1.0)|内の文字の数を返します*string_exp、*末尾の空白を除外します。<br /><br /> **長さ**文字列のみを受け入れます。 このため変換は暗黙的に*string_exp*文字列、および戻り値 (データ型のサイズ内部ではなく) この文字列の長さにします。|  
|**検索 (** *string_exp1*、 *string_exp2*[、*開始*]**)** (ODBC 1.0)|最初に見つかった位置の開始位置を返します*string_exp1*内*string_exp2*です。 最初に見つかった位置の検索*string_exp1*内の最初の文字位置から始まります*string_exp2*しない限り、オプションの引数*開始*が指定されています。 場合*開始*を指定すると、検索の値で指定された文字位置から始まります*開始*です。 最初の文字の位置*string_exp2*値 1 で示されます。 場合*string_exp1*内に見つからなかった*string_exp2*値 0 が返されます。<br /><br /> アプリケーションで、検索のスカラー関数を呼び出すことができるかどうか、 *string_exp1*、 *string_exp2*、および*開始*引数、ドライバーは SQL_FN_STR_LOCATE を返しますと**SQLGetInfo**してを呼び出すと、*オプション*SQL_STRING_FUNCTIONS のです。 アプリケーションでのみを持つ 検索のスカラー関数を呼び出すことができる場合、 *string_exp1*と*string_exp2*引数、ドライバーは SQL_FN_STR_LOCATE_2 を返しますと**SQLGetInfo**してを呼び出すと、*オプション*SQL_STRING_FUNCTIONS のです。 2 つまたは 3 つの引数を指定して検索関数の呼び出しをサポートするドライバーは、SQL_FN_STR_LOCATE と SQL_FN_STR_LOCATE_2 の両方を返します。|  
|**LTRIM (** *string_exp* **)** (ODBC 1.0)|文字を返します*string_exp*、先行する空白が削除されたとします。|  
|**OCTET_LENGTH (** *string_exp* **)** (ODBC 3.0)|文字列式の長さ (バイト単位) を返します。 結果は、ビット数を 8 で割った値以上の最小の整数になります。<br /><br /> 文字列データ型に対してのみは機能には、変換は暗黙的にない*string_exp*代わりに文字列にはどのようなデータ型が指定の (内部) のサイズを返します。|  
|**位置 (** *character_exp* **IN** *character_exp * * *)** (ODBC 3.0)|2 番目の文字式には、最初の文字式の位置を返します。 結果は、実装定義の有効桁数と小数点以下桁数は 0 の正確な数値です。|  
|**繰り返します (** *string_exp、* *数 * * *)** (ODBC 1.0)|文字の文字列で構成を返します*string_exp*繰り返し*カウント*回です。|  
|**置換 (** *string_exp1*、 *string_exp2*、 *string_exp3 * * *)** (ODBC 1.0)|検索*string_exp1*の foroccurrences *string_exp2*、置き換えます*string_exp3*です。|  
|**右 (** *string_exp*、*数 * * *)** (ODBC 1.0)|右端を返します*カウント*の文字*string_exp*です。|  
|**RTRIM (** *string_exp* **)** (ODBC 1.0)|文字を返します*string_exp*を空白で削除します。|  
|**SOUNDEX (** *string_exp* **)** (ODBC 2.0)|内の単語のサウンドを表すデータ ソースに依存する文字の文字列を返します*string_exp*です。 たとえば、SQL Server には 4 桁の SOUNDEX コード; が返されますOracle では、各単語の音声表現を返します。|  
|**領域 (** *カウント* **)** (ODBC 2.0)|成る文字列を返します*カウント*スペースです。|  
|**部分文字列 (** *string_exp*、*開始*、長さ **)** (ODBC 1.0)|派生した文字列を返します*string_exp*で指定された文字位置から始まる、*開始*の*長さ*文字です。|  
|**UCASE (** *string_exp* **)** (ODBC 1.0)|文字列を以下にするを返します*string_exp*、すべて小文字を大文字に変換します。|
