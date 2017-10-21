---
title: "char および varchar (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- varchar
- varchar_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fixed-length data types [SQL Server]
- character data type
- char data type
- varchar(max) data type
- variable-length data types [SQL Server]
- varchar data type
ms.assetid: 282cd982-f4fb-4b22-b2df-9e8478f13f6a
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c7bcb0e8ad7f8904703bd6c979b00aa30dd5348
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="char-and-varchar-transact-sql"></a>char および varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

これらのデータ型では、固定長または可変長のどちらかです。  
  
## <a name="arguments"></a>引数  
**char** [(  *n*  )] 固定長の Unicode 以外の文字列データです。 *n*文字列の長さを定義し、1 ~ 8,000 の値でなければなりません。 ストレージのサイズは *n* バイトです。 ISO シノニムは、 **char**は**文字**です。
  
**varchar** [(  *n*   |  **max** )] 可変長の Unicode 以外の文字列データです。 *n*文字列の長さを定義し、1 ~ 8,000 の値を指定できます。 **max**ストレージの最大サイズが 2 であることを示します。 ^ 31-1 バイト (2 GB)。 格納サイズは、入力したデータの実際の長さ + 2 バイトとなります。 ISO シノニム**varchar**は**charvarying**または**charactervarying**です。
  
## <a name="remarks"></a>解説  
ときに *n* が指定されていないデータ定義または変数宣言ステートメントで、既定の長さは 1 です。 ときに *n* が指定されていない、CAST および CONVERT 関数を使用する場合、既定の長さは 30 です。
  
使用するオブジェクト**char**または**varchar** COLLATE 句を使用して、特定の照合順序が割り当てられていない限り、データベースの既定の照合順序を割り当てられています。 照合順序によって、文字型データの格納に使用されるコード ページが制御されます。
  
複数の言語をサポートするサイトがある場合、Unicode を使用して検討**nchar**または**nvarchar**文字変換から生じる問題を最小限に抑えるのデータ型。 使用する場合**char**または**varchar**次をお勧めします。
- 使用して**char**列データ エントリのサイズが一定の場合。  
- 使用して**varchar**列データ エントリのサイズを大きく変化する場合。  
- 使用して**varchar (max)**と列データ エントリのサイズが大きく変化し、サイズが 8,000 バイトを超える場合があります。  
  
CREATE TABLE または ALTER TABLE を実行すると、SET ANSI_PADDING が OFF の場合、 **char**として NULL が処理済みとして定義されている列**varchar**です。
  
ストレージのサイズがまだは照合順序コード ページは、2 バイト文字を使用するときに *n* バイトです。 文字の文字列のストレージ サイズに応じて *n* バイトより小さい *n* 文字です。

> [!WARNING]
> 各 null varchar (max) または nvarchar (max) 列には、並べ替え操作中に 8,060 バイトの行の制限に対してカウントする追加の固定割り当ての 24 バイトが必要です。 これは、暗黙的な null varchar (max)、またはテーブル内に作成できる nvarchar (max) 列の数に制限を作成できます。  
テーブルの作成時やデータ挿入時に、最大行サイズが許容最大値の 8060 バイトを超えるという通常の警告以外の、特別なエラーは提供されません。 この大きな行サイズが原因で、クラスター化インデックス キーの更新や列セット全体の並べ替えなどの通常操作の一部でエラー (エラー 512 など) が発生する可能性があります。これは操作を実行するまでユーザーは予測することができません。
  
##  <a name="_character"></a>文字データの変換  
文字式を異なるサイズの文字型に変換する場合、値が新しいデータ型にとって長すぎるときは、切り捨てられます。 **Uniqueidentifier**型と見なされます、文字の種類、文字式からの変換のためであるため、文字型に変換する場合は切り捨てルールの対象です。 例については、後の「例」のセクションを参照してください。
  
