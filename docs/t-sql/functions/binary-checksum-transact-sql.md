---
title: BINARY_CHECKSUM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 392e21cdf50dc537e5bf6cdfcadf18771e66aad7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759690"
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
計算がすべてのテーブルの列に対して行われることを指定します。 BINARY_CHECKSUM の計算では、比較できないデータ型の列は無視されます。 比較できないデータ型は次のとおりです。  
* **カーソル (cursor)**  
* **image**  
* **ntext**  
* **text**  
* **xml**  

および比較できない共通言語ランタイム (CLR) ユーザー定義型です。
  
*式 (expression)*  
任意のデータ型の[式](../../t-sql/language-elements/expressions-transact-sql.md)。 BINARY_CHECKSUM の計算では、比較できないデータ型の式は無視されます。

## <a name="return-types"></a>戻り値の型  
 **int**
  
## <a name="remarks"></a>Remarks  
BINARY_CHECKSUM(*) をテーブルの行に対して実行した場合、行が変更されていなければ同じ値が返されます。 BINARY_CHECKSUM はハッシュ関数のプロパティとなります。BINARY_CHECKSUM を 2 つの式のリストに適用した場合、その 2 つに対応する要素のデータ型が同じで、等号 (=) 演算子により比較した場合に等しければ、同じ値が返されます。 この定義では、指定した型が NULL 値であるとすると、等しい値として比較されます。 式リストのいずれかの値を変更した場合は、その式のチェックサムも変わります。 ただし、これは保証されません。 そのため、値が変更されたかどうかを検出するには、アプリケーションが変更を検出できないことを許容できる場合のみ、BINARY_CHECKSUM の使用をお勧めします。 それ以外の場合は、代わりに HashBytes を検討してください。 MD5 ハッシュ アルゴリズムを指定した場合は、HashBytes から 2 つの異なる入力に対して同じ結果が返される可能性が BINARY_CHECKSUM よりもはるかに低くなります。
  
BINARY_CHECKSUM は式のリスト全体を処理でき、指定したリストに対しては同じ値が返されます。 BINARY_CHECKSUM を 2 つの式のリストに適用した場合、2 つのリストの対応する要素が同じ型と同じバイト表現であれば、同じ値が返されます。 この定義では、指定した型の値が NULL であった場合、これらの値は同じバイト表現として扱われます。
  
BINARY_CHECKSUM と CHECKSUM は類似した関数で、どちらも式のリストに対するチェックサム値の計算に使用でき、式の順序が結果の値に影響します。 BINARY_CHECKSUM(*) で使用される列の順序は、テーブルまたはビュー定義で指定された列の順序です。 これには、計算列が含まれます。
  
ロケールによっては、異なる表現の文字列が等しいとして比較される場合があります。このような場合、BINARY_CHECKSUM と CHECKSUM では文字列データ型に対して異なる値が返されます。 文字列データ型は次のとおりです。  

* **char**  
* **nchar**  
* **nvarchar**  
* **varchar**  

内の複数の  

* **sql_variant** (**sql_variant** の基本データ型が文字列データ型の場合)。  
  
たとえば、文字列 "McCavity" と "Mccavity" の BINARY_CHECKSUM 値は異なります。 これに対し、大文字小文字が区別されないサーバーの場合、CHECKSUM ではこれらの文字列に同じチェックサム値が返されます。 CHECKSUM 値と BINARY_CHECKSUM 値の比較を避ける必要があります。
 
BINARY_CHECKSUM は、最大 8,000 の **varbinary(max)** 型の文字と、最大 255 の **nvarchar(max)** 型の文字をサポートします。
  
## <a name="examples"></a>使用例  
この例では、`BINARY_CHECKSUM` を使用して、テーブル行の変更を検出します。
  
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
  
  
