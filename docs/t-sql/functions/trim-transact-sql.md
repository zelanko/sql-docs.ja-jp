---
title: "TRIM (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/20/2017
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
- TRIM
- TRIM_TSQL
dev_langs: TSQL
helpviewer_keywords: TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: "4"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 88ba00513a8f76ae560ed717801150aa9b80046e
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="trim-transact-sql"></a>TRIM (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

空白文字を削除`char(32)`または開始または文字列の末尾から指定したその他の文字列。  
 
## <a name="syntax"></a>構文   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[両方 |先頭の |末尾] いないまだ使用可能です。"

## <a name="arguments"></a>引数   

文字   
リテラル、変数、または任意の LOB ではない文字型の関数呼び出し (`nvarchar`、 `varchar`、 `nchar`、または`char`) を削除する文字を含むです。 `nvarchar(max)`および`varchar(max)`型は許可されません。

string   
任意の文字型の式です (`nvarchar`、 `varchar`、 `nchar`、または`char`) 文字を削除する必要があります。

## <a name="return-types"></a>戻り値の型   
文字列引数の型と文字列式を返します場所、空白文字`char(32)`またはその他の指定した文字は、両方の側から削除されます。 返します`NULL`入力文字列が場合`NULL`です。

## <a name="remarks"></a>解説   
既定では`TRIM`関数は、空白文字を削除`char(32)`両側からです。 これに相当`LTRIM(RTRIM(@string))`です。 動作`TRIM `指定された文字を持つ関数は、の動作と同じ`REPLACE`関数の先頭または末尾からの文字が空の文字列に置き換えられます。


## <a name="examples"></a>使用例
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  文字列の両方の側から、空白文字を削除します。   
次の例は前に、から、単語の後にスペースを削除`test`です。   
```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  指定した文字列の両方の側からの文字を削除   
次の例では、末尾にピリオドと末尾のスペースを削除します。
```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>参照
 [左と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ltrim-transact-sql.md)  
 [右 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)  
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