文字式が変換される場合に別のデータ型やサイズの文字式などから**char (5)**に**varchar (5)**、または**char(20)** に**char (15)**、変換後の値を入力値の照合順序が割り当てられます。 文字式でない式が文字型に変換される場合、現在のデータベースの既定の照合順序が変換後の値に割り当てられます。 どちらの場合を使用して特定の照合順序を割り当てることができます、 [COLLATE](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)句。
  
> [!NOTE]  
>  コード ページ変換はサポートされて**char**と**varchar**データ型のではなく**テキスト**データ型。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と同様に、コード ページ変換中のデータの喪失は報告されません。  
  
文字式、概算値に変換される文字**数値**データ型は省略可能な指数表記を含めることができます (小文字の e または大文字の E の後に省略可能なプラス (+) またはマイナス記号 (-)、その後、数)。
  
文字式に完全に変換される文字**数値**データ型は、桁数、小数点、および省略可能なので構成する必要がありますプラス (+) またはマイナス記号 (-)。 先頭の空白は無視されます。 123,456.00 の桁区切り記号のようにコンマを区切り記号として文字列内で使用することはできません。
  
文字式に変換する**money**または**smallmoney**小数点とドル記号 ($) のデータ型を含めることもできます。 $123,456.00 のようにコンマを区切り記号として使用できます。
  
## <a name="examples"></a>使用例  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. 変数宣言で使用された場合の n の既定値  
次の例では、既定値の *n* がの場合は 1、`char`と`varchar`データ型の変数宣言で使用されている場合。
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>B. CAST および CONVERT と共に varchar が使用された場合の n の既定値  
次の例を既定値の *n*  30 ときに、`char`または`varchar`データ型を使用、`CAST`と`CONVERT`関数。
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>C. 表示用にデータを変換する  
次の例では、2 つの列を文字型に変換し、表示されるデータに特定の形式を適用するスタイルを指定します。 A **money**型が文字データに変換されが表示されますをコンマで値を小数点の左へ 3 桁ごとおよび 2 桁の数字の小数点の右側に、スタイル 1 が適用されます。 A **datetime**型が文字データに変換し、スタイル 3 を適用すると、形式 dd/月/年のデータが表示されます。 WHERE 句で、 **money**型が文字列比較操作を実行する、文字型にキャストします。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  BusinessEntityID,   
   SalesYTD,   
   CONVERT (varchar(12),SalesYTD,1) AS MoneyDisplayStyle1,   
   GETDATE() AS CurrentDate,   
   CONVERT(varchar(12), GETDATE(), 3) AS DateDisplayStyle3  
FROM Sales.SalesPerson  
WHERE CAST(SalesYTD AS varchar(20) ) LIKE '1%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID SalesYTD              DisplayFormat CurrentDate             DisplayDateFormat  
---------------- --------------------- ------------- ----------------------- -----------------  
278              1453719.4653          1,453,719.47  2011-05-07 14:29:01.193 07/05/11  
280              1352577.1325          1,352,577.13  2011-05-07 14:29:01.193 07/05/11  
283              1573012.9383          1,573,012.94  2011-05-07 14:29:01.193 07/05/11  
284              1576562.1966          1,576,562.20  2011-05-07 14:29:01.193 07/05/11  
285              172524.4512           172,524.45    2011-05-07 14:29:01.193 07/05/11  
286              1421810.9242          1,421,810.92  2011-05-07 14:29:01.193 07/05/11  
288              1827066.7118          1,827,066.71  2011-05-07 14:29:01.193 07/05/11  
```  
  
### <a name="d-converting-uniqueidentifer-data"></a>D. uniqueidentifer 型データを変換する  
次の例では、`uniqueidentifier` 型の値を `char` 型の値に変換します。
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
次の例は、変換後のデータ型に対して値が長すぎる場合のデータの切り捨てを示します。 **Uniqueidentifier**型は 36 文字に制限されて、その長さを超える文字は切り捨てられます。
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[nchar および nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[データベース サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-database.md)
  
  

