---
title: sp_estimate_data_compression_savings (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_estimate_data_compression_savings_TSQL
- sp_estimate_data_compression_savings
dev_langs:
- TSQL
helpviewer_keywords:
- compression [SQL Server], estimating
- sp_estimate_data_compression_savings
ms.assetid: 6f6c7150-e788-45e0-9d08-d6c2f4a33729
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 533e4245bc731b55eeb373aa86fd10947d84488c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spestimatedatacompressionsavings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  要求されたオブジェクトの現在のサイズ、および要求された圧縮状態での推定オブジェクト サイズを返します。 圧縮は、テーブル全体またはテーブルの一部について評価できます。 これには、ヒープ、クラスター化インデックス、非クラスター化インデックス、インデックス付きビュー、およびテーブル パーティションとインデックス パーティションが含まれます。 オブジェクトは、行の圧縮またはページの圧縮を使用して圧縮できます。 テーブル、インデックス、またはパーティションが既に圧縮されている場合は、このプロシージャを使用して、再圧縮された場合のテーブル、インデックス、またはパーティションのサイズを推定できます。  
  
> [!NOTE]  
>  圧縮と**sp_estimate_data_compression_savings**のすべてのエディションでは使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 要求された圧縮設定を使用した場合のオブジェクト サイズを推定するために、このストアド プロシージャでは、ソース オブジェクトがサンプリングされ、そのデータが tempdb に作成された同等のテーブルとインデックスに読み込まれます。 さらに、tempdb に作成されたテーブルまたはインデックスが要求された設定に圧縮され、圧縮で削減される推定領域が計算されます。  
  
 テーブル、インデックス、またはパーティションの使用の圧縮状態を変更する、 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)ステートメントです。 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
> [!NOTE]  
>  既存のデータが断片化されている場合は、インデックスを再構築することで、圧縮を使用しなくてもデータのサイズを削減できる可能性があります。 インデックスについては、再構築中に FILL FACTOR が適用されます。 これによってインデックスのサイズが増える可能性があります。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_estimate_data_compression_savings   
     [ @schema_name = ] 'schema_name'    
   , [ @object_name = ] 'object_name'   
   , [@index_id = ] index_id   
   , [@partition_number = ] partition_number   
   , [@data_compression = ] 'data_compression'   
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @schema_name=] '*schema_name*'  
 テーブルまたはインデックス付きビューを含んでいるデータベース スキーマの名前です。 *schema_name*は**sysname**です。 場合*schema_name* NULL の場合は、現在のユーザーの既定のスキーマを使用します。  
  
 [ @object_name=] '*object_name*'  
 インデックスが有効になっているテーブルまたはインデックス付きビューの名前です。 *object_name* は **sysname** です。  
  
 [ @index_id=] '*index_id*'  
 インデックスの ID です。 *index_id*は**int**、値は次のいずれかを指定できます。 インデックス、NULL の場合、または 0 の場合の ID 番号*object_id*ヒープ。 ベース テーブルまたはビューのすべてのインデックスについて情報を返すには、NULL を指定します。 NULL を指定する場合も NULL を指定する必要があります*partition_number*です。  
  
 [ @partition_number=] '*partition_number*'  
 オブジェクトのパーティション番号です。 *partition_number*は**int**値は次のいずれかを指定できます。 インデックスまたはヒープ、NULL または 1 パーティション分割されていないインデックスまたはヒープのパーティション番号。  
  
 パーティションを指定するには、指定することも、 [$partition](../../t-sql/functions/partition-transact-sql.md)関数。 所有するオブジェクトのすべてのパーティションについて情報を返すには、NULL を指定します。  
  
 [ @data_compression=] '*data_compression*'  
 評価される圧縮の種類です。 *data_compression*値は次のいずれかになります。 [なし]、行、またはページです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 テーブル、インデックス、またはパーティションの現在のサイズと推定サイズの情報を提供する以下の結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|テーブルまたはインデックス付きビューの名前。|  
|schema_name|**sysname**|テーブルまたはインデックス付きビューのスキーマ。|  
|index_id|**int**|インデックスのインデックス ID。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス|  
|partition_number|**int**|パーティション番号。 非パーティション テーブルまたはインデックスの場合は 1 を返します。|  
|size_with_current_compression_setting (KB)|**bigint**|要求されたテーブル、インデックス、またはパーティションの現在のサイズ。|  
|size_with_requested_compression_setting (KB)|**bigint**|要求された圧縮設定を使用するテーブル、インデックス、またはパーティションの推定サイズ。該当する場合は既存の FILL FACTOR を適用し、断片化が生じていないことを前提としています。|  
|sample_size_with_current_compression_setting (KB)|**bigint**|現在の圧縮設定を使用するサンプルのサイズ。 この列には、断片化も含まれます。|  
|sample_size_with_requested_compression_setting (KB)|**bigint**|要求された圧縮設定を使用して作成されたサンプルのサイズ。該当する場合は既存の FILL FACTOR を適用し、断片化は考慮していません。|  
  
## <a name="remarks"></a>解説  
 sp_estimate_data_compression_savings は、テーブルまたはパーティションで行またはページの圧縮を有効にした場合に削減できる領域を推定する場合に使用します。 たとえば、行の平均サイズを 40% 削減できれば、オブジェクトのサイズを 40% 削減できる可能性があります。 これは FILL FACTOR と行サイズに左右されるため、領域を削減できない場合もあります。 たとえば、長さ 8,000 バイトの行があり、そのサイズを 40% 削減したとしても、データ ページに収まるのは 1 行のみであることに変わりはないので、 領域は削減されません。  
  
 sp_estimate_data_compression_savings を実行してテーブルが増大するという結果が示される場合は、テーブルの多くの行でデータ型の有効桁数がほとんど使用されており、圧縮された形式に必要なわずかなオーバーヘッドが積み重なって、圧縮による削減量を上回ることを意味しています。 このようなまれなケースでは、圧縮を使用しないでください。  
  
 テーブルで圧縮が有効になっている場合は、sp_estimate_data_compression_savings を使用して、テーブルが圧縮されていない場合の平均行サイズを推定します。  
  
 この操作中に、テーブルで (IS) ロックが取得されます。 (IS) ロックを取得できない場合は、プロシージャがブロックされます。 テーブルは、READ COMMITTED 分離レベルでスキャンされます。  
  
 要求された圧縮設定が現在の圧縮設定と同じである場合は、ストアド プロシージャが既存の FILL FACTOR を使用して、データが断片化されていない状態での推定サイズを返します。  
  
 インデックス ID またはパーティション ID が存在しない場合は、結果が返されません。  
  
## <a name="permissions"></a>権限  
 テーブルに対する SELECT 権限が必要です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 このプロシージャは列ストア テーブルには適用されないため、データ圧縮パラメーター COLUMNSTORE および COLUMNSTORE_ARCHIVE を指定できません。  
  
## <a name="examples"></a>使用例  
 次の例では、`Production.WorkOrderRouting` 圧縮を使用して `ROW` テーブルを圧縮した場合のサイズを推定します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimate_data_compression_savings 'Production', 'WorkOrderRouting', NULL, NULL, 'ROW' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Unicode 圧縮の実装](../../relational-databases/data-compression/unicode-compression-implementation.md)  
  
  
