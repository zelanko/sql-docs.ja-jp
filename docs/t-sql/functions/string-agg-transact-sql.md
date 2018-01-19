---
title: "STRING_AGG (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STRING_AGG
- STRING_AGG_TSQL
helpviewer_keywords: STRING_AGG function
ms.assetid: 8860ef3f-142f-4cca-aa64-87a123e91206
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: f2bcc8b02b0228dc403fffc4ef1c6b82557872a4
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="stringagg-transact-sql"></a>STRING_AGG (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

文字列式の値を連結し、それらの間の区切り記号の値を格納します。 区切り記号は、文字列の末尾には追加されません。
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STRING_AGG ( expression, separator ) [ <order_clause> ]

<order_clause> ::=   
    WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )   
```

## <a name="arguments"></a>引数 

*separator*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)の`NVARCHAR`または`VARCHAR`の区切り記号として使用される型が文字列を連結します。 リテラルまたは変数を指定できます。 

*式 (expression)*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)任意の型。 式に変換する`NVARCHAR`または`VARCHAR`連結中に種類です。 非文字列型に変換されます`NVARCHAR`型です。


<order_clause>   
使用して連結の結果の順序を必要に応じて指定`WITHIN GROUP`句。
```
WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )
```   
<order_by_expression_list>   
 
  非定数の一覧[式](../../t-sql/language-elements/expressions-transact-sql.md)結果の並べ替えを使用できます。 1 つだけ`order_by_expression`1 つのクエリは許可されています。 既定の並べ替え順は昇順です。   
  

## <a name="return-types"></a>戻り値の型 

戻り値の型は、最初の引数 (式) に依存します。 入力引数が文字列型の場合 (`NVARCHAR`、 `VARCHAR`)、結果型は入力の型と同じになります。 次の表に、自動変換を示します。  

|入力式の型 |結果 | 
|-------|-------|
|NVARCHAR(MAX) |NVARCHAR(MAX) |
|VARCHAR(MAX) |VARCHAR(MAX) |
|NVARCHAR(1…4000) |NVARCHAR(4000) |
|VARCHAR(1…8000) |VARCHAR(8000) |
|int、bigint、smallint、tinyint、数値、float、real、bit、decimal、smallmoney、money、datetime、datetime2、 |NVARCHAR(4000) |


## <a name="remarks"></a>解説  
 
`STRING_AGG`集計関数を行からのすべての式を受け取って 1 つの文字列に連結します。 式の値は文字列型に暗黙的に変換され、連結されています。 文字列への暗黙の変換は、データ型変換の既存の規則に従います。 データ型変換の詳細については、次を参照してください。 [CAST および CONVERT (TRANSACT-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)です。 

入力式が型の場合`VARCHAR`、区切り記号が型にすることはできません`NVARCHAR`です。 

Null 値は無視され、対応する区切り記号は追加されません。 Null 値のプレース ホルダーを返すを使用して、 `ISNULL` B. の例に示すとおりに機能

`STRING_AGG`すべての互換性レベルがあります。


## <a name="examples"></a>使用例 

### <a name="a-generate-list-of-names-separated-in-new-lines"></a>A. 新しい行で区切られた名の一覧を生成します。 
次の例では、復帰で区切られた 1 つの結果セルの名前の一覧を生成します。
```sql
SELECT STRING_AGG (FirstName, CHAR(13)) AS csv 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|csv | 
|--- |
|Syed <br />Catherine <br />Kim <br />Kim <br />Kim <br />Hazem <br />[...] | 

`NULL`値`name`結果内のセルは返されません。   
> [!NOTE]  
>  Management Studio のクエリ エディターを使用する場合、**結果をグリッドに**オプションは、キャリッジ リターンを実装できません。 切り替える**結果をテキスト**結果を適切に設定します。   


