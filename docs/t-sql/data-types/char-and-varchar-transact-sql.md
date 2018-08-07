---
title: char および varchar (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8e8eb43fd5dffa9ae1047730bcb17075d2204d8
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454886"
---
# <a name="char-and-varchar-transact-sql"></a>char および varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

これらのデータ型は、固定長または可変長です。  
  
## <a name="arguments"></a>引数  
**char** [ ( *n* ) ] 固定長の Unicode 以外の文字列データです。 *n* では文字列の長さを定義し、指定できる値の範囲は 1 ～ 8,000 です。 ストレージのサイズは *n* バイトです。 **char** の ISO シノニムは、**character** です。
  
**varchar** [ ( *n* | **max** ) ] 可変長の Unicode 以外の文字列データです。 *n* では文字列の長さを定義し、指定できる値の範囲は 1 ～ 8,000 です。 **max** は最大格納サイズが 2^31-1 バイト (2 GB) であることを示します。 格納サイズは、入力したデータの実際の長さ + 2 バイトとなります。 **varchar** の ISO シノニムは、**charvarying** または **charactervarying** です。
  
## <a name="remarks"></a>Remarks  
データ定義または変数宣言ステートメントで *n* を指定しないと、既定の長さは 1 になります。 CAST 関数および CONVERT 関数で *n* を指定しない場合は、既定の長さは 30 になります。
  
COLLATE 句で特定の照合順序を指定しない限り、**char** 型または **varchar** 型を使用するオブジェクトにはデータベースの既定の照合順序が割り当てられます。 照合順序によって、文字型データの格納に使用されるコード ページが制御されます。
  
サイトで複数の言語をサポートする場合は、文字変換から生じる問題を最小限にするために、Unicode の **nchar** 型または **nvarchar** 型を使用することを検討してください。 **char** 型または **varchar** 型を使用する場合は、次のように使い分けます。
- 列データ エントリのサイズが一定の場合は、**char** を使用します。  
- 列データ エントリのサイズが大幅に変化する場合は、**varchar** を使用します。  
- 列データ エントリのサイズが大幅に異なり、また 8,000 バイトを超える可能性がある場合は、**varchar(max)** 型を使用します。  
  
CREATE TABLE または ALTER TABLE 実行時に SET ANSI_PADDING が OFF に設定されている場合、NULL として定義されている **char** 型の列は **varchar** 型として扱われます。
  
照合順序のコード ページで 2 バイト文字が使用されている場合、記憶領域のサイズは *n* バイトのままです。 文字列によって、*n* バイトのストレージ サイズは *n* 文字未満になる可能性があります。

> [!WARNING]
> Null 以外の varchar(max) または nvarchar(max) の各列には、24 バイトの追加の固定割り当てが必要で、これは並べ替え操作中の 8,060 バイトの行制限におけるカウント対象となります。 これにより、テーブル内に作成できる Null 以外の varchar(max) または nvarchar(max) の列数について、暗黙的な制限が生じます。  
テーブルの作成時やデータ挿入時に、最大行サイズが許容最大値の 8060 バイトを超えるという通常の警告以外の、特別なエラーは提供されません。 この大きな行サイズが原因で、クラスター化インデックス キーの更新や列セット全体の並べ替えなどの通常操作の一部でエラー (エラー 512 など) が発生する可能性があります。これは操作を実行するまでユーザーは予測することができません。
  
##  <a name="_character"></a> 文字データの変換  
文字式を異なるサイズの文字型に変換する場合、値が新しいデータ型にとって長すぎるときは、切り捨てられます。 **uniqueidentifier** 型は、文字式からの変換のための文字型と見なされるため、文字型に変換する場合は切り捨てルールが適用されます。 例については、後の「例」のセクションを参照してください。
  
文字式がデータ型やサイズが異なる文字式に変換される場合 (**char(5)** から **varchar(5)** や、**char(20)** から **char(15)** など)、入力値の照合順序が変換後の値に割り当てられます。 文字式でない式が文字型に変換される場合、現在のデータベースの既定の照合順序が変換後の値に割り当てられます。 どちらの場合でも、[COLLATE](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9) 句を使用して特定の照合を割り当てることができます。
  
> [!NOTE]  
>  コード ページ変換は **char** および **varchar** データ型に対してはサポートされていますが、**text** データ型に対してはサポートされていません。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と同様に、コード ページ変換中のデータの喪失は報告されません。  
  
文字式を **numeric** 型の概算値に変換する場合、その文字式は指数表記を含むことができます。指数表記とは、小文字の e または大文字の E の後に必要に応じてプラス記号 (+) またはマイナス記号 (-) を付け、その後に数字を付けた表記です。
  
文字式を正確な **numeric** 型に変換する場合、その文字式は、数字と小数点から構成されている必要があります。必要に応じて、プラス記号 (+) またはマイナス記号 (-) を付けることができます。 先頭の空白は無視されます。 123,456.00 の桁区切り記号のようにコンマを区切り記号として文字列内で使用することはできません。
  
文字式を **money** 型または **smallmoney** 型に変換する場合、その文字式も、小数点とドル記号 ($) を含むことができます。 $123,456.00 のようにコンマを区切り記号として使用できます。
  
## <a name="examples"></a>使用例  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. 変数宣言で使用された場合の n の既定値  
次の例は、`char` データ型および `varchar` データ型が変数宣言で使用された場合に、*n* の既定値が 1 になることを示しています。
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>B. CAST および CONVERT と共に varchar が使用された場合の n の既定値  
次の例は、`char` データ型または `varchar` データ型が `CAST` 関数および `CONVERT` 関数と共に使用された場合に、*n* の既定値が 30 になることを示しています。
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>C. 表示用にデータを変換する  
次の例では、2 つの列を文字型に変換し、表示されるデータに特定の形式を適用するスタイルを指定します。 **money** 型は文字データに変換され、スタイル 1 が適用されます。それによって、整数部分は 3 桁ごとにコンマで区切られ、小数点以下は 2 桁までの値が表示されます。 **datetime** 型は文字データに変換され、スタイル 3 が適用されます。それによって、dd/mm/yy の形式でデータが表示されます。 WHERE 句の **money** 型は文字タイプにキャストされ、文字列比較操作が実行されます。
  
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
  
次の例は、変換後のデータ型に対して値が長すぎる場合のデータの切り捨てを示します。 **uniqueidentifier** 型は 36 文字に制限されているため、この長さを超える文字は切り捨てられます。
  
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
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[データベース サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-database.md)
  
  
