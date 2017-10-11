---
title: "部分文字列 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUBSTRING
- SUBSTRING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- portion of expression returned [SQL Server]
- part of expression returned [SQL Server]
- SUBSTRING function
- offsets [SQL Server]
- binary [SQL Server], returning part of
- expressions [SQL Server], part returned
- characters [SQL Server], returning part of
ms.assetid: a19c808f-aaf9-4a69-af59-b1a5fc3e5c4c
caps.latest.revision: 65
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7f36ec82c65e5d52c2186c67033adddbf1700c4d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="substring-transact-sql"></a>SUBSTRING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、文字、バイナリ、テキスト、またはイメージ型の式の一部を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SUBSTRING ( expression ,start , length )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **文字**、**バイナリ**、**テキスト**、 **ntext**、または**イメージ**[式](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *開始*  
 整数または**bigint**返される文字の開始位置を指定する式。 (番号は、式の最初の文字が 1 である 1 に基づいて、意味です) です。 場合*開始*が 1 より小さい、返される式で指定されている最初の文字から始まります*式*です。 返される文字数の合計の最大値は、この場合、*開始* + *長さ*- 1 と 0 です。 場合*開始*数よりも大きい値式の文字は、長さゼロの式が返されます。  
  
 *length*  
 正の整数または**bigint**文字数を指定する式、*式*が返されます。 場合*長さ*は負の場合、エラーが生成され、ステートメントは終了します。 場合の合計*開始*と*長さ*内の文字数よりも大きい*式*、値式全体で始まる*開始*が返されます。  
  
## <a name="return-types"></a>戻り値の型  
 場合、データが文字を返します*式*はサポートされている文字データ型の 1 つです。 場合、バイナリ データを返します*式*はサポートされている 1 つ**バイナリ**データ型。 返される文字列のデータ型は、指定した式のデータ型と同じです。ただし、次の表の場合は例外です。  
  
|指定した式|戻り値の型|  
|--------------------------|-----------------|  
|**char**/**varchar**/**テキスト**|**varchar**|  
|**nchar**/**nvarchar**/**ntext**|**nvarchar**|  
|**バイナリ**/**varbinary**/**イメージ**|**varbinary**|  
  
## <a name="remarks"></a>解説  
 値は、*開始*と*長さ*の文字数で指定する必要があります**ntext**、 **char**、または**varchar**データ型とのバイト**テキスト**、**イメージ**、**バイナリ**、または**varbinary**データ型。  
  
 *式*する必要があります**varchar (max)**または**varbinary (max)**ときに、*開始*または*長さ*2,147, 483,647 を超える値が含まれています。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 補助文字 (SC) の照合順序を使用する場合両方*開始*と*長さ*内の各サロゲート ペアの数*式*単一の文字として。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-substring-with-a-character-string"></a>A. SUBSTRING に文字列を使用する  
 次の例では、文字列の一部分のみを返す方法を示しています。 `sys.databases`テーブル、次のクエリ名を返します、システム データベース 最初の列では、2 番目の列で、データベースと最後の列に 3 番目と 4 番目の文字の最初の文字です。  
  
```  
SELECT name, SUBSTRING(name, 1, 1) AS Initial ,
SUBSTRING(name, 3, 2) AS ThirdAndFourthCharacters
FROM sys.databases  
WHERE database_id < 5;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

|name |Initial |ThirdAndFourthCharacters|
|---|--|--|
|master  |m  |st |
|tempdb  |t  |管理パック |
|model   |m  |de |
|msdb    |m  |db |


  
 ここでは、2 つ目を表示する方法、3 番目と 4 番目の文字を文字列定数の`abcdef`します。  
  
```  
SELECT x = SUBSTRING('abcdef', 2, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x  
----------  
bcd  
  
(1 row(s) affected)
```  
  
### <a name="b-using-substring-with-text-ntext-and-image-data"></a>B. SUBSTRING に text、ntext、および image 型のデータを使用する  
  
> [!NOTE]  
>  次の例を実行するにインストールする必要があります、 **pubs**データベース。  
  
 次の例のそれぞれから最初の 10 文字を返す方法を示しています、**テキスト**と**イメージ**内のデータ列、`pub_info`のテーブル、`pubs`データベース。 **テキスト**としてデータが返されます**varchar**、および**イメージ**としてデータが返される**varbinary**です。  
  
```  
USE pubs;  
SELECT pub_id, SUBSTRING(logo, 1, 10) AS logo,   
   SUBSTRING(pr_info, 1, 10) AS pr_info  
FROM pub_info  
WHERE pub_id = '1756';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 pub_id logo    pr_info
------ ---------------------- ----------
1756   0x474946383961E3002500 This is sa

(1 row(s) affected)
```  
  
 次の例は、両方で SUBSTRING の効果を示します**テキスト**と**ntext**データ。 最初に、この例での新しいテーブルを作成、`pubs`という名前のデータベース`npub_info`です。 例を次に、作成、`pr_info`内の列、`npub_info`テーブルの最初の 80 文字から、`pub_info.pr_info`列を追加し、`ü`最初の文字として。 最後に、`INNER JOIN`すべてのパブリッシャー id 番号を取得し、`SUBSTRING`両方の**テキスト**と**ntext**パブリッシャー情報列です。  
  
```  
IF EXISTS (SELECT table_name FROM INFORMATION_SCHEMA.TABLES   
      WHERE table_name = 'npub_info')  
   DROP TABLE npub_info;  
GO  
-- Create npub_info table in pubs database. Borrowed from instpubs.sql.  
USE pubs;  
GO  
CREATE TABLE npub_info  
(  
 pub_id char(4) NOT NULL  
    REFERENCES publishers(pub_id)  
    CONSTRAINT UPKCL_npubinfo PRIMARY KEY CLUSTERED,  
pr_info ntext NULL  
);  
  
GO  
  
-- Fill the pr_info column in npub_info with international data.  
RAISERROR('Now at the inserts to pub_info...',0,1);  
  
GO  
  
INSERT npub_info VALUES('0736', N'üThis is sample text data for New Moon Books, publisher 0736 in the pubs database')  
,('0877', N'üThis is sample text data for Binnet & Hardley, publisher 0877 in the pubs databa')  
,('1389', N'üThis is sample text data for Algodata Infosystems, publisher 1389 in the pubs da')  
,('9952', N'üThis is sample text data for Scootney Books, publisher 9952 in the pubs database')  
,('1622', N'üThis is sample text data for Five Lakes Publishing, publisher 1622 in the pubs d')  
,('1756', N'üThis is sample text data for Ramona Publishers, publisher 1756 in the pubs datab')  
,('9901', N'üThis is sample text data for GGG&G, publisher 9901 in the pubs database. GGG&G i')  
,('9999', N'üThis is sample text data for Lucerne Publishing, publisher 9999 in the pubs data');  
GO  
-- Join between npub_info and pub_info on pub_id.  
SELECT pr.pub_id, SUBSTRING(pr.pr_info, 1, 35) AS pr_info,  
   SUBSTRING(npr.pr_info, 1, 35) AS npr_info  
FROM pub_info pr INNER JOIN npub_info npr  
   ON pr.pub_id = npr.pub_id  
ORDER BY pr.pub_id ASC;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-substring-with-a-character-string"></a>C. SUBSTRING に文字列を使用する  
 次の例では、文字列の一部分のみを返す方法を示しています。 このクエリでは、`dbo.DimEmployee` テーブルから、最初の列に姓を、2 番目の列には名のイニシャルのみを返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUBSTRING(FirstName, 1, 1) AS Initial  
FROM dbo.DimEmployee  
WHERE LastName LIKE 'Bar%'  
ORDER BY LastName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName             Initial
-------------------- -------
Barbariol            A
Barber               D
Barreto de Mattos    P
```  
  
 次の例は、2 つ目を返す方法を示します、3 番目と 4 番目の文字を文字列定数の`abcdef`します。  
  
```  
USE ssawPDW;  
  
SELECT TOP 1 SUBSTRING('abcdef', 2, 3) AS x FROM dbo.DimCustomer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x
-----
bcd
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



