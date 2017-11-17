---
title: "書式設定 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FORMAT_TSQL
- FORMAT
dev_langs:
- TSQL
helpviewer_keywords:
- FORMAT function
ms.assetid: dad6f24c-b8d9-4dbe-a561-9b167b8f20c8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75f944ad28bc56300db7ca9dd7220036faaea711
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="format-transact-sql"></a>FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  指定した書式およびオプションのカルチャの書式設定値を返します[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 文字列としての日付/時刻と数値のロケール依存の書式指定には FORMAT 関数を使用します。 一般的なデータ型変換では、引き続き CAST または CONVERT を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
FORMAT ( value, format [, culture ] )  
```  
  
## <a name="arguments"></a>引数  
 *value*  
 書式設定がサポートされているデータ型の式。 有効な型の一覧については、以下の「解説」のセクションにある表を参照してください。  
  
 *書式設定*  
 **nvarchar**形式パターン。  
  
 *形式*引数含める必要があります、有効な .NET Framework 形式文字列 (たとえば、"C"または"D") は、標準書式指定文字列、またはカスタム文字のパターンとしての日付と数値 (たとえば、"MMMM DD, yyyy (dddd)"). 複合書式設定はサポートされていません。 これらの書式設定パターンの完全な説明については、一般書式指定文字列、カスタムの日付と時刻の形式、およびカスタム数値書式で .NET Framework のドキュメントを参照してください。 適切な開始点は、トピック「"[型の書式設定](http://go.microsoft.com/fwlink/?LinkId=211776)。"  
  
 *カルチャ*  
 省略可能な**nvarchar**カルチャを指定する引数。  
  
 場合、*カルチャ*引数が指定されていない、現在のセッションの言語を使用します。 この言語には、SET LANGUAGE ステートメントを使用して、暗黙的または明示的には設定されます。 *カルチャ*、引数として .NET Framework でサポートされている任意のカルチャを受け入れますで明示的にサポートされる言語に限定されるわけで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 場合、*カルチャ*引数が有効でない形式でエラーが発生します。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar**または null  
  
 戻り値の長によって決定されます、*形式*です。  
  
## <a name="remarks"></a>解説  
 形式は NULL を返しますエラー以外の場合、*カルチャ*外にある*有効*です。 値が指定されている場合に NULL が返されますなど*形式*が無効です。  
 
 FORMAT 関数は非決定的です。   
  
 形式は、.NET Framework 共通言語ランタイム (CLR) の存在に依存しています。  
  
 この関数は、CLR の存在に依存しているために、リモート処理は実行することはできません。 リモート処理、CLR を必要とする関数には、リモート サーバーでエラー可能性があります。  
  
 形式は、書式指定規則で、コロンおよび期間をエスケープする必要があるディクテーション CLR に依存します。 そのため、形式が (2 番目のパラメーター) を文字列とコロンまたはピリオド、コロンが含まれているか、期間、ときに、入力値の円記号でエスケープする必要があります (最初) のパラメーターは、**時間**データ型。 参照してください[時刻のデータ型を使用してD. 形式](#ExampleD)です。  
  
 次の表に、許容データ型、*値*とその .NET Framework のマッピングと同じ型の引数。  
  
|カテゴリ|型|.NET の種類|  
|--------------|----------|---------------|  
|数値|bigint|Int64|  
|数値|int|Int32|  
|数値|smallint|Int16|  
|数値|tinyint|Byte|  
|数値|decimal|SqlDecimal|  
|数値|numeric|SqlDecimal|  
|数値|float|Double|  
|数値|real|単一|  
|数値|smallmoney|Decimal|  
|数値|money|Decimal|  
|日時|date|DateTime|  
|日時|time|TimeSpan|  
|日時|datetime|DateTime|  
|日時|smalldatetime|DateTime|  
|日時|datetime2|DateTime|  
|日時|datetimeoffset|DateTimeOffset|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-format-example"></a>A. 単純な FORMAT 例  
 次の例では、さまざまなカルチャ用にフォーマットされた単純な日付を返します。  
  
```sql  
DECLARE @d DATETIME = '10/01/2011';  
SELECT FORMAT ( @d, 'd', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'd', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'd', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'd', 'zh-cn' ) AS 'Simplified Chinese (PRC) Result';   
  
SELECT FORMAT ( @d, 'D', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'D', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'D', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'D', 'zh-cn' ) AS 'Chinese (Simplified PRC) Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
US English Result Great Britain English Result  German Result Simplified Chinese (PRC) Result  
----------------  ----------------------------- ------------- -------------------------------------  
10/1/2011         01/10/2011                    01.10.2011    2011/10/1  
  
(1 row(s) affected)  
  
US English Result            Great Britain English Result  German Result                    Chinese (Simplified PRC) Result  
---------------------------- ----------------------------- -----------------------------  ---------------------------------------  
Saturday, October 01, 2011   01 October 2011               Samstag, 1. Oktober 2011        2011年10月1日  
  
(1 row(s) affected)  
```  
  
### <a name="b-format-with-custom-formatting-strings"></a>B. カスタムの書式指定文字列を使用する FORMAT  
 次の例では、カスタム書式を指定して数値を書式設定する方法を示します。 例では、現在の日付が 2012 年 9 月 27 日である前提としています。 これらおよびその他のカスタム形式の詳細については、次を参照してください。[カスタム数値書式指定文字列](http://msdn.microsoft.com/library/0c899ak8.aspx)です。  
  
```sql  
DECLARE @d DATETIME = GETDATE();  
SELECT FORMAT( @d, 'dd/MM/yyyy', 'en-US' ) AS 'DateTime Result'  
       ,FORMAT(123456789,'###-##-####') AS 'Custom Number Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DateTime Result  Custom Number Result  
--------------   --------------------  
27/09/2012       123-45-6789  
  
(1 row(s) affected)  
```  
  
### <a name="c-format-with-numeric-types"></a>C. 数値型を使用する FORMAT  
 次の例から 5 行を返します、 **Sales.CurrencyRate**テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 列**EndOfDateRate**型として格納された**money**テーブルにします。 この例では、書式設定されずに返された列を、.NET の数値書式、一般書式、および通貨の書式の種類を指定して書式設定します。 これらおよびその他の数値形式の詳細については、次を参照してください。[標準の数値書式指定文字列](http://msdn.microsoft.com/library/dwhawy9k.aspx)です。  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
            ,FORMAT(EndOfDayRate, 'N', 'en-us') AS 'Number Format'  
            ,FORMAT(EndOfDayRate, 'G', 'en-us') AS 'General Format'  
            ,FORMAT(EndOfDayRate, 'C', 'en-us') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1.00            1.0002          $1.00  
2              1.55          1.55            1.5500          $1.55  
3              1.9419        1.94            1.9419          $1.94  
4              1.4683        1.47            1.4683          $1.47  
5              8.2784        8.28            8.2784          $8.28  
  
(5 row(s) affected)  
  
```  
  
 この例では、ドイツのカルチャ de (de-de) を指定します。  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
      ,FORMAT(EndOfDayRate, 'N', 'de-de') AS 'Numeric Format'  
      ,FORMAT(EndOfDayRate, 'G', 'de-de') AS 'General Format'  
      ,FORMAT(EndOfDayRate, 'C', 'de-de') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1,00            1,0002          1,00 €  
2              1.55          1,55            1,5500          1,55 €  
3              1.9419        1,94            1,9419          1,94 €  
4              1.4683        1,47            1,4683          1,47 €  
5              8.2784        8,28            8,2784          8,28 €  
  
 (5 row(s) affected)  
```  
  
###  <a name="ExampleD"></a> D. 時刻のデータ型を使用する FORMAT します。  
 形式がために、このような場合に NULL を返します`.`と`:`はエスケープされません。  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh.mm');   --> returns NULL  
SELECT FORMAT(cast('07:35' as time), N'hh:mm');   --> returns NULL  
```  
  
 形式で書式設定された文字列が返されます、`.`と`:`エスケープされます。  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh\.mm');  --> returns 07.35  
SELECT FORMAT(cast('07:35' as time), N'hh\:mm');  --> returns 07:35  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

