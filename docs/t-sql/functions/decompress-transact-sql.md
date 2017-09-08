---
title: "(TRANSACT-SQL) を圧縮解除 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/30/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7918a9bce5afcd7ce59551a60fc7e3f2f318f492
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="decompress-transact-sql"></a>圧縮解除 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  GZIP アルゴリズムを使用して、入力式を圧縮解除できません。 圧縮の結果は、バイト配列 (varbinary (max) 型) です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 **Varbinary (***n***)**、 **varbinary (max)**、または**バイナリ (** *n***)**. 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。  
  
## <a name="return-types"></a>戻り値の型  
 データ型を返す**varbinary (max)**型です。 入力引数は、ZIP アルゴリズムを使用して圧縮が解除されます。 ユーザーは、必要な場合は、対象の種類に結果を明示的にキャストする必要があります。  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
  
### <a name="a-decompress-data-at-query-time"></a>A. クエリ時にデータを圧縮解除します。  
 次の例では、圧縮するテーブルからデータを表示する方法を示します。  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>B. 計算列を使用して圧縮されたデータを表示します。  
 次の例では、圧縮解除されたデータを格納するテーブルを作成する方法を示します。  
  
```  
CREATE TABLE (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/compress-transact-sql.md)  
  
  

