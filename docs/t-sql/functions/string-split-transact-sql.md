---
title: "STRING_SPLIT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs: TSQL
helpviewer_keywords: STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 00debf90f1b79a0e38cb883f31479ae5731f40d3
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  指定した区切り記号が挿入された文字式を分割します。  
  
> [!NOTE]  
>  **STRING_SPLIT**関数は、互換性レベル 130 でのみ使用します。 データベースの互換性レベルが 130 より下の場合は、SQL Server ことはできませんを見つけて実行する**STRING_SPLIT**関数。 次のコマンドを利用し、データベースの互換性レベルを変更できます。  
> ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
>   
>  互換性レベル 120 は新しい Azure SQL データベースであっても既定でされる可能性がありますに注意してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>引数  
 *string*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)任意の文字型 (つまり**nvarchar**、 **varchar**、 **nchar**または**char**)。  
  
 *separator*  
 1 つの文字は、[式](../../t-sql/language-elements/expressions-transact-sql.md)任意の文字型 (例: **nvarchar(1)**、 **varchar (1)**、 **nchar (1)**または**char (1)**) 連結された文字列の区切り記号として使用されます。  
  
## <a name="return-types"></a>戻り値の型  
 フラグメントを単一列テーブルを返します。 列の名前は**値**です。 返します**nvarchar**場合、入力引数のいずれかのいずれかの**nvarchar**または**nchar**です。 返しますそれ以外の場合**varchar**です。 戻り値の型の長さは、文字列引数の長さと同じです。  
  
## <a name="remarks"></a>解説  
 **STRING_SPLIT**は分割するか、文字列および文字列の分割に使用される区切り記号を取得します。 部分文字列を含む 1 列のテーブルを返します。 たとえば、次のステートメント`SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');`区切り記号として空白文字を使用して、次の結果のテーブルを返します。  
  
|value|  
|-----------|  
|Lorem|  
|ipsum|  
|dolor|  
|座る|  
|amet です。|  
  
 場合は、入力文字列が**NULL**、 **STRING_SPLIT**テーブル値関数は、空のテーブルを返します。  
  
 **STRING_SPLIT**少なくとも 130 の互換モードです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-split-comma-separated-value-string"></a>A. 分割のコンマ区切り値の文字列  
 値のコンマ区切り一覧を解析し、すべての空でないトークンを返します。  
  
```  
  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
  
```  
  
 区切り記号の間で項目がない場合、STRING_SPLIT は空の文字列を返します。 条件の RTRIM(value) <> ' 空のトークンが削除されます。  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. 分割コンマ区切りの列に値の文字列  
 Product テーブルには、次の例に示すようにタグのコンマで区切った一覧の列があります。  
  
|ProductId|名前|Tags|  
|---------------|----------|----------|  
|1|フル指 Gloves|clothing、road、touring、自転車|  
|2|LL ヘッドセット|自転車|  
|3|HL Mountain Frame|自転車、mountain|  
  
 次のクエリでは、各タグのリストを変換し、元の行と結合します。  
  
```  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|ProductId|名前|value|  
|---------------|----------|-----------|  
|1|フル指 Gloves|clothing|  
|1|フル指 Gloves|road|  
|1|フル指 Gloves|touring|  
|1|フル指 Gloves|自転車|  
|2|LL ヘッドセット|自転車|  
|3|HL Mountain Frame|自転車|  
|3|HL Mountain Frame|mountain|  
  
### <a name="c-aggregation-by-values"></a>C. 値ごとの集計  
 ユーザーは、2 つ以上の製品とタグのみをフィルター処理して、製品の数の順、各タグごとに製品の数を表示するレポートを作成する必要があります。  
  
```  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>D. タグ値で検索します。  
 開発者は、キーワードで記事を検索するクエリを作成する必要があります。 これらは、次のクエリを使用できます。  
  
 1 つのタグ (clothing) での製品を検出するには。  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
 2 つの指定されたタグ (clothing および道路) で製品を検索するには。  
  
```  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>E. 値のリストで行を検索します。  
 開発者は、id の一覧を使用してアーティクルを検索するクエリを作成する必要があります。 これらは、次のクエリを使用できます。  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
 これは、アプリケーション層での動的 SQL 文字列の作成などの共通のアンチ パターンの代わりに、または[!INCLUDE[tsql](../../includes/tsql-md.md)]、または LIKE 演算子を使用しています。  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>参照  
 [左と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ltrim-transact-sql.md)  
 [右 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rtrim-transact-sql.md)  
 [部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)  
 [トリム &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/trim-transact-sql.md)  
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
