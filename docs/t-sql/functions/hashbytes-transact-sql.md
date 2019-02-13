---
title: HASHBYTES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HASHBYTES_TSQL
- HASHBYTES
dev_langs:
- TSQL
helpviewer_keywords:
- hash input
- HASHBYTES
ms.assetid: 0ea6a4d1-313e-4f70-b939-dd2cd570f6d6
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ee8626047df76aaf9186295c092623a7cee6d263
ms.sourcegitcommit: 7c052fc969d0f2c99ad574f99076dc1200d118c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55570665"
---
# <a name="hashbytes-transact-sql"></a>HASHBYTES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で入力の MD2、MD4、MD5、SHA、SHA1、または SHA2 ハッシュを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
HASHBYTES ( '<algorithm>', { @input | 'input' } )  
  
<algorithm>::= MD2 | MD4 | MD5 | SHA | SHA1 | SHA2_256 | SHA2_512   
```  
  
## <a name="arguments"></a>引数  
 **'**\<algorithm>**'**  
 入力のハッシュに使用するハッシュ アルゴリズムを指定します。 これは必須の引数で、既定値はありません。 単一引用符で囲む必要があります。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降、SHA2_256 と SHA2_512 以外のすべてのアルゴリズムは使用されなくなりました。 推奨されない古いアルゴリズムは引き続き機能しますが、Deprecation イベントが発生します。  
  
 **@input**  
 ハッシュされるデータを含む変数を指定します。 **@input** は、**varchar**、**nvarchar**、または **varbinary** です。  
  
 **'** *input* **'**  
 ハッシュする文字またはバイナリ文字列に評価される式を指定します。  
  
 出力はアルゴリズムの標準に準拠します。MD2、MD4、および MD5 の場合は 128 ビット (16 バイト)、SHA および SHA1 の場合は 160 ビット (20 バイト)、SHA2_256 の場合は 256 ビット (32 バイト)、SHA2_512 の場合は 512 ビット (64 バイト) です。  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以前の場合、指定できる入力値は 8000 バイトまでに制限されます。  
  
## <a name="return-value"></a>戻り値  
 **varbinary** (最大 8,000 バイト)  

## <a name="remarks"></a>Remarks  
ハッシュ値を計算するための別の方法として、`CHECKSUM` または `BINARY_CHECKSUM` の使用を検討してください。

MD2、MD4、MD5、SHA、および SHA1 アルゴリズムは、互換性レベル 130 以上では使用できません。 代わりに SHA2_256 または SHA2_512 を使用してください。

## <a name="examples"></a>使用例  
### <a name="return-the-hash-of-a-variable"></a>変数のハッシュを返す  
 次の例では、変数 `@HashThis` に格納されている **nvarchar** 型のデータの `SHA1` ハッシュを返します。  
  
```sql  
DECLARE @HashThis nvarchar(4000);  
SET @HashThis = CONVERT(nvarchar(4000),'dslfdkjLK85kldhnv$n000#knf');  
SELECT HASHBYTES('SHA1', @HashThis);  
```  
  
### <a name="return-the-hash-of-a-table-column"></a>テーブル列のハッシュを返す  
 次の例では、テーブル `c1` 内の列 `Test1` の値の SHA1 ハッシュを返します。  
  
```sql  
CREATE TABLE dbo.Test1 (c1 nvarchar(50));  
INSERT dbo.Test1 VALUES ('This is a test.');  
INSERT dbo.Test1 VALUES ('This is test 2.');  
SELECT HASHBYTES('SHA1', c1) FROM dbo.Test1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------------  
0x0E7AAB0B4FF0FD2DFB4F0233E2EE7A26CD08F173  
0xF643A82F948DEFB922B12E50B950CEE130A934D6  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
[暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
[CHECKSUM_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-agg-transact-sql.md)  
[チェックサム (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/checksum-transact-sql.md)  
[BINARY_CHECKSUM  &#40;Transact-SQL&#41;](../../t-sql/functions/binary-checksum-transact-sql.md)  
  
