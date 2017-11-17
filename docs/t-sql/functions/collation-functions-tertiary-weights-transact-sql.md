---
title: "TERTIARY_WEIGHTS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TERTIARY_WEIGHTS_TSQL
- TERTIARY_WEIGHTS
dev_langs:
- TSQL
helpviewer_keywords:
- weights [SQL Server]
- SQL tertiary collations
- TERTIARY_WEIGHTS function
ms.assetid: 7e1f5350-260b-4c61-8c84-69bb1a214f1f
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7414f60414c14457dddc6f860201fd84409f1cb1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="collation-functions---tertiaryweights-transact-sql"></a>照合順序の機能 - TERTIARY_WEIGHTS (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

SQL の第 3 の照合順序で定義された Unicode 以外の文字列式での各文字の重みを示すバイナリ文字列を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
TERTIARY_WEIGHTS( non_Unicode_character_string_expression )  
```  
  
## <a name="arguments"></a>引数  
*non_Unicode_character_string_expression*  
文字列は、[式](../../t-sql/language-elements/expressions-transact-sql.md)型の**char**、 **varchar**、または**varchar (max)**第 3 の SQL 照合順序で定義されています。 これらの照合順序の一覧については、「解説」を参照してください。
  
## <a name="return-types"></a>戻り値の型
TERTIARY_WEIGHTS を返します**varbinary**とき*non_Unicode_character_string_expression*は**char**または**varchar**、しを返します**varbinary (max)**とき*non_Unicode_character_string_expression*は**varchar (max)**です。
  
## <a name="remarks"></a>解説  
TERTIARY_WEIGHTS ときに、NULL を返します*non_Unicode_character_string_expression* SQL 第 3 の照合順序が定義されていません。 次の表に、SQL の第 3 の照合順序を示します。
  
|並べ替え順 ID|SQL 照合順序|  
|---|---|
|33|SQL_Latin1_General_Pref_CP437_CI_AS|  
|34|SQL_Latin1_General_CP437_CI_AI|  
|43|SQL_Latin1_General_Pref_CP850_CI_AS|  
|44|SQL_Latin1_General_CP850_CI_AI|  
|49|SQL_1xCompat_CP850_CI_AS|  
|53|SQL_Latin1_General_Pref_CP1_CI_AS|  
|54|SQL_Latin1_General_CP1_CI_AI|  
|56|SQL_AltDiction_Pref_CP850_CI_AS|  
|57|SQL_AltDiction_CP850_CI_AI|  
|58|SQL_Scandinavian_Pref_CP850_CI_AS|  
|82|SQL_Latin1_General_CP1250_CI_AS|  
|84|SQL_Czech_CP1250_CI_AS|  
|86|SQL_Hungarian_CP1250_CI_AS|  
|88|SQL_Polish_CP1250_CI_AS|  
|90|SQL_Romanian_CP1250_CI_AS|  
|92|SQL_Croatian_CP1250_CI_AS|  
|94|SQL_Slovak_CP1250_CI_AS|  
|96|SQL_Slovenian_CP1250_CI_AS|  
|106|SQL_Latin1_General_CP1251_CI_AS|  
|108|SQL_Ukrainian_CP1251_CI_AS|  
|113|SQL_Latin1_General_CP1253_CS_AS|  
|114|SQL_Latin1_General_CP1253_CI_AS|  
|130|SQL_Latin1_General_CP1254_CI_AS|  
|146|SQL_Latin1_General_CP1256_CI_AS|  
|154|SQL_Latin1_General_CP1257_CI_AS|  
|156|SQL_Estonian_CP1257_CI_AS|  
|158|SQL_Latvian_CP1257_CI_AS|  
|160|SQL_Lithuanian_CP1257_CI_AS|  
|183|SQL_Danish_Pref_CP1_CI_AS|  
|184|SQL_SwedishPhone_Pref_CP1_CI_AS|  
|185|SQL_SwedishStd_Pref_CP1_CI_AS|  
|186|SQL_Icelandic_Pref_CP1_CI_AS|  
  
TERTIARY_WEIGHTS は、の値に定義されている計算列の定義で使用するもの、 **char**、 **varchar**、または**varchar (max)**列です。 計算の両方の列にインデックスを定義して、 **char**、 **varchar**、または**varchar (max)**列は、パフォーマンスを向上させることができる場合、 **char**、 **varchar**、または**varchar (max)**クエリの ORDER BY 句で列を指定します。
  
## <a name="examples"></a>使用例  
次の例では、`TERTIARY_WEIGHTS` 関数を `char` 列の値に適用するテーブルに計算列を作成します。
  
```sql
CREATE TABLE TertColTable  
(Col1 char(15) COLLATE SQL_Latin1_General_Pref_CP437_CI_AS,  
Col2 AS TERTIARY_WEIGHTS(Col1));  
GO   
```  
  
## <a name="see-also"></a>参照
[ORDER BY 句 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-order-by-clause-transact-sql.md)
  
  

