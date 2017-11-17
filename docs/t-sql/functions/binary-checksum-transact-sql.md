---
title: "BINARY_CHECKSUM (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BINARY_CHECKSUM
- BINARY_CHECKSUM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- BINARY_CHECKSUM function
- binary [SQL Server], checksum values
ms.assetid: 07fece4d-58e3-446e-a3b5-92fe24d2d1fb
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b84847f3efe7224c6fa0ad945b03f3afbc1381b9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="binarychecksum--transact-sql"></a>BINARY_CHECKSUM (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

テーブルの 1 つの行、または一連の式に対して計算された、バイナリのチェックサム値を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
BINARY_CHECKSUM ( * | expression [ ,...n ] )   
```  
  
## <a name="arguments"></a>引数  
*\**  
計算テーブルのすべての列を指定します。 BINARY_CHECKSUM の計算では、比較できないデータ型の列は無視されます。 比較できないデータ型を含める**テキスト**、 **ntext**、**イメージ**、**カーソル**、 **xml**、および比較できない共通言語ランタイム (CLR) ユーザー定義型です。
  
*式 (expression)*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)任意の型。 BINARY_CHECKSUM の計算では、比較できないデータ型の式は無視されます。
  
## <a name="remarks"></a>解説  
BINARY_CHECKSUM(*) をテーブルの行に対して実行した場合、行が変更されていなければ同じ値が返されます。 BINARY_CHECKSUM はハッシュ関数のプロパティを満たす: 2 つのリストの対応する要素が同じ型であるし、等号 (=) 演算子を使って比較した場合に等しければ、2 つの式のリストに適用される BINARY_CHECKSUM が同じ値を返します。 この定義では、指定した型が NULL 値である場合、これらの値は等しいものとして比較されます。 いずれかの式の値を変更した場合は通常、そのリストのチェックサムも変わりますが、 チェックサムが変わらない場合もわずかですがあります。 このため、お勧めしません BINARY_CHECKSUM を使用して、アプリケーションには、場合によっては、変更がありませんが許容できる場合を除き、値が変更されたかどうかを検出します。 HashBytes を代わりに使用を検討してください。 MD5 ハッシュ アルゴリズムを指定すると、2 つの異なる入力に対して同じ結果を返す HashBytes の確率は BINARY_CHECKSUM よりも大幅に低くです。
  
BINARY_CHECKSUM は式のリストに適用でき、指定したリストに対しては同じ値が返されます。 BINARY_CHECKSUM を 2 つの式のリストに適用した場合、2 つのリストの対応する要素が同じ型と同じバイト表現であれば、同じ値が返されます。 この定義では、指定した型の値が NULL であった場合、これらの値は同じバイト表現として扱われます。
  
BINARY_CHECKSUM と CHECKSUM は類似した関数で、どちらも式のリストに対するチェックサム値の計算に使用でき、式の順序が結果の値に影響します。 BINARY_CHECKSUM(*) で使用される列の順序は、テーブルまたはビュー定義で指定された列の順序です。 これには計算列も含まれます。
  
ロケールによっては、異なる表現の文字列が同じものと判断される場合があります。このような場合、CHECKSUM と BINARY_CHECKSUM では文字列型に対して異なる値が返されます。 文字列データ型は**char**、 **varchar**、 **nchar**、 **nvarchar**、または**sql_variant** (場合、基本型**sql_variant**文字列データ型です)。 たとえば、文字列 "McCavity" と "Mccavity" の BINARY_CHECKSUM 値は異なります。 これに対し、大文字小文字が区別されないサーバーの場合、CHECKSUM では 2 つの文字列に同じチェックサム値が返されます。 CHECKSUM 値を BINARY_CHECKSUM 値と比較しないでください。
 
BINARY_CHECKSUM は、型の最大で 8,000 文字をサポートしている**varbinary (max)**および最大で 255 文字の種類の**nvarchar (max)**です。
  
## <a name="examples"></a>使用例  
次の例では`BINARY_CHECKSUM`テーブルの行で変更を検出します。
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE myTable (column1 int, column2 varchar(256));  
GO  
INSERT INTO myTable VALUES (1, 'test');  
GO  
SELECT BINARY_CHECKSUM(*) from myTable;  
GO  
UPDATE myTable set column2 = 'TEST';  
GO  
SELECT BINARY_CHECKSUM(*) from myTable;  
GO  
```  
  
## <a name="see-also"></a>参照
[集計関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[チェックサム & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/checksum-transact-sql.md)  
[CHECKSUM_AGG & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/checksum-agg-transact-sql.md)
  
  

