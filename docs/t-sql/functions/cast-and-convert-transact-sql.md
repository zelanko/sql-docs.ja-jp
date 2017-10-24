---
title: "CAST および CONVERT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CAST_TSQL
- CONVERT_TSQL
- CAST
- CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- automatic data type conversion
- varbinary data type
- CONVERT function
- data types [SQL Server], converting
- large value data types
- implicit data type conversions
- image data type, converting
- explicit data type conversions [SQL Server]
- binary [SQL Server], converting
- text data type, converting
- date and time [SQL Server], cast and convert
- truncating conversions
- converting data types [SQL Server], conversion functions
- time zones [SQL Server]
- roundtrip conversions
ms.assetid: a87d0850-c670-4720-9ad5-6f5a22343ea8
caps.latest.revision: 136
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: b7f2f78bbda485de979c76076404f35122b61277
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="cast-and-convert-transact-sql"></a>CAST および CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

あるデータ型の式を別のデータ型の式に変換します。  
たとえば、次の例では、有効桁数のレベルが異なるその他の 2 つの型に入力データ型を変更します。
```sql  
SELECT 9.5 AS Original, CAST(9.5 AS int) AS int, 
    CAST(9.5 AS decimal(6,4)) AS decimal;
SELECT 9.5 AS Original, CONVERT(int, 9.5) AS int, 
    CONVERT(decimal(6,4), 9.5) AS decimal;
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
|翻訳元   |int    |decimal |  
|----|----|----|  
|9.5 |9 |9.5000 |  

> [!TIP]
> 多く[例](#BKMK_examples)がこのトピックの下部にします。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for CAST:  
CAST ( expression AS data_type [ ( length ) ] )  
  
-- Syntax for CONVERT:  
CONVERT ( data_type [ ( length ) ] , expression [ , style ] )  
```  
  
## <a name="arguments"></a>引数  
*式 (expression)*  
有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。
  
*data_type*  
対象のデータ型です。 これが含まれます**xml**、 **bigint**、および**sql_variant**です。 別名データ型は使用できません。
  
*length*  
対象のデータ型の長さを指定する整数です (省略可能)。 既定値は、30 です。
  
*スタイル*  
CONVERT 関数は、変換する方法を指定する整数式です*式*です。 スタイルが NULL の場合は、NULL が返されます。 範囲はによって決まります*data_type*です。 
  
## <a name="return-types"></a>戻り値の型
返します*式*に変換*data_type*です。

## <a name="date-and-time-styles"></a>日付および時刻のスタイル  
ときに*式*日付または時刻のデータ型は、*スタイル*次の表に示すように値のいずれかになります。 その他の値は 0 として処理されます。 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]から変換するときにサポートされている唯一のスタイルの日付し、時刻型を**datetimeoffset**は 0 または 1 です。 他のすべての変換スタイルでは 9809 が返されます。
  
