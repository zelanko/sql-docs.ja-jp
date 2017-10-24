---
title: "STUFF (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STUFF
- STUFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting characters
- STUFF function
- length characters
- removing characters
- replacing characters
- characters [SQL Server], replacing
- inserting data
ms.assetid: abb0afa9-44f6-42a2-a871-5f471dfb222b
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: df9a3d019f22ec8a0ba610f2dd694e45a8bd9da3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="stuff-transact-sql"></a>STUFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  STUFF 関数は、文字列を別の文字列に挿入します。 まず、1 番目の文字列の指定された開始位置から指定された長さの文字を削除し、次に、2 番目の文字列を 1 番目の文字列の指定された開始位置に挿入します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STUFF ( character_expression , start , length , replaceWith_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字データです。 *character_expression*定数、変数、または文字またはバイナリ データのいずれかの列を指定できます。  
  
 *開始*  
 削除と挿入を開始する位置を整数で指定します。 場合*開始*または*長さ*は負の場合、null 文字列が返されます。 場合*開始*最初よりも長い*character_expression*、null 文字列が返されます。 *開始*型でも**bigint**です。  
  
 *length*  
 削除する文字数を整数で指定します。 場合*長さ*最初よりも長い*character_expression*、文字までが削除最後に、最後の*character_expression*です。 *長さ*型でも**bigint**です。  
  
 *replaceWith_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字データです。 *character_expression*定数、変数、または文字またはバイナリ データのいずれかの列を指定できます。 この式が置き換えられます*長さ*の文字*character_expression*始点*開始*です。 提供する`NULL`として、 *replaceWith_expression*、何も挿入しないで文字を削除します。   
  
## <a name="return-types"></a>戻り値の型  
 場合、データが文字を返します*character_expression*はサポートされている文字データ型の 1 つです。 場合、バイナリ データを返します*character_expression*はサポートされているバイナリ データ型の 1 つです。  
  
## <a name="remarks"></a>解説  
 開始位置または長さが負の場合、または開始位置が 1 番目の文字列の長さを超える場合は NULL 文字列が返されます。 開始位置が 0 の場合は、NULL 値が返されます。 削除する長さが 1 番目の文字列より長い場合は、1 番目の文字列の最初の文字まで削除されます。  

結果値が、戻り値の型でサポートされている最大値より大きい場合は、エラーが発生します。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 SC の照合順序を使用する場合両方*character_expression*と*replaceWith_expression*サロゲート ペアを含めることができます。 長さのパラメーターが内の各サロゲートを数*character_expression*単一の文字として。  
  
## <a name="examples"></a>使用例  
 次の例は、最初の文字列から 3 つの文字を削除することによって作成された文字列を返します`abcdef`位置から`2`で`b`と削除時点で 2 番目の文字列を挿入します。  
  
```  
SELECT STUFF('abcdef', 2, 3, 'ijklmn');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
aijklmnef   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  

