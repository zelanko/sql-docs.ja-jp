---
title: nchar と nvarchar (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 856f26ac921a1bbe4f467cd11b785ee3868eeac2
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643890"
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar および nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

固定長 (**nchar**)、または可変長 (**nvarchar**) の文字データ型です。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降、[補助文字 (SC)](../../relational-databases/collations/collation-and-unicode-support.md#Supplementary_Characters) が有効になっている照合順序を使用する場合、これらのデータ型には [Unicode](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn) 文字データの全範囲が格納され、[UTF-16](http://www.wikipedia.org/wiki/UTF-16) 文字エンコードが使用されます。 SC が無効の照合順序を指定する場合、これらのデータ型には [UCS-2](http://www.wikipedia.org/wiki/Universal_Coded_Character_Set#Encoding_forms) 文字エンコードでサポートされている文字データのサブセットのみが格納されます。
  
## <a name="arguments"></a>引数  
**nchar** [ ( n ) ]  
固定長の文字列データです。 *n* によってバイト ペアでの文字列の長さが定義されます。1 から 4,000 までの値にする必要があります。 ストレージのサイズは、*n* の 2 倍のバイト数です。 [UCS-2](http://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF) エンコードの場合、ストレージのサイズは *n* の 2 倍のバイト数となり、格納できる文字数もまた *n* となります。 UTF-16 エンコードの場合、ストレージのサイズは引き続き *n* の 2 倍のバイト数ですが、補助文字によって 2 つのバイト ペア (または[サロゲート ペア](http://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF)) が使用されるため、格納できる文字数は *n* よりも少なくなる場合があります。 **nchar** の ISO シノニムは、**national char** および **national character** です。
  
**nvarchar** [ ( n | **max** ) ]  
可変長の文字列データです。 *n* によってバイト ペアでの文字列の長さが定義されます。1 から 4,000 までの値を指定できます。 **max** は、ストレージの最大サイズが 2^30-1 文字 (2 GB) であることを示します。 ストレージのサイズは、*n* の 2 倍のバイト数 + 2 バイトです。 [UCS-2](http://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF) エンコードの場合、ストレージのサイズは *n* の 2 倍のバイト数 + 2 バイトとなり、格納できる文字数もまた *n* となります。 UTF-16 エンコードの場合、ストレージのサイズは引き続き *n* の 2 倍のバイト数 + 2 バイトですが、補助文字によって 2 つのバイト ペア (または[サロゲート ペア](http://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF)) が使用されるため、格納できる文字数は *n* よりも少なくなる場合があります。 ISO シノニム **nvarchar** は national char のさまざまな **と** 各国語文字がさまざまな**です**。
  
## <a name="remarks"></a>Remarks  
データ定義または変数宣言ステートメントで *n* を指定しないと、既定の長さは 1 になります。 CAST 関数で *n* を指定しないと、既定の長さは 30 になります。

**nchar** または **nvarchar** を使用する場合は、次のことをお勧めします。
- 列データ エントリのサイズが一定の場合は、**nchar** を使用します。  
- 列データ エントリのサイズが大幅に変化する場合は、**nvarchar** を使用します。  
- 列データ エントリのサイズが大幅に変化し、かつ文字列の長さが 4,000 バイト ペアを超える可能性がある場合は、**nvarchar(max)** を使用します。  
  
**sysname** と機能的に等価であるシステム提供のユーザー定義データ型は、 **nvarchar (128)**, が許容されない点が異なります。 **sysname** データベース オブジェクト名を参照するために使用します。
  
使用するオブジェクト **nchar** または **nvarchar** COLLATE 句を使用して、特定の照合順序が割り当てられていない限り、データベースの既定の照合順序は割り当てられます。
  
SET ANSI_PADDING が ON にでは常に **nchar** と **nvarchar**です。 SET ANSI_PADDING OFF には適用されませんが、 **nchar** または **nvarchar** データ型。
  
Unicode 文字の文字列定数には、プレフィックスとして文字 N を付けて UCS-2 または UTF-16 の入力を通知します。これは SC 照合順序が使用されているか使用されていないかによって異なります。 プレフィックス N がない場合、文字列はデータベースの既定のコード ページに変換され、特定の文字が認識されない場合があります。 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 以降、UTF-8 が有効になっている照合順序を使用する場合、既定のコード ページでは UNICODE UTF-8 文字セットを格納させることができます。 
 
> [!NOTE]  
> 文字列定数にプレフィックスとして文字 N を付けたときに、変換する定数の長さが nvarchar 文字列データ型の最大長 (4,000) を超えない場合、暗黙的な変換によって UCS-2 または UTF-16 の文字列が生成されます。 それ以外の場合、暗黙的な変換では大きな値の nvarchar(max) が生成されます。
  
> [!WARNING]  
> Null 以外の **varchar(max)** または **nvarchar(max)** の各列には、24 バイトの追加の固定割り当てが必要です。これは並べ替え操作中の 8,060 バイトの行制限におけるカウント対象となります。 これらの追加バイトにより、テーブル内の Null 以外の **varchar(max)** または **nvarchar(max)** の列数について、暗黙的な制限が生じます。 テーブルの作成時やデータ挿入時に、最大行サイズが許容最大値の 8,060 バイトを超えるという通常の警告以外の、特別なエラーは提供されません。 この大きな行サイズにより、一部の通常操作の間に、ユーザーが予期しないエラー (エラー 512 など) が発生することがあります。  このような操作の 2 つの例は、クラスター化インデックス キーの更新と、列セット全体の並べ替えです。
  
## <a name="converting-character-data"></a>文字データの変換  
文字データを変換する方法の詳細については、を参照してください。 [char と varchar (&) #40 です。TRANSACT-SQL と #41;](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[ように (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)    
[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)     
[1 バイト文字セットとマルチバイト文字セット](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets)  
  
