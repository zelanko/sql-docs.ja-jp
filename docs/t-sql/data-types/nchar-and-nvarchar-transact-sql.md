---
title: "nchar および nvarchar (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc7de3b64519f3d0fd1f2e9557ccf7196e3f07a8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar および nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

文字データ型は固定長、 **nchar**、または可変長の**nvarchar**、Unicode データで使用する UNICODE ucs-2 文字セット。
  
## <a name="arguments"></a>引数  
**nchar** [(n)]  
固定長の Unicode 文字列データです。 *n*文字列の長さを定義して、1 ~ 4,000 値を指定する必要があります。 ストレージのサイズは 2 回 *n* バイトです。 ストレージのサイズがまだは照合順序コード ページは、2 バイト文字を使用するときに *n* バイトです。 文字列のストレージのサイズによっては *n* バイトには、指定された値より小さくなること *n*です。 ISO シノニム**nchar**は**national char**と**各国語文字**.
  
**nvarchar** [(n |**max** )]  
可変長の Unicode 文字列データです。 *n*文字列の長さを定義し、1 ~ 4,000 の値を指定できます。 **max**ストレージの最大サイズが 2 であることを示します。 ^ 31-1 バイト (2 GB)。 記憶領域のサイズ (バイト単位) は、入力したデータの実際の長さの 2 倍のバイト数に 2 バイトを足した数です。 ISO シノニム**nvarchar**は**varying、national char**と**各国語文字 varying**です。
  
## <a name="remarks"></a>解説  
ときに *n* が指定されていないデータ定義または変数宣言ステートメントで、既定の長さは 1 です。 ときに *n* が指定されていない、CAST 関数で、既定の長さは 30 です。
  
使用して**nchar**列データ エントリのサイズと思われる場合と同様にします。
  
使用して**nvarchar**列データ エントリのサイズが大幅に異なる可能性がありますとれる場合。
  
**sysname**と機能的に等価であるシステム提供のユーザー定義データ型は、 **nvarchar (128)**, が許容されない点が異なります。 **sysname**データベース オブジェクト名を参照するために使用します。
  
使用するオブジェクト**nchar**または**nvarchar** COLLATE 句を使用して、特定の照合順序が割り当てられていない限り、データベースの既定の照合順序を割り当てられています。
  
SET ANSI_PADDING は ON に、常に**nchar**と**nvarchar**です。 SET ANSI_PADDING OFF には適用されません、 **nchar**または**nvarchar**データ型。
  
プレフィックスの Unicode 文字列定数には、文字 n を付けます。なし、N プレフィックスは、文字列は、データベースの既定のコード ページに変換されます。 この既定のコード ページでは、一部の文字が認識されない場合があります。
 
> [!NOTE]  
>  文字列定数と、文字 N を付けること、ときに、定数に変換する Unicode 文字列データ型 (4,000) の最大長を超えない場合 Unicode 文字列に暗黙的な変換が発生します。 それ以外の場合、暗黙的な変換は、Unicode 大きな値 (max) になります。
  
> [!WARNING]  
>  各 null **varchar (max)**または**nvarchar (max)**列が並べ替え操作中に 8,060 バイトの行の制限に対してカウントする追加の固定割り当ての 24 バイトが必要です。 これは、暗黙的な null 以外の数に制限を作成できます**varchar (max)**または**nvarchar (max)**列、テーブルに作成できます。 テーブルの作成時やデータ挿入時に、最大行サイズが許容最大値の 8060 バイトを超えるという通常の警告以外の、特別なエラーは提供されません。 この大きな行サイズが原因で、クラスター化インデックス キーの更新や列セット全体の並べ替えなどの通常操作の一部でエラー (エラー 512 など) が発生する可能性があります。これは操作を実行するまでユーザーは予測することができません。  
  
## <a name="converting-character-data"></a>文字データの変換  
文字データを変換する方法については、次を参照してください。 [char および varchar & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="examples"></a>使用例  
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyNCharColumn nchar(15)  
,MyNVarCharColumn nvarchar(20)
  
);  
  
GO  
INSERT INTO dbo.MyTable VALUES (N'Test data', N'More test data');  
GO  
SELECT MyNCharColumn, MyNVarCharColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyNCharColumn   MyNVarCharColumn  
--------------- --------------------  
Test data       More test data  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[ような & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)
  
  

