---
title: "binary と varbinary (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 8/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e6aaf00b8e846316c92897360932703a013150e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="binary-and-varbinary-transact-sql"></a>binary と varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

固定長または可変長のバイナリ データ型です。
  
## <a name="arguments"></a>引数  
**バイナリ**[(  *n*  )] 固定長のバイナリ データの長さを *n*  (バイト単位) を *n* 値です1 ~ 8,000 です。 ストレージのサイズは *n* バイトです。
  
**varbinary** [(  *n*   |  **max**)] 可変長バイナリ データ。 *n*1 ~ 8,000 の値を指定できます。 **max**ストレージの最大サイズが 2 であることを示します。 ^ 31-1 バイトです。 格納サイズは、入力したデータの実際の長さ + 2 バイトとなります。 入力するデータの長さは 0 バイトでもかまいません。 ANSI SQL シノニム**varbinary**は**バイナリのさまざまな**します。
  
## <a name="remarks"></a>解説  
ときに *n* が指定されていないデータ定義または変数宣言ステートメントで、既定の長さは 1 です。 ときに *n* が指定されていない、CAST 関数で、既定の長さは 30 です。

| データ型 | ときに使用してください. |
| --- | --- |
| **[バイナリ]** | 列データ エントリのサイズは一貫性のあります。|
| **varbinary** | 列データ エントリのサイズが大きく変化します。|
| **varbinary(max)** | 列データ エントリは、8,000 バイトを超えています。|


## <a name="converting-binary-and-varbinary-data"></a>Binary と varbinary のデータを変換します。
文字列データ型からデータを変換するとき (**char**、 **varchar**、 **nchar**、 **nvarchar**、**バイナリ**、 **varbinary**、**テキスト**、 **ntext**、または**イメージ**) に、**バイナリ**または**varbinary** 、等しくない長さのデータ型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]埋め込み文字を埋め込むか、右側のデータが切り捨てられます。 他のデータ型を変換するときに**バイナリ**または**varbinary**データが埋め込まれるか、左側に切り捨てられます。 桁の埋め込みには 16 進数の 0 が使用されます。
  
データを変換する、**バイナリ**と**varbinary**データ型は便利な場合は**バイナリ**データがデータを移動する最も簡単な方法です。 いずれかの任意の値を変換するための十分なサイズの大きなバイナリ値を入力しの型に常に結果を同じ値の両方の変換で実行されている、同じバージョンの場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 バージョンからのバージョンに値のバイナリ表現を変更する可能性があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。
  
変換することができます**int**、 **smallint**、および**tinyint**に**バイナリ**または**varbinary**、場合にします。変換、**バイナリ**切り捨てが発生した場合に、整数値、この値に戻す値が元の整数値異なっています。 たとえば、次の SELECT ステートメントは整数値 `123456` を通常はバイナリ値 `0x0001e240` として格納することを示しています。
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
ただし、次`SELECT`ステートメントが場合を示しています、**バイナリ**ターゲットが小さすぎる値全体を保持するために、左側の桁は切り捨てられますとして同じ番号が格納されているように`0xe240`:
  
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
>  すべてのデータ間の変換を入力し、**バイナリ**データ型は、のバージョン間で同じである保証はありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型の変換 (&) #40";"データベース エンジン"&"#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

