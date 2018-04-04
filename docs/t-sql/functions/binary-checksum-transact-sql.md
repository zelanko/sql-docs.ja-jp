---
title: BINARY_CHECKSUM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9ff8368877b3fb2153685554f1484b5fbbcc7c3a
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
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
&#42;テーブルのすべての列、計算があることを指定します。 BINARY_CHECKSUM の計算では、比較できないデータ型の列は無視されます。 比較できないデータ型を含める **テキスト**, 、**ntext**, 、**イメージ**, 、**カーソル**, 、**xml**, 、および比較できない共通言語ランタイム (CLR) ユーザー定義型です。
  
*式 (expression)*  
任意のデータ型の[式](../../t-sql/language-elements/expressions-transact-sql.md)を指定します。 BINARY_CHECKSUM の計算では、比較できないデータ型の式は無視されます。

## <a name="return-types"></a>戻り値の型  
 **int**
  
## <a name="remarks"></a>Remarks  
BINARY_CHECKSUM(*) をテーブルの行に対して実行した場合、行が変更されていなければ同じ値が返されます。 BINARY_CHECKSUM はハッシュ関数のプロパティとなります。BINARY_CHECKSUM を任意の 2 つの式に適用した場合、その 2 つに対応する要素のデータ型が同じで、等号 (=) 演算子により比較した場合に等しければ、同じ値が返されます。 この定義では、指定した型が NULL 値である場合、これらの値は等しいものとして比較されます。 いずれかの式の値を変更した場合は通常、そのリストのチェックサムも変わりますが、 チェックサムが変わらない場合もわずかですがあります。 したがって、アプリケーションで値の変更をすべて検出する必要がある場合は、値の変更の検出に BINARY_CHECKSUM を使用しないことをお勧めします。 使用を検討して HashBytes 代わりにします。 MD5 ハッシュ アルゴリズムを指定した場合は、HashBytes から 2 つの異なる入力に対して同じ結果が返される可能性が BINARY_CHECKSUM よりもはるかに低くなります。
  
BINARY_CHECKSUM は式のリストに適用でき、指定したリストに対しては同じ値が返されます。 BINARY_CHECKSUM を 2 つの式のリストに適用した場合、2 つのリストの対応する要素が同じ型と同じバイト表現であれば、同じ値が返されます。 この定義では、指定した型の値が NULL であった場合、これらの値は同じバイト表現として扱われます。
  
BINARY_CHECKSUM と CHECKSUM は類似した関数で、どちらも式のリストに対するチェックサム値の計算に使用でき、式の順序が結果の値に影響します。 BINARY_CHECKSUM(*) で使用される列の順序は、テーブルまたはビュー定義で指定された列の順序です。 これには計算列も含まれます。
  
ロケールによっては、異なる表現の文字列が同じものと判断される場合があります。このような場合、CHECKSUM と BINARY_CHECKSUM では文字列型に対して異なる値が返されます。 文字列のデータ型は **char**, 、**varchar**, 、**nchar**, 、**nvarchar**, 、または **sql_variant** (基本データ型の場合 **sql_variant** は文字列データ型)。 たとえば、文字列 "McCavity" と "Mccavity" の BINARY_CHECKSUM 値は異なります。 これに対し、大文字小文字が区別されないサーバーの場合、CHECKSUM では 2 つの文字列に同じチェックサム値が返されます。 CHECKSUM 値を BINARY_CHECKSUM 値と比較しないでください。
 
BINARY_CHECKSUM は、最大 8,000 の **varbinary(max)** 型の文字と、最大 255 の **nvarchar(max)** 型の文字をサポートします。
  
## <a name="examples"></a>使用例  
次の例では、`BINARY_CHECKSUM` を使用して、テーブルの行に変更がないかどうかを確認します。
  
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
[集計関数 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[チェックサム (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/checksum-transact-sql.md)  
[CHECKSUM_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-agg-transact-sql.md)
  
  
