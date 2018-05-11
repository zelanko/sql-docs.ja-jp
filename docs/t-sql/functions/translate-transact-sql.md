---
title: TRANSLATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 4e070109028ed446636610b1008b76fc33bf495e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

2 番目の引数で指定された一部の文字が対象の文字セットに変換された後に、最初の引数として指定された文字列を返します。

## <a name="syntax"></a>構文   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>引数   

inputString   
任意の文字型 (つまり nvarchar、varchar、nchar、または char) の[式](../../t-sql/language-elements/expressions-transact-sql.md)です。

characters   
置換対象の文字を含む任意の文字型の[式](../../t-sql/language-elements/expressions-transact-sql.md)です。

翻訳   
型と長さが 2 番目の引数と一致する文字[式](../../t-sql/language-elements/expressions-transact-sql.md)です。

## <a name="return-types"></a>戻り値の型   
2 番目の引数の文字が 3 番目の引数の一致する文字に置き換えられる、`inputString` と同じ型の文字式を返します。

## <a name="remarks"></a>Remarks   

文字と翻訳の長さが異なる場合、`TRANSLATE` 関数はエラーを返します。 文字または置換の引数として null 値が指定された場合、`TRANSLATE` 関数は変更されていない入力を返します。 `TRANSLATE` 関数の動作は、[REPLACE](../../t-sql/functions/replace-transact-sql.md) 関数と同じと考えられます。   

`TRANSLATE` 関数の動作は、複数の `REPLACE` 関数を使用した場合と同じです。

`TRANSLATE` は常に SC 照合順序を認識しています。

## <a name="examples"></a>使用例   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. 角かっこと中かっこを通常のかっこで置き換える    
次のクエリは、入力文字列の角かっこと中かっこを通常のかっこで置き換えます。
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  この例の `TRANSLATE` 関数は、`REPLACE` を使用する次のステートメントと同等ですが、はるかに簡単です。`SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>B. GeoJSON ポイントを WKT に変換する    
GeoJSON は、さまざまな地理的データ構造をエンコードするための形式です。 `TRANSLATE` 関数を使用すると、開発者は GeoJSON ポイントから WKT 形式への変換とその逆の変換に簡単に実行できます。 次のクエリは、入力の角かっこと中かっこを通常のかっこで置き換えます。   
```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|ポイント  |座標 |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


## <a name="see-also"></a>参照
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [文字列関数 (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