>  [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、アラビア式での日付形式がクウェート アルゴリズムによりサポートされます。
  
|2 桁の年 (yy) (<sup>1</sup>)|4 桁の年 (yyyy)|Standard|入力/出力 (<sup>3</sup>)|  
|---|---|--|---|
|-|**0**または**100** (<sup>1、</sup><sup>2</sup>)|datetime および smalldatetime の既定値|mon dd yyyy hh:miAM (または PM)|  
|**1**|**101**|米国|1 = mm/dd/yy<br /> 101 = mm/dd/yyyy|  
|**2**|**102**|ANSI|2 = yy.mm.dd<br /> 102 = yyyy.mm.dd|  
|**3**|**103**|イギリス/フランス|3 = dd/mm/yy<br /> 103 = dd/mm/yyyy|  
|**4**|**104**|ドイツ語|4 = dd.mm.yy<br /> 104 = dd.mm.yyyy|  
|**5**|**105**|イタリア語|5 = dd-mm-yy<br /> 105 = dd-mm-yyyy|  
|**6**|**106** <sup>(1)</sup>|-|6 = dd mon yy<br /> 106 = dd mon yyyy|  
|**7**|**107** <sup>(1)</sup>|-|7 = Mon dd, yy<br /> 107 = Mon dd, yyyy|  
|**8**|**108**|-|hh:mi:ss|  
|-|**9**または**109** (<sup>1、</sup><sup>2</sup>)|既定値 + ミリ秒|mon dd yyyy hh:mi:ss:mmmAM (または PM)|  
|"**10**"|**110**|米国|10 = mm-dd-yy<br /> 110 = mm-dd-yyyy|  
|**11**|**111**|日本|11 = yy/mm/dd<br /> 111 = yyyy/mm/dd|  
|**12**|**112**|ISO|12 = yymmdd<br /> 112 = yyyymmdd|  
|-|**13**または**113** (<sup>1、</sup><sup>2</sup>)|ヨーロッパの既定値 + ミリ秒|dd mon yyyy hh:mi:ss:mmm(24h)|  
|**14**|**114**|-|hh:mi:ss:mmm(24h)|  
|-|**20**または**120** (<sup>2</sup>)|ODBC 標準|yyyy-mm-dd hh:mi:ss(24h)|  
|-|**21**または**121** (<sup>2</sup>)|time、date、datetime2、および datetimeoffset の ODBC 標準 (ミリ秒を含む) の既定値|yyyy-mm-dd hh:mi:ss.mmm(24h)|  
|-|**126** (<sup>4</sup>)|ISO8601|yyyy-mm-ddThh:mi:ss.mmm (スペースなし)<br /> 注: 値をミリ秒 (mmm) が 0 の場合、ミリ秒の値は表示されません。 たとえば、値 '2012-11-07T18:26:20.000' は、'2012-11-07T18:26:20' と表示されます。|  
|-|**127**(<sup>6, 7</sup>)|ISO 8601 (タイム ゾーン Z)|yyyy-mm-ddThh:mi:ss.mmmZ (スペースなし)<br /> 注: 値をミリ秒 (mmm) が 0 の場合、ミリ秒の値は表示されません。 たとえば、値 '2012-11-07T18:26:20.000' は、'2012-11-07T18:26:20' と表示されます。|  
|-|**130** (<sup>1,</sup><sup>2</sup>)|イスラム暦 (<sup>5</sup>)|dd mon yyyy hh:mi:ss:mmmAM<br /> このスタイルでは、mon は月の正式名に関する複数トークンの Hijri (イスラム暦) ユニコード表現を意味します。 この値は正しく表示されない、既定値を SSMS の米国用インストール。|  
|-|**131** (<sup>2</sup>)|イスラム暦 (<sup>5</sup>)|dd/mm/yyyy hh:mi:ss:mmmAM|  
  
<sup>1</sup>これらのスタイル値が非決定的の結果を返します。 この場合は、すべての (yy) (2 桁の年) スタイルと、(yyyy) (4 桁の年) スタイルのサブセットが対象となります。
  
<sup>2</sup>既定値 (*スタイル** *0** または**100**、 **9**または**109**、 **13**または**113**、 **20**または**120**、および**21**または**121**)常に 2 桁の年 (yyyy) を返します。
  
<sup>3</sup>に変換する場合の入力**datetime**は出力を文字データに変換する場合。
  
<sup>4</sup> XML で使用するよう設計されています。 変換**datetime**または**smalldatetime**を文字データ、出力形式は、前の表で説明します。
  
<sup>5</sup>イスラム暦がいくつかのバリエーションのカレンダー システムです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ではクウェート アルゴリズムを使用します。
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定では、2 桁の年は、終了年 2049 年を基準に解釈されます。 つまり、2 桁の年である 49 年は 2049 年、50 年は 1950 年と解釈されます。 クライアント アプリケーションの中には、オートメーション オブジェクトをベースとするクライアント アプリケーションのように、2030 年を終了年とするものも多くあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって使用される基準になる年を変更する two digit year cutoff 構成オプションを提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付の一貫性のある処理を行うことができします。 年は 4 桁で指定することを推奨します。  
  
<sup>6</sup>文字データをキャストする場合にのみサポート**datetime**または**smalldatetime**です。 キャストのみが表す文字データが日付または時刻部分、 **datetime**または**smalldatetime**データ型の場合、指定されていない時刻部分に設定 00:00:00.000、され、指定されていません。日付部分は 1900-01-01 に設定します。
  
<sup>7</sup>オプションのタイム ゾーン インジケーター Z が XML にマップするが容易に使用される**datetime**にタイム ゾーン情報を持つ値[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**タイム ゾーンがない値. Z は、タイム ゾーン UTC-0 を示すインジケーターです。 他のタイム ゾーンは、+ または - の方向に HH:MM オフセットで示されます。 たとえば、 `2006-12-12T23:45:12-08:00`のようにします。
  
文字データに変換する際に**smalldatetime**、秒またはミリ秒を含むスタイルは、それらの位置の 0 を表示します。 変換するときは、日付の不要な部分を切り捨てることができます**datetime**または**smalldatetime**適切なを使用して値**char**または**varchar**データ型の長さ。
  
変換する場合**datetimeoffset**時刻を含むスタイルでは、文字のデータからは、タイム ゾーン オフセットが結果に追加されます。
  
## <a name="float-and-real-styles"></a>float 型と real 型スタイル
ときに*式*は**float**または**実際**、*スタイル*次の表に示すように値のいずれかになります。 その他の値は 0 として処理されます。
  
|値|出力|  
|---|---|
|**0** (既定値)|最高 6 桁。 該当する場合は、科学的表記法で使用します。|  
|**1**|常に 8 桁。 常に科学的表記法で使用します。|  
|**2**|常に 16 桁。 常に科学的表記法で使用します。|  
|**3**|常に 17 桁。 損失のない変換に使用します。 このスタイルですべての個別の float または実際の値は、個別の文字の文字列に変換する保証されます。<br /> **適用されます:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、以降では、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。|  
|**126, 128, 129**|レガシ システムのために含まれていますが、将来のリリースでは廃止される可能性があります。|  
  
## <a name="money-and-smallmoney-styles"></a>money および smallmoney スタイル
ときに*式*は**money**または**smallmoney**、*スタイル*次の表に示すように値のいずれかになります。 その他の値は 0 として処理されます。
  
|値|出力|  
|---|---|
|**0** (既定値)|小数点位置から左へ 3 桁ごとの位置にはコンマを挿入しません。また、小数点右側には 2 桁をとります。たとえば 4235.98 のようになります。|  
|**1**|小数点位置から左へ 3 桁ごとにコンマを挿入し、小数点右側には 2 桁をとります。たとえば 3,510.92 のようになります。|  
|**2**|小数点位置から左へ 3 桁ごとの位置にはコンマを挿入しません。また、小数点右側には 4 桁をとります。たとえば 4235.9819 のようになります。|  
|**126**|char(n) または varchar(n) に変換する場合はスタイル 2 に相当します。|  
  
## <a name="xml-styles"></a>xml スタイル
ときに*式*は**xml***、スタイル*次の表に示すように値のいずれかになります。 その他の値は 0 として処理されます。
  
|値|出力|  
|---|---|
|**0** (既定値)|既定の解析動作を使用します。つまり、余分な空白を破棄し、内部の DTD サブセットを許可しません。<br /> **注:**に変換する場合、 **xml**データ型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]意味のない空白よりも XML 1.0 では異なる方法で処理します。 詳細については、次を参照してください。 [XML データのインスタンスを作成する](../../relational-databases/xml/create-instances-of-xml-data.md)です。|  
|**1**|余分な空白を保持します。 このスタイル設定、既定**xml:space**同じ動作を行う処理として**xml:space ="preserve"**が代わりに指定されています。|  
|**2**|限定的な内部 DTD サブセット処理を有効にします。<br /><br /> 有効な場合、サーバーでは内部 DTD サブセットで提供される情報を次のように使用して、検証を行わない解析操作を実行できます。<br /> -属性の既定の設定が適用されます。<br /> -内部エンティティ参照は解決され、展開します。<br /> の構文の正確さ DTD のコンテンツ モデルがチェックされます。<br /> パーサーは、外部の DTD サブセットを無視します。 評価されません、XML 宣言を参照してくださいかどうか、**スタンドアロン**属性が設定されている**はい**または**ありません**、スタンドアロンである場合、解析、XML インスタンスドキュメントです。|  
|**3**|余分な空白を保持し、限定的な内部 DTD サブセット処理を有効にします。|  
  
## <a name="binary-styles"></a>バイナリ スタイル
ときに*式*は**binary (n)**、 **varbinary (n)**、 **char (n)**、または**varchar (n)**、 *スタイル*次の表に示すように値のいずれかになります。 表に記載されていないスタイル値の場合は、エラーが返されます。
  
|値|出力|  
|---|---|
|**0** (既定値)|ASCII 文字をバイナリ バイトに変換するか、バイナリ バイトを ASCII 文字に変換します。 各文字またはバイトは 1:1 で変換されます。<br /> 場合、 *data_type*がバイナリ型で、文字 0x が結果の左側に追加されます。|  
|**1**, **2**|場合、 *data_type*バイナリ型では、式は文字式である必要があります。 *式*が偶数の 16 進数字で構成する必要があります (0、1、2、3、4、5、6、7、8、9、A、B、C、D、E、F、a、b、c、d、e、f)。 場合、*スタイル*1 に設定されて、文字 0x にする必要があります最初の 2 つの文字式です。 式に奇数桁の文字が含まれているか、いずれかの文字が無効な場合は、エラーが発生します。<br /> 変換された式の長さがの長さより大きいかどうか、 *data_type*結果は、右側が切り捨てられました。<br /> 固定長*data_types*はより大きく、変換結果があるゼロの結果の右側に追加します。<br /> data_type が文字型である場合、式はバイナリ式であることが必要です。 各バイナリ文字は、16 進値を表す 2 桁の英数文字に変換されます。 変換された式の長さがより大きいかどうか、 *data_type*の長さに右側が切り捨てられます。<br /> 場合、 *data_type*は固定サイズの文字型であり、変換された結果の長さがの長さよりも小さい、 *data_type*;、でも維持するために変換された式の右側に空白を追加16 進数字の数。<br /> 文字の変換の結果の左側に 0x を追加、*スタイル*1 です。|  
  
## <a name="implicit-conversions"></a>暗黙的な変換
暗黙的な変換とは、CAST または CONVERT 関数を指定せずに実行される変換のことです。 明示的な変換は、CAST または CONVERT 関数を指定するを必要とされる変換のことです。 次の図は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムで提供されるデータ型に許可されている、すべての明示的および暗黙的なデータ型変換です。 これらを含める**xml**、 **bigint**、および**sql_variant**です。 暗黙の変換からの割り当てではありません、 **sql_variant**データ型への暗黙的な変換が**sql_variant**です。
  
> [!TIP]  
>  このグラフでダウンロード可能な PDF ファイルとして利用可能な[Microsoft ダウンロード センター](http://www.microsoft.com/download/details.aspx?id=35834)です。  
  
![データ型変換テーブル](../../t-sql/data-types/media/lrdatahd.png "データ型変換テーブル")
  
間で変換する際に**datetimeoffset**と文字型**char**、 **varchar**、 **nchar**、および**nvarchar**変換後のタイム ゾーン オフセット部分には、HH と MM-08 などの両方の 2 桁必要があります: 00 です。
  
> [!NOTE]  
>  変換する場合に警告を使用して、Unicode データは、常に偶数のバイトを使用するため**バイナリ**または**varbinary**と Unicode の間のデータ型をサポートします。 たとえば、次の変換返さない 41; の 16 進値4100 が返されます。`SELECT CAST(CAST(0x41 AS nvarchar) AS varbinary)`です。  
  
## <a name="large-value-data-types"></a>大きな値データ型
大きな値データ型とは動作同じ明示的および暗黙的な変換それより小さな値では、具体的には、 **varchar**、 **nvarchar**と**varbinary**データ型。 ただし、次のガイドラインを考慮する必要があります。
-   変換**イメージ**に**varbinary (max)**間の変換は、その逆が暗黙的な変換**テキスト**と**varchar(max)**、および**ntext**と**nvarchar (max)**です。  
-   などの大きな値のデータから変換型**varchar (max)** などの小さな入力**varchar**、暗黙的な変換が、切り捨て発生の大きな値が大きすぎる場合、小さいデータ型の長さを指定します。  
-   変換**varchar**、 **nvarchar**、または**varbinary**に対応する大きな値データ型が暗黙的に実行します。  
-   変換、 **sql_variant**大きな値データ型へのデータ型は明示的に変換します。  
-   大きな値データ型に変換できない、 **sql_variant**データ型。  
  
変換する方法について、 **xml**データ型を参照してください[XML データのインスタンスを作成する](../../relational-databases/xml/create-instances-of-xml-data.md)です。
  
## <a name="xml-data-type"></a>xml データ型。
明示的または暗黙的にキャストするとき、 **xml**データ型、文字列またはバイナリ データ型のコンテンツを**xml**データ型は、一連のルールに基づいてシリアル化します。 これらの規則については、次を参照してください。 [XML データのシリアル化を定義する](../../relational-databases/xml/define-the-serialization-of-xml-data.md)です。 他のデータ型から変換する方法については、 **xml**データ型を参照してください[XML データのインスタンスを作成する](../../relational-databases/xml/create-instances-of-xml-data.md)です。
  
## <a name="text-and-image-data-types"></a>テキストおよびイメージ データ型
データの自動型変換はサポートされていません、**テキスト**と**イメージ**データ型。 明示的に変換することができます**テキスト**データを文字データ、および**イメージ**データ**バイナリ**または**varbinary**が、最大の長さが 8000バイト数です。 文字を含む文字式を変換するなど、不適切な変換しようとすると、 **int**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー メッセージが返されます。
  
## <a name="output-collation"></a>出力の照合順序  
CAST または CONVERT の入出力が文字列である場合、出力では入力と同じ照合順序および照合順序ラベルが使用されます。 入力が文字列ではない場合、出力ではデータベースの既定の照合順序、および強制可能な既定照合順序の照合順序ラベルが使用されます。 詳細については、次を参照してください。[照合の優先順位 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/collation-precedence-transact-sql.md).
  
出力に別の照合順序を割り当てるには、CAST 関数または CONVERT 関数の結果式に COLLATE 句を適用します。 例:
  
`SELECT CAST('abc' AS varchar(5)) COLLATE French_CS_AS`
  
## <a name="truncating-and-rounding-results"></a>切り捨てと丸め処理の結果
文字やバイナリ式に変換する場合 (**char**、 **nchar**、 **nvarchar**、 **varchar**、**バイナリ**、または**varbinary**)、別のデータ型の式にデータを切り捨てて、のみ部分的に表示されているか、結果が小さすぎて表示できないため、エラーが返されます。 変換**char**、 **varchar**、 **nchar**、 **nvarchar**、**バイナリ**、および**varbinary**次の表に示す変換を除き、切り捨てられます。
  
|変換前のデータ型|変換後のデータ型|結果|  
|---|---|---|
|**int**、 **smallint**、または**tinyint**|**char**|*|  
||**varchar**|*|  
||**nchar**|E|  
||**nvarchar**|E|  
|**money**、 **smallmoney**、**数値**、 **decimal**、 **float**、または**real**|**char**|E|  
||**varchar**|E|  
||**nchar**|E|  
||**nvarchar**|E|  
  
\*= 結果が短すぎて表示できません。 E  = 結果が短すぎて表示できない場合エラーが返される。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみのラウンド トリップ変換、変換元のデータ型からデータ型に変換し、再度がバージョンごとにについて同じ値を生成していることを保証します。 次にラウンド トリップ変換の例を示します。
  
```sql
DECLARE @myval decimal (5, 2);  
SET @myval = 193.57;  
SELECT CAST(CAST(@myval AS varbinary(20)) AS decimal(10,5));  
-- Or, using CONVERT  
SELECT CONVERT(decimal(10,5), CONVERT(varbinary(20), @myval));  
```  
  
> [!NOTE]  
>  構築しないでください**バイナリ**値であり、これを数値データ型に分類されるデータ型に変換します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]限りませんの結果、 **decimal**または**数値**データ型に変換**バイナリ**のバージョン間で同じになります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
次の例では、短すぎて表示できない結果式を示します。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, SUBSTRING(p.Title, 1, 25) AS Title,
    CAST(e.SickLeaveHours AS char(1)) AS [Sick Leave]  
FROM HumanResources.Employee e JOIN Person.Person p 
    ON e.BusinessEntityID = p.BusinessEntityID  
WHERE NOT e.BusinessEntityID >5;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```   
FirstName   LastName      Title   Sick Leave
---------   ------------- ------- --------`
Ken         Sanchez       NULL   *
Terri       Duffy         NULL   *
Roberto     Tamburello    NULL   *
Rob         Walters       NULL   *
Gail        Erickson      Ms.    *
(5 row(s) affected)  
```
  
小数点の位置が異なるデータ型を変換すると、場合によって結果の値が切り捨てられるか丸められます。 次の表はその動作です。
  
|From|変換先|動作|  
|---|---|---|
|**numeric**|**numeric**|四捨五入|  
|**numeric**|**int**|切り捨て|  
|**numeric**|**money**|四捨五入|  
|**money**|**int**|四捨五入|  
|**money**|**numeric**|四捨五入|  
|**float**|**int**|切り捨て|  
|**float**|**numeric**|四捨五入<br /><br /> 変換**float**値を科学的表記法を使用する**decimal**または**数値**17 桁のみを有効桁数の値に制限されます。 有効桁数が 17 より多い値はゼロに丸められます。|  
|**float**|**datetime**|四捨五入|  
|**datetime**|**int**|四捨五入|  
  
たとえば、値 10.6496 および-10.6496 切り捨て場合やへの変換中に丸められます**int**または**数値**型。
  
```sql
SELECT  CAST(10.6496 AS int) as trunc1,
         CAST(-10.6496 AS int) as trunc2,
         CAST(10.6496 AS numeric) as round1,
         CAST(-10.6496 AS numeric) as round2;
 ```
クエリの結果は次の表に示します。
 
|trunc1|trunc2|round1|round2|
|---|---|---|---|
|10|-10|11|-11|
 
変換後のデータ型の小数点以下桁数が変換前のデータ型の小数点以下桁数より少ない場合は、値が丸められます。 たとえば、次の変換の結果は`$10.3497`:
  
`SELECT CAST(10.3496847 AS money);`
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数値以外の場合、エラー メッセージを返します**char**、 **nchar**、 **varchar**、または**nvarchar**データに変換されます**int**、 **float**、**数値**、または**decimal**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー時に、空の文字列を返します ("") に変換されます**数値**または**decimal**です。
  
## <a name="certain-datetime-conversions-are-nondeterministic"></a>一部の datetime 変換は非決定的関数
次の表は、文字列から datetime への変換が非決定的であるスタイルを示します。
  
|||  
|-|-|  
|100 未満のすべてのスタイル<sup>1</sup>|106|  
|107|109|  
|113|130|  
  
<sup>1</sup>スタイル 20 と 21 を除く
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)
以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]からキャスト操作、補助文字 (SC) の照合順序を使用する場合、 **nchar**または**nvarchar**を**nchar**または**nvarchar**短いの型がサロゲート ペア内は切り捨てられません。 補助文字の前で切り捨てが行わします。 たとえば、次のコード フラグメントのまま`@x`だけが保持`'ab'`です。 補助文字を保持するための十分な領域がありません。
  
```sql
DECLARE @x NVARCHAR(10) = 'ab' + NCHAR(0x10000);  
SELECT CAST (@x AS NVARCHAR(3));  
```  
  
SC の照合順序の動作を使用するときに`CONVERT`とよく似ているは、`CAST`です。
  
## <a name="compatibility-support"></a>互換性サポート
以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、に対する CAST および CONVERT 操作の既定のスタイル**時間**と**datetime2**データ型は、計算列の式内のいずれかの型を使用する場合を除き、121 です。 計算列の場合、既定のスタイルは 0 です。 この動作は、計算列が作成されるとき、自動パラメーター化を含むクエリで使用されるとき、または制約の定義で使用されるときに、計算列に影響を与えます。
  
互換性レベル 110 以上は、既定のスタイル CAST および CONVERT 操作の**時間**と**datetime2**データ型は常に 121 です。 クエリが古い動作に依存する場合は、110 より小さい互換性レベルを使用するか、または影響を受けるクエリで 0 スタイルを明示的に指定してください。
  
データベースを互換性レベル 110 以上にアップグレードしても、ディスクに格納されているユーザー データは変更されません。 このようなデータは手動で適切に修正する必要があります。 たとえば、SELECT INTO を使用して、前に説明した計算列の式を含むソースからテーブルを作成した場合は、計算列の定義自体ではなく、(スタイル 0 を使用する) データが格納されます。 このようなデータは、手動で更新してスタイル 121 に一致させる必要があります。
  
## <a name="BKMK_examples"></a> 使用例  
  
### <a name="a-using-both-cast-and-convert"></a>A. CAST と CONVERT の両方を使用する  
次の各例では、表示価格の最初の桁が `3` である製品について製品名を取得し、その `ListPrice` を `int` 型に変換します。
  
```sql
-- Use CAST  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CAST(ListPrice AS int) LIKE '3%';  
GO  
  
-- Use CONVERT.  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
GO  
```  
  
### <a name="b-using-cast-with-arithmetic-operators"></a>B. CAST を算術演算子と共に使用する  
次の例は、1 つの列の計算を計算 (`Computed`) 年度累計売上を合計で割ることによって (`SalesYTD`) 手数料のパーセンテージで (`CommissionPCT`)。 この結果に変換される、`int`最も近い整数に丸められた後にデータを入力します。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT CAST(ROUND(SalesYTD/CommissionPCT, 0) AS int) AS Computed  
FROM Sales.SalesPerson   
WHERE CommissionPCT != 0;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
```  
Computed
------
379753754
346698349
257144242
176493899
281101272
0  
301872549
212623750
298948202
250784119
239246890
101664220
124511336
97688107
(14 row(s) affected)  
```  
  
### <a name="c-using-cast-to-concatenate"></a>C. CAST を使用して連結する  
次の例では、キャストを使用する文字式を連結します。 AdventureWorksDW を使用します。
  
```sql
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice  
FROM dbo.DimProduct  
WHERE ListPrice BETWEEN 350.00 AND 400.00;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09  
```  
  
### <a name="d-using-cast-to-produce-more-readable-text"></a>D. CAST を使用してテキストをさらに読みやすくする  
次の例に変換する、選択リストでキャストを使用して、`Name`列を**char (10)**列です。 AdventureWorksDW を使用します。
  
```sql
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Name        UnitPrice
----------  ---------
Long-Sleev  31.2437
Long-Sleev  32.4935
Long-Sleev  49.99  
```  
  
### <a name="e-using-cast-with-the-like-clause"></a>E. CAST を LIKE 句と共に使用する  
次の例では、`money` 列 `SalesYTD` を `int` 型に変換して、次に `char(20)` 句と共に使用できるよう `LIKE` 列に変換します。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, s.SalesYTD, s.BusinessEntityID  
FROM Person.Person AS p   
JOIN Sales.SalesPerson AS s   
    ON p.BusinessEntityID = s.BusinessEntityID  
WHERE CAST(CAST(s.SalesYTD AS int) AS char(20)) LIKE '2%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
FirstName        LastName            SalesYTD         SalesPersonID
---------------- ------------------- ---------------- -------------
Tsvi             Reiter              2811012.7151      279
Syed             Abbas               219088.8836       288
Rachel           Valdez              2241204.0424      289
(3 row(s) affected)  
```
  
### <a name="f-using-convert-or-cast-with-typed-xml"></a>F. CONVERT または CAST を、型指定された XML と共に使用する  
使用して表示する例をいくつかの変換を使用して型指定された XML に変換するは、次のとおり、 [XML データ型と列 & #40 です。SQL Server &#41;](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md).
  
次の例では、空白、テキスト、およびマークアップのある文字列を、型指定された XML に変換し、すべての余分な空白 (ノード間の境界の空白) を削除します。
  
```sql
CONVERT(XML, '<root><child/></root>')  
```  
  
次の例では、空白、テキスト、およびマークアップのある同様の文字列を、型指定された XML に変換し、すべての余分な空白 (ノード間の境界の空白) を保持します。
  
```sql
CONVERT(XML, '<root>          <child/>         </root>', 1)  
```  
  
次の例では、空白、テキスト、マークアップのある文字列を、型指定された XML にキャストします。
  
```sql
CAST('<Name><FName>Carol</FName><LName>Elliot</LName></Name>'  AS XML)  
```  
  
例については、次を参照してください。 [XML データのインスタンスを作成する](../../relational-databases/xml/create-instances-of-xml-data.md)です。
  
### <a name="g-using-cast-and-convert-with-datetime-data"></a>G. CAST および CONVERT を datetime データと共に使用する  
次の例では、現在の日付と時刻を表示し、`CAST` を使用して現在の日付と時刻を文字列データ型に変更した後、`CONVERT` を使用して `ISO 8901` 形式で日付と時刻を表示します。
  
```sql
SELECT   
   GETDATE() AS UnconvertedDateTime,  
   CAST(GETDATE() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), GETDATE(), 126) AS UsingConvertTo_ISO8601  ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast              UsingConvertTo_ISO8601
----------------------- ---------------------- ------------------------------
2006-04-18 09:58:04.570 Apr 18 2006  9:58AM    2006-04-18T09:58:04.570
(1 row(s) affected)  
```
  
次の例は、前の例とほぼ逆になります。 例では、文字データを使用して、日付と時刻を表示する`CAST`に文字データを変更する、`datetime`データ型、および、使用`CONVERT`に文字データを変更する、`datetime`データ型。
  
```sql
SELECT   
   '2006-04-25T15:50:59.997' AS UnconvertedText,  
   CAST('2006-04-25T15:50:59.997' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2006-04-25T15:50:59.997', 126) AS UsingConvertFrom_ISO8601 ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2006-04-25T15:50:59.997 2006-04-25 15:50:59.997 2006-04-25 15:50:59.997
(1 row(s) affected)  
```
  
### <a name="h-using-convert-with-binary-and-character-data"></a>H. CONVERT をバイナリ データおよび文字データと共に使用する  
以下は、さまざまなスタイルを使用してバイナリ データと文字データを変換した結果を示す例です。
  
```sql
--Convert the binary value 0x4E616d65 to a character value.  
SELECT CONVERT(char(8), 0x4E616d65, 0) AS [Style 0, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, binary to character
----------------------------
Name  
(1 row(s) affected)  
```
 
次の例では、スタイル 1 が切り捨てられるように結果を強制する方法を示します。 切り捨てが原因の文字を含む 0 x 結果です。  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 1) AS [Style 1, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, binary to character
------------------------------
0x4E616D
(1 row(s) affected)  
```  
 
次の例は、エントリのため、スタイル 2 は、結果が切り捨てられません文字 0x が結果に含まれません。  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 2) AS [Style 2, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, binary to character
------------------------------
4E616D65
(1 row(s) affected)  
```
  
'Name' の文字の値をバイナリ値に変換します。  
```sql
SELECT CONVERT(binary(8), 'Name', 0) AS [Style 0, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, character to binary
----------------------------
0x4E616D6500000000
(1 row(s) affected)  
```
  
```sql
SELECT CONVERT(binary(4), '0x4E616D65', 1) AS [Style 1, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, character to binary
---------------------------- 
0x4E616D65
(1 row(s) affected)  
```  

```sql
SELECT CONVERT(binary(4), '4E616D65', 2) AS [Style 2, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, character to binary  
----------------------------------  
0x4E616D65
(1 row(s) affected)  
```  
  
### <a name="i-converting-date-and-time-data-types"></a>I. 日付と時刻のデータ型の変換  
次の例では、date、time、および datetime データ型の変換の例を示します。
  
```sql
DECLARE @d1 date, @t1 time, @dt1 datetime;  
SET @d1 = GETDATE();  
SET @t1 = GETDATE();  
SET @dt1 = GETDATE();  
SET @d1 = GETDATE();  
-- When converting date to datetime the minutes portion becomes zero.  
SELECT @d1 AS [date], CAST (@d1 AS datetime) AS [date as datetime];  
-- When converting time to datetime the date portion becomes zero   
-- which converts to January 1, 1900.  
SELECT @t1 AS [time], CAST (@t1 AS datetime) AS [time as datetime];  
-- When converting datetime to date or time non-applicable portion is dropped.  
SELECT @dt1 AS [datetime], CAST (@dt1 AS date) AS [datetime as date], 
   CAST (@dt1 AS time) AS [datetime as time];  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-using-cast-and-convert"></a>J. CAST および CONVERT を使用します。  
この例は、ある製品の製品の名前を取得、`3`に変換し、表示価格の最初の桁で、`ListPrice`に**int**です。AdventureWorksDW を使用します。
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(ListPrice AS int) LIKE '3%';  
```  
  
この例では、CAST ではなく CONVERT を使用して、同じクエリを使用します。 AdventureWorksDW を使用します。
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
```  
  
### <a name="k-using-cast-with-arithmetic-operators"></a>K. CAST を算術演算子と共に使用する  
次の例は、製品の単価を割ることによって、1 つの列の計算を計算 (`UnitPrice`) して割引率 (`UnitPriceDiscountPct`)。 この結果に変換される、`int`最も近い整数に丸められた後にデータを入力します。 AdventureWorksDW を使用します。
  
```sql
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,  
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice  
FROM dbo.FactResellerSales  
WHERE SalesOrderNumber = 'SO47355'   
      AND UnitPriceDiscountPct > .02;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1  
```  
  
### <a name="l-using-cast-with-the-like-clause"></a>L. CAST を LIKE 句と共に使用する  
次の例では、変換、 **money**列`ListPrice`を**int**型とし、さらに、 **char(20)** LIKE 句と共に使用できるように入力します。 AdventureWorksDW を使用します。
  
```sql
SELECT EnglishProductName AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(CAST(ListPrice AS int) AS char(20)) LIKE '2%';  
```  
  
### <a name="m-using-cast-and-convert-with-datetime-data"></a>M. CAST および CONVERT を datetime データと共に使用する  
次の例は、現在の日付と時刻を使用して、文字データ型に現在の日付と時刻を変更するキャストされ、CONVERT を使用してが日付と時刻を ISO 8601 形式で表示されます。 AdventureWorksDW を使用します。
  
```sql
SELECT TOP(1)  
   SYSDATETIME() AS UnconvertedDateTime,  
   CAST(SYSDATETIME() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), SYSDATETIME(), 126) AS UsingConvertTo_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast                     UsingConvertTo_ISO8601  
---------------------   ---------------------------   ---------------------------  
07/20/2010 1:44:31 PM   2010-07-20 13:44:31.5879025   2010-07-20T13:44:31.5879025  
```  
  
次の例は、前の例とほぼ逆になります。 例では、文字データとして、日付と時刻を表示、キャストを使用して、文字データを変更する、 **datetime**データ型、および、使用する文字データを変更する変換、 **datetime**データ型。 AdventureWorksDW を使用します。
  
```sql
SELECT TOP(1)   
   '2010-07-25T13:50:38.544' AS UnconvertedText,  
CAST('2010-07-25T13:50:38.544' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2010-07-25T13:50:38.544', 126) AS UsingConvertFrom_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2010-07-25T13:50:38.544 07/25/2010 1:50:38 PM   07/25/2010 1:50:38 PM  
```  
  
## <a name="see-also"></a>参照
[データ型の変換 (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
[システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[国際化に対応した Transact-SQL ステートメントの記述](../../relational-databases/collations/write-international-transact-sql-statements.md)
  

