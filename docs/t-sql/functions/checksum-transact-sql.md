---
title: "チェックサム (TRANSACT-SQL) |Microsoft ドキュメント"
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
- CHECKSUM_TSQL
- CHECKSUM
dev_langs:
- TSQL
helpviewer_keywords:
- hash indexes
- CHECKSUM function
- checksum values
ms.assetid: e26d3339-845c-49c2-9d89-243376874c13
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: d41736f6ac216de0ecf755cbf7ca73ba34a697b8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="checksum-transact-sql"></a>CHECKSUM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

テーブルの行または式のリストで計算されたチェックサム値を返します。 CHECKSUM は、ハッシュ インデックスの作成に使用します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CHECKSUM ( * | expression [ ,...n ] )  
```  
  
## <a name="arguments"></a>引数  
\*  
テーブルのすべての列を計算の対象とします。 列のいずれかが比較できないデータ型である場合、CHECKSUM ではエラーが返されます。 比較できないデータ型は**テキスト**、 **ntext**、**イメージ**、XML、および**カーソル**も**sql_variant**が基本型として、これらの型のいずれか。
  
*式 (expression)*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)比較できないデータ型を除く任意の型。
  
## <a name="return-types"></a>戻り値の型
 **int**  
  
## <a name="remarks"></a>解説  
CHECKSUM では、一連の引数に対してハッシュ値 (チェックサム) が計算されます。 このハッシュ値はハッシュ インデックスの作成に使用されます。 CHECKSUM の引数に列を指定し、計算された CHECKSUM 値を基にインデックスを作成すると、結果はハッシュ インデックスになります。 このハッシュ インデックスは、列で等値検索を行うときに使用できます。
  
CHECKSUM はハッシュ関数のプロパティとなります。CHECKSUM を任意の 2 つの式に適用した場合、その 2 つに対応する要素のデータ型が同じで、等号 (=) 演算子により比較した場合に等しければ、同じ値が返されます。 この定義では、指定した型が NULL 値である場合、これらの値は等しいものとして比較されます。 いずれかの式の値を変更した場合は通常、そのリストのチェックサムも変わりますが、 チェックサムが変わらない場合もわずかですがあります。 したがって、アプリケーションで値の変更をすべて検出する必要がある場合は、値の変更の検出に CHECKSUM を使用しないことをお勧めします。 使用を検討して[HashBytes](../../t-sql/functions/hashbytes-transact-sql.md)代わりにします。 MD5 ハッシュ アルゴリズムを指定した場合は、HashBytes から 2 つの異なる入力に対して同じ結果が返される可能性が CHECKSUM よりもはるかに低くなります。
  
式の順序は、CHECKSUM の結果の値に影響します。 CHECKSUM(*) で使用される列の順序は、テーブルまたはビュー定義で指定される列の順序です。 これには、計算列が含まれます。
  
CHECKSUM 値は照合順序によって異なります。 異なる照合順序で保存された同じ値は別の CHECKSUM 値を返します。
  
## <a name="examples"></a>使用例  
次の例では、`CHECKSUM` を使ってハッシュ インデックスを作成します。 ハッシュ インデックスを作成するときは、計算されたチェックサム列をインデックスの作成先のテーブルに追加し、そのチェックサム列に対してインデックスを作成します。
  
```sql
-- Create a checksum index.  
SET ARITHABORT ON;  
USE AdventureWorks2012;   
GO  
ALTER TABLE Production.Product  
ADD cs_Pname AS CHECKSUM(Name);  
GO  
CREATE INDEX Pname_index ON Production.Product (cs_Pname);  
GO  
```  
  
このチェックサム インデックスを、ハッシュ インデックスとして使用できます。特にインデックスを作成する列の文字列が長い場合は、インデックス作成速度を向上できます。 チェックサム インデックスは、等値検索に使用できます。
  
```sql
/*Use the index in a SELECT query. Add a second search   
condition to catch stray cases where checksums match,   
but the values are not the same.*/  
SELECT *   
FROM Production.Product  
WHERE CHECKSUM(N'Bearing Ball') = cs_Pname  
AND Name = N'Bearing Ball';  
GO  
```  
  
計算列にインデックスを作成するとチェックサム列が具体化され、`ProductName` 値を変更すると、それがどのような変更であってもチェックサム列に反映されます。 インデックスを作成する列に直接インデックスを作成することもできます。 ただし、キー値が長いと標準インデックスおよびチェックサム インデックスは機能しない可能性があります。
  
## <a name="see-also"></a>参照
[CHECKSUM_AGG &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/checksum-agg-transact-sql.md)  
[HASHBYTES &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/hashbytes-transact-sql.md)  
[BINARY_CHECKSUM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/binary-checksum-transact-sql.md)
  
  