### <a name="b-generate-list-of-names-separated-with-comma-without-null-values"></a>B. NULL 値を含まないコンマで区切られた名の一覧を生成します。   
次の例では、'なし' に null 値を置換し、1 つの結果セルにコンマ区切りで名前を返します。  
```sql
SELECT STRING_AGG ( ISNULL(FirstName,'N/A'), ',') AS csv 
FROM Person.Person; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
 

|Csv | 
|--- |
|John、N/A、Mike、Peter、N/A、N/A、Alice、Bob します。 |  


### <a name="c-generate-comma-separated-values"></a>C. コンマ区切り値を生成します。 

```sql   
SELECT 
STRING_AGG(CONCAT(FirstName, ' ', LastName, ' (', ModifiedDate, ')'), CHAR(13)) 
  AS names 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|名 | 
|--- |
|Ken Sánchez (Feb 8 2003 12時 00分 AM) <br />Terri Duffy (2 月 24日 2002 12時 00分 AM) <br />Roberto Tamburello (Dec  5 2001 12:00AM) <br />Rob Walters (2001 年 12 月 29日 12時 00分 AM) <br />[...] |

> [!NOTE]  
>  Management Studio のクエリ エディターを使用する場合、**結果をグリッドに**オプションは、キャリッジ リターンを実装できません。 切り替える**結果をテキスト**結果を適切に設定します。   
 

### <a name="d-return-news-articles-with-related-tags"></a>D. 関連するタグのニュース記事を返す 

記事と、タグは、異なるテーブルに区切られます。 開発者は、各アーティクルに関連付けられているすべてのタグごとに 1 行を返すたいとします。 次のクエリを使用します。 
```sql
SELECT a.articleId, title, STRING_AGG (tag, ',') as tags 
FROM dbo.Article AS a       
LEFT JOIN dbo.ArticleTag AS t 
    ON a.ArticleId = t.ArticleId 
GROUP BY a.articleId, title;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|articleId |title |タグ |
|--- |--- |--- |
|172 |ポーリングを閉じる選択結果を示します |政治、投票、市区町村 council | 
|176 |新しい高速道路を輻輳を減らすために必要 |NULL |
|177 |犬は引き続き cats よりも一般的になります |投票動物| 

### <a name="e-generate-list-of-emails-per-towns"></a>E. 都市ごとの電子メールの一覧を生成します。

次のクエリでは、従業員の電子メール アドレスを検索し、都市別にグループ化。 
```sql
SELECT town, STRING_AGG (email, ';') AS emails 
FROM dbo.Employee 
GROUP BY town; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|町 |電子メール |
|--- |--- |
|Seattle |syed0@adventure-works.com;catherine0@adventure-works.com;kim2@adventure-works.com |
|LA |sam1@adventure-works.com;hazem0@adventure-works.com |

電子メールを送信するいくつか特定の都市にかかわっているユーザーのグループに列を直接使用することができます、メールで電子メールが返されます。 

### <a name="f-generate-a-sorted-list-of-emails-per-towns"></a>F. 都市ごとの電子メールの並べ替えられたリストを生成します。   
   
前の例と同様に、次のクエリの従業員の電子メール アドレスを検索、町、別にグループ化し、電子メールをアルファベット順に並べ替えます。   
```sql
SELECT town, 
    STRING_AGG (email, ';') WITHIN GROUP (ORDER BY email ASC) AS emails 
FROM dbo.Employee 
GROUP BY town; 
```
   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|町 |電子メール |
|--- |--- |
|Seattle |catherine0@adventure-works.com;kim2@adventure-works.com;syed0@adventure-works.com |
|LA |hazem0@adventure-works.com;sam1@adventure-works.com |


## <a name="see-also"></a>参照  
 [CONCAT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/quotename-transact-sql.md)  
 [置換 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/replace-transact-sql.md)  
 [リバース &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/stuff-transact-sql.md)  
 [変換 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/translate-transact-sql.md)  
 [集計関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/aggregate-functions-transact-sql.md)  
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  

