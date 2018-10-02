---
title: SOUNDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SOUNDEX
- SOUNDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SOUNDEX function
- comparing string data
- strings [SQL Server], similarity
- strings [SQL Server], comparing
- SOUNDEX values
ms.assetid: 8f1ed34e-8467-4512-a211-e0f43dee6584
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: efd2ea94d7f1eeef885df323ca522503c9e15cd1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762741"
---
# <a name="soundex-transact-sql"></a>SOUNDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの文字列の類似性を評価する 4 文字 (SOUNDEX) コードを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SOUNDEX ( character_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 文字データの英数字[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 *character_expression* には定数、変数、または列を指定できます。  
  
## <a name="return-types"></a>戻り値の型  
 **varchar**  
  
## <a name="remarks"></a>Remarks  
 SOUNDEX は、英数字の文字列を、文字列の音声表現に基づいた 4 文字のコードに変換します。 コードの最初の文字の最初の文字は *character_expression*, 、大文字に変換されます。 コードの 2 番目から 4 番目までの文字は、式の中の文字を表す数字です。 A、E、I、O、U、H、W、Y の各文字は、文字列の先頭の文字である場合を除き無視されます。 4 文字のコードを生成するために必要な場合は、最後にゼロが追加されます。 SOUNDEX コードの詳細については、次を参照してください。 [The Soundex Indexing System](https://www.archives.gov/research/census/soundex.html)です。  
  
 さまざまな文字列の SOUNDEX コードを比較して、文字列の音声表現の類似性を確認できます。 DIFFERENCE 関数は、2 つの文字列に対して SOUNDEX を実行し、それらの文字列の SOUNDEX コードの類似性を表す整数を返します。  
  
 SOUNDEX は照合順序に依存します。 文字列関数は入れ子にすることができます。  
  
## <a name="soundex-compatibility"></a>SOUNDEX の互換性  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、SOUNDEX 関数で SOUNDEX のルールのサブセットが適用されていました。 データベースの互換性レベルが 110 以上の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではより完全なルール セットが適用されます。  
  
 互換性レベル 110 以上へのアップグレード後に、SOUNDEX 関数を使用するインデックス、ヒープ、または CHECK 制約の再構築が必要になる場合があります。  
  
-   SOUNDEX で定義された保存される計算列を含むヒープは、`ALTER TABLE <table> REBUILD` ステートメントを実行してヒープが再構築されるまでクエリできません。  
  
-   SOUNDEX で定義された CHECK 制約は、アップグレード時に無効になります。 無効になった制約を有効にするには、`ALTER TABLE <table> WITH CHECK CHECK CONSTRAINT ALL` ステートメントを実行します。  
  
-   SOUNDEX で定義された保存される計算列を含むインデックス (インデックス付きビューを含む) は、`ALTER INDEX ALL ON <object> REBUILD` ステートメントを実行してインデックスが再構築されるまでクエリできません。  
  
## <a name="examples"></a>使用例  
 次の例では、SOUNDEX 関数、およびこれに関連した DIFFERENCE 関数を示しています。 最初の例では、標準 `SOUNDEX` 値がすべての子音に対して返されます。 母音、文字 `SOUNDEX`、2 文字の連続、および文字 `Smith` は含まれないため、`Smythe` と `y` に対する `h` では同じ結果が返されます。  
  
```  
-- Using SOUNDEX  
SELECT SOUNDEX ('Smith'), SOUNDEX ('Smythe');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)] Latin1_General の照合順序に有効です。  
  
```  
  
----- -----   
S530  S530    
  
(1 row(s) affected)  
```  
  
 `DIFFERENCE` 関数は、`SOUNDEX` パターンの結果を比較します。 次の例では、母音が違うだけの 2 つの文字列の場合を示しています。 返される値は、類似性が最も高い `4` です。  
  
```  
-- Using DIFFERENCE  
SELECT DIFFERENCE('Smithers', 'Smythers');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)] Latin1_General の照合順序に有効です。  
  
```  
-----------   
4             
  
(1 row(s) affected)  
```  
  
 次の例では子音が異なるため、類似性が低い `2` が返されます。  
  
```  
SELECT DIFFERENCE('Anothers', 'Brothers');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)] Latin1_General の照合順序に有効です。  
  
```  
-----------   
2             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [DIFFERENCE &#40;Transact-SQL&#41;](../../t-sql/functions/difference-transact-sql.md)   
 [文字列関数 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [ALTER DATABASE 互換性レベル &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

