---
title: "変換 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 5
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 583c414206a0acc79d1abdfff34728c38711a855
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="translate-transact-sql"></a>変換 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

2 番目の引数で指定されたいくつかの文字は、移行先の一連の文字に変換した後、最初の引数として指定された文字列を返します。

## <a name="syntax"></a>構文   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>引数   

inputString   
[式](../../t-sql/language-elements/expressions-transact-sql.md)任意の文字型 (nvarchar、varchar、nchar、char)。

文字   
[式](../../t-sql/language-elements/expressions-transact-sql.md)任意の文字型文字を置き換える必要があります。

翻訳   
文字[式](../../t-sql/language-elements/expressions-transact-sql.md)型と長さが 2 番目の引数に一致します。

## <a name="return-types"></a>戻り値の型   
同じ型の文字式を返します`inputString`2 番目の引数からの文字が 3 番目の引数の一致する文字に置き換えられます。

## <a name="remarks"></a>解説   

`TRANSLATE`関数には文字と翻訳の長さが異なる場合に、エラーが返されます。 `TRANSLATE`関数は、null 値が文字または置換引数として指定される場合、変更されていない入力を返す必要があります。 動作、`TRANSLATE`関数と同じにする必要があります、[置換](../../t-sql/functions/replace-transact-sql.md)関数。   

動作、`TRANSLATE`関数は複数の使用と同じ`REPLACE`関数。

`TRANSLATE`常に SC の照合順序に注意してください。

## <a name="examples"></a>使用例   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. 四角形と中かっこを正規の中かっこに置き換える    
次のクエリでは、かっこを入力文字列内の四角形と中かっこが置き換えられます。
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  `TRANSLATE`この例では関数と同じですが、次のステートメントを使用するよりもはるかにある`REPLACE`:`SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>B. WKT GeoJSON ポイントに変換します。    
GeoJSON は、さまざまな地理的なデータ構造体のエンコード形式です。 `TRANSLATE`関数の場合、開発者は、GeoJSON ポイント WKT 形式またはその逆を簡単に変換できます。 次のクエリでは、正規の中かっこを入力内の四角形と波かっこが置き換えられます。   
```tsql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|ポイント  |座標 |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


## <a name="see-also"></a>参照

[文字列関数 (TRANSACT-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
[置換 (TRANSACT-SQL)](../../t-sql/functions/replace-transact-sql.md)   


