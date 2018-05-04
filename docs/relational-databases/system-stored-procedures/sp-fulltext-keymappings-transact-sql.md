---
title: sp_fulltext_keymappings (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_keymappings_TSQL
- sp_fulltext_keymappings
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], key column
- sp_fulltext_keymappings
- full-text indexes [SQL Server], troubleshooting
ms.assetid: 2818fa42-072d-4664-a2f7-7ec363b51d81
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7237d85373e0830ea35dc247220f042699c45f77
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spfulltextkeymappings-transact-sql"></a>sp_fulltext_keymappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  ドキュメント識別子 (DocId) とフルテキスト キー値の間のマッピングを返します。 DocId 列には値が含まれています、 **bigint**フルテキスト インデックス付きテーブルで特定のフルテキスト キー値にマップされる整数です。 検索条件に一致する DocId 値は、Full-Text Engine からデータベース エンジンに渡され、そこでクエリ対象のベース テーブルのフルテキスト キー値にマップされます。 フルテキスト キー列は、テーブルの 1 つの列で必須の一意インデックスです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_fulltext_keymappings { table_id | table_id, docid | table_id, NULL, key }  
```  
  
#### <a name="parameters"></a>パラメーター  
 *table_id*  
 フルテキスト インデックスが設定されたテーブルのオブジェクト ID。 無効なを指定する場合は*table_id*エラーが返されます。 テーブルのオブジェクト ID を取得する方法の詳細については、次を参照してください。 [OBJECT_ID &#40;TRANSACT-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)です。  
  
 *docid*  
 キー値に対応する内部ドキュメント識別子 (DocId)。 *docid* 値が無効な場合、結果は返されません。  
  
 *key*  
 指定したテーブルからのフルテキスト キー値。 *key* 値が無効な場合、結果は返されません。 フルテキスト キー値については、次を参照してください。 [、フルテキスト インデックスの管理](http://msdn.microsoft.com/library/28ff17dc-172b-4ac4-853f-990b5dc02fd1)です。  
  
> [!IMPORTANT]  
>  1 つ、2 つ、または 3 つのパラメーターを使用する方法の詳細については、後の「解説」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 [なし] :  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|DocId|**bigint**|キー値に対応する内部ドキュメント識別子 (DocId) 列。|  
|Key|*|指定したテーブルからのフルテキスト キー値。<br /><br /> マッピング テーブルにフルテキスト キーが存在しない場合は、空の行セットが返されます。|  
  
 <sup>*</sup> キーのデータ型は、ベース テーブルのフルテキスト キー列のデータ型と同じです。  
  
## <a name="permissions"></a>権限  
 この関数はパブリックであり、特別な権限は必要ありません。  
  
## <a name="remarks"></a>解説  
 次の表に、1 つ、2 つ、または 3 つのパラメーターを使用した場合の効果を示します。  
  
|パラメーター リスト|効果|  
|--------------------------|----------------------|  
|*table_id*|のみ呼び出されると、 *table_id*パラメーター、sp_fulltext_keymappings で、各キーに対応する DocId とは、指定したベース テーブルからすべてのフルテキスト キー (Key) 値が返されます。 これには削除保留中のキーが含まれます。<br /><br /> この機能は、さまざまな問題をトラブルシューティングする場合に便利です。 特に、選択したフルテキスト キーが整数データ型でないときに、フルテキスト インデックス コンテンツを確認する場合に役立ちます。 結果を含む sp_fulltext_keymappings の結果を結合では、この**sys.dm_fts_index_keywords_by_document**です。 詳細については、次を参照してください。 [sys.dm_fts_index_keywords_by_document &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)です。<br /><br /> ただし、通常は、可能であれば特定のフルテキスト キーまたは DocId を指定するパラメーターを指定して sp_fulltext_keymappings を実行することをお勧めします。 これは、キー マップ全体を返すよりもはるかに効率的です。特に、キー マップ全体を返すとパフォーマンスが大幅に低下する可能性がある、非常に大きなテーブルの場合に有効です。|  
|*table_id*, *docid*|だけの場合、 *table_id*と*docid*指定すると、 *docid* null 以外であるし、指定されたテーブルで有効な DocId を指定する必要があります。 この機能は、カスタム フルテキスト キーを、特定のフルテキスト インデックスの DocId に対応するベース テーブルから切り離す場合に役立ちます。|  
|*table_id*、NULL、*キー*|3 つのパラメーターが存在する場合は、2 番目のパラメーターが NULL の場合と*キー* null 以外であるし、指定したテーブルから有効なフルテキスト キー値を指定する必要があります。 この機能は、特定のフルテキスト キーに対応する DocId をベース テーブルから切り離す場合に役立ちます。|  
  
 次のいずれかの条件に該当する場合は、エラーが返されます。  
  
-   無効なを指定する*table_id*です。  
  
-   テーブルにフルテキスト インデックスが設定されていない場合。  
  
-   NULL 以外の値が許可されるパラメーターについて NULL が検出された場合。  
  
## <a name="examples"></a>使用例  
  
> [!NOTE]  
>  この例は、セクションの使用、`Production.ProductReview`のテーブル、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]サンプル データベース。 提示された例を実行することによってこのインデックスを作成することができます、`ProductReview`テーブルに[CREATE FULLTEXT INDEX &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)です。  
  
### <a name="a-obtaining-all-the-key-and-docid-values"></a>A. すべてのキーと DocId 値を取得する  
 次の例では、 [DECLARE](../../t-sql/language-elements/declare-local-variable-transact-sql.md)ローカル変数を作成するステートメント`@table_id`との ID を割り当て、`ProductReview`その値としてのテーブルです。 例では実行**sp_fulltext_keymappings**指定`@table_id`の*table_id*パラメーター。  
  
> [!NOTE]  
>  使用して**sp_fulltext_keymappings**のみを持つ、 *table_id*パラメーターは小さなテーブルに適しています。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id;  
GO  
  
```  
  
 テーブルから次のようにすべての DocIds とフルテキスト キーが返されます。  
  
||||  
|-|-|-|  
||`docid`|`key`|  
|`1`|`1`|`1`|  
|`2`|`2`|`2`|  
|`3`|`3`|`3`|  
|`4`|`4`|`4`|  
  
### <a name="b-obtaining-the-docid-value-for-a-specific-key-value"></a>B. 特定のキー値の DocId 値を取得する  
 次の例では、DECLARE ステートメントを使用してローカル変数 `@table_id`を作成し、 `ProductReview` テーブルの ID をその値として割り当てます。 例では実行**sp_fulltext_keymappings**を指定する`@table_id`の*table_id*パラメーターに NULL、 *docid*パラメーター、および 4 は、 *キー*パラメーター。  
  
> [!NOTE]  
>  使用して**sp_fulltext_keymappings**のみを持つ、 *table_id*指して小さなテーブルに適しています。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @table_id int = OBJECT_ID(N'Production.ProductReview');  
EXEC sp_fulltext_keymappings @table_id, NULL, 4;  
GO  
  
```  
  
 この例では、次の結果が返されます。  
  
||||  
|-|-|-|  
||`docid`|`key`|  
|`4`|`4`|`4`|  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索およびセマンティック検索ストアド プロシージャの&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
