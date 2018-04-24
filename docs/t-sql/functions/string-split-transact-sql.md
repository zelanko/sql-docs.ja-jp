---
title: STRING_SPLIT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5204f8df5f2267421c27528ef85126e118fe56b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  指定した区切り記号を使用して文字式を分割します。  
  
> [!NOTE]  
>  **STRING_SPLIT** 関数は、互換性レベル 130 でのみ使用できます。 データベースの互換性レベルが 130 よりも低い場合、SQL Server は **STRING_SPLIT** 関数を見つけて実行することができません。 次のコマンドを利用し、データベースの互換性レベルを変更できます。  
> ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
>   
>  新しい Azure SQL Database であっても、互換性レベル 120 が既定値の場合があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>引数  
 *string*  
 任意の文字型 (つまり **nvarchar**、**varchar**、**nchar**、または **char**) の[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 *separator*  
 任意の文字型の 1 文字の[式](../../t-sql/language-elements/expressions-transact-sql.md)です (**nvarchar(1)**、**varchar(1)**、**nchar(1)**、**char(1)** など)。連結する文字列の区切り文字として使用されます。  
  
## <a name="return-types"></a>戻り値の型  
 フラグメントを含む単一列のテーブルを返します。 列の名前は **value** です。 入力引数のいずれかが **nvarchar** または **nchar** の場合は、**nvarchar** を返します。 それ以外の場合は **varchar** を返します。 戻り値の型の長さは、文字列引数の長さと同じです。  
  
## <a name="remarks"></a>Remarks  
 **STRING_SPLIT** は、分割される文字列と、文字列の分割に使用される区切り記号を受け取ります。 サブ文字列を含む単一列のテーブルを返します。 たとえば、区切り記号としてスペース文字を使用する次のステートメントの `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');` は、次の結果のテーブルを返します。  
  
|value|  
|-----------|  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|amet.|  
  
 入力文字列が **NULL** の場合、**STRING_SPLIT** テーブル値関数は空のテーブルを返します。  
  
 **STRING_SPLIT** を使用するには、130 以上の互換モードが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-split-comma-separated-value-string"></a>A. コンマ区切り値文字列を分割する  
 コンマ区切り値リストを解析し、空ではないすべてのトークンを返します。  
  
```  
  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
  
```  
  
 区切り記号の間に何もない場合、STRING_SPLIT は空の文字列を返します。 条件 RTRIM(value) <> '' を指定すると、空のトークンが削除されます。  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. 列内のコンマ区切り値文字列を分割する  
 次の例のように、Product テーブルには、コンマで区切られたタグのリストを含む列があります。  
  
|ProductId|[オブジェクト名]|Tags|  
|---------------|----------|----------|  
|@shouldalert|Full-Finger Gloves|clothing,road,touring,bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike,mountain|  
  
 次のクエリは、タグの各リストを変換し、元の行と結合します。  
  
```  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|ProductId|[オブジェクト名]|value|  
|---------------|----------|-----------|  
|@shouldalert|Full-Finger Gloves|clothing|  
|@shouldalert|Full-Finger Gloves|road|  
|@shouldalert|Full-Finger Gloves|touring|  
|@shouldalert|Full-Finger Gloves|bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike|  
|3|HL Mountain Frame|mountain|  
  
### <a name="c-aggregation-by-values"></a>C. 値による集計  
 ユーザーは、製品数で並べ替え、タグごとに製品数を表示するレポートを作成し、2 製品を超えるタグのみに絞り込む必要があります。  
  
```  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>D. タグ値で検索する  
 開発者はキーワードで記事を検索するクエリを作成する必要があります。 この場合、次のクエリを使用できます。  
  
 1 つのタグ (clothing) を持つ製品を検索するには:  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
 指定された 2 つのタグ (clothing と road) を持つ製品を検索するには:  
  
```  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>E. 値のリストで行を検索する  
 開発者は、ID のリストで記事を検索するクエリを作成する必要があります。 この場合、次のクエリを使用できます。  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
 これは、アプリケーション レイヤーまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] で動的な SQL 文字列を作成するか、LIKE 演算子を使用するなど、一般的なアンチパターンの置き換えです。  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>参照  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [文字列関数 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
