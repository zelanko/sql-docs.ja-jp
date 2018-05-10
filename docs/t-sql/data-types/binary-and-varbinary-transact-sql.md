---
title: binary と varbinary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 8/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- binary_TSQL
- varbinary_TSQL
- binary
- varbinary
dev_langs:
- TSQL
helpviewer_keywords:
- varbinary data type
- binary [SQL Server], about binary data type
ms.assetid: bcce65f9-10db-4b3e-bfaf-dfc06c6f820f
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 624a2b764d6c397b950796fe822764b7983664ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="binary-and-varbinary-transact-sql"></a>binary と varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

固定長または可変長のバイナリ データ型です。
  
## <a name="arguments"></a>引数  
**binary** [ ( *n* ) ]。長さ *n* バイトの固定長のバイナリ データです。*n* は 1 ～ 8,000 の値になります。 ストレージのサイズは *n* バイトです。
  
**varbinary** [ ( *n* | **max**) ] 可変長のバイナリ データ。 *n* には 1 ～ 8,000 の値を指定できます。 **max** 記憶域の最大サイズが 2 であることを示します。 ^ 31-1 バイトです。 格納サイズは、入力したデータの実際の長さ + 2 バイトとなります。 入力するデータの長さは 0 バイトでもかまいません。 ANSI SQL シノニム **varbinary** は **バイナリのさまざまなです**。
  
## <a name="remarks"></a>Remarks  
データ定義または変数宣言ステートメントで *n* を指定しないと、既定の長さは 1 になります。 CAST 関数で *n* を指定しないと、既定の長さは 30 になります。

| データ型 | 次の場合に使用 |
| --- | --- |
| **[バイナリ]** | 列データ エントリのサイズが一定である。|
| **varbinary** | 列データ エントリのサイズが大幅に変化する。|
| **varbinary(max)** | 列データ エントリのサイズが 8,000 バイトを超える。|


## <a name="converting-binary-and-varbinary-data"></a>binary 型データと varbinary 型データの変換
データが文字列データ型から変換される場合 (**char,** 、**varchar**, 、**nchar**, 、**nvarchar,** 、**バイナリ**, 、**varbinary**, 、**テキス**ト, 、**ntext**, 、または **イメージ**) を **バイナリ** または **varbinary** データの型、長さが等しくない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 埋め込み文字を埋め込むか、または右にデータを切り捨てます。 他のデータ型が変換される場合 **バイナリ** または **varbinary**, 、データが埋め込まれるか、左側に切り捨てられます。 桁の埋め込みには 16 進数の 0 が使用されます。
  
データの **binary** データ型と **varbinary** データ型への変換は、データ間を移動するもっとも簡単な方法が**バイナリ** データである場合に便利です。 任意の型の任意の値を十分なサイズのバイナリ値に変換した後、元の型に戻す場合、両方の変換が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の同じバージョンで実行されれば、結果は常に同じになります。 値の 2 進表現は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョン間で異なる場合があります。
  
変換することができます **int**, 、**smallint**, 、および **tinyint** に **バイナリ** または **varbinary**, 、変換する場合は、 **バイナリ** 切り捨てが発生した場合は、整数値、この値に値を元の整数値を異なる場合がします。 たとえば、次の SELECT ステートメントは整数値 `123456` を通常はバイナリ値 `0x0001e240` として格納することを示しています。
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
ただし、次の `SELECT` ステートメントは、変換先の **binary** 型が小さすぎて値全体を保持できない場合は、左側の桁が暗黙的に切り捨てられ、同じ数値が `0xe240` として格納されることを示します。
  
```sql
SELECT CAST( 123456 AS BINARY(2) );  
```  
  
次のバッチは、暗黙的な切り捨てが算術演算に影響を与えることがあり、その場合でもエラーが生成されないことを示します。
  
```sql
DECLARE @BinaryVariable2 BINARY(2);  
  
SET @BinaryVariable2 = 123456;  
SET @BinaryVariable2 = @BinaryVariable2 + 1;  
  
SELECT CAST( @BinaryVariable2 AS INT);  
GO  
```  
  
最終的な値は `57921` ではなく `123457` になります。
  
> [!NOTE]  
>  すべてのデータ間の変換の入力と **バイナリ** データ型は、バージョンの間で同じであるとは限りません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41 です。](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
