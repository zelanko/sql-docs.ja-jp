---
title: sp_estimate_data_compression_savings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 70efe047d1fae61f9755c2dbeecf9627de5b5a79
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713954"
---
# <a name="spestimatedatacompressionsavings-transact-sql"></a>sp_estimate_data_compression_savings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  要求されたオブジェクトの現在のサイズ、および要求された圧縮状態での推定オブジェクト サイズを返します。 圧縮は、テーブル全体またはテーブルの一部について評価できます。 これには、ヒープ、クラスター化インデックスが含まれますが、非クラスター化インデックス、列ストア インデックス、インデックス付きビュー、およびテーブルおよびインデックス パーティション。 オブジェクトは、行、ページ、列ストアまたは列ストア アーカイブの圧縮を使用して圧縮できます。 テーブル、インデックス、またはパーティションが既に圧縮されている場合は、このプロシージャを使用して、再圧縮された場合のテーブル、インデックス、またはパーティションのサイズを推定できます。  
  
> [!NOTE]  
>  圧縮と**sp_estimate_data_compression_savings**のすべてのエディションでは使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 要求された圧縮設定を使用した場合のオブジェクト サイズを推定するために、このストアド プロシージャでは、ソース オブジェクトがサンプリングされ、そのデータが tempdb に作成された同等のテーブルとインデックスに読み込まれます。 さらに、tempdb に作成されたテーブルまたはインデックスが要求された設定に圧縮され、圧縮で削減される推定領域が計算されます。  
  
 テーブル、インデックス、またはパーティションの使用の圧縮状態を変更する、 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)ステートメント。 圧縮の詳細については、次を参照してください。[データ圧縮](../../relational-databases/data-compression/data-compression.md)します。  
  
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
 テーブルまたはインデックス付きビューを含んでいるデータベース スキーマの名前です。 *schema_name*は**sysname**します。 場合*schema_name*が null の場合、現在のユーザーの既定のスキーマを使用します。  
  
 [ @object_name=] '*object_name*'  
 インデックスが有効になっているテーブルまたはインデックス付きビューの名前です。 *object_name* は **sysname** です。  
  
 [ @index_id=] '*index_id*'  
 インデックスの ID です。 *index_id*は**int**、値は次のいずれかを指定できます。 インデックスや NULL の場合は 0 の ID 番号*object_id*ヒープ。 ベース テーブルまたはビューのすべてのインデックスについて情報を返すには、NULL を指定します。 NULL を指定する場合は NULL も指定する必要があります*partition_number*します。  
  
 [ @partition_number=] '*partition_number*'  
 オブジェクトのパーティション番号です。 *partition_number*は**int**値は次のいずれかを指定できます。 インデックスまたはヒープ、NULL、または 1 をパーティション分割されていないインデックスまたはヒープのパーティション番号。  
  
 パーティションを指定するには、指定の[$partition](../../t-sql/functions/partition-transact-sql.md)関数。 所有するオブジェクトのすべてのパーティションについて情報を返すには、NULL を指定します。  
  
 [ @data_compression=] '*data_compression*'  
 評価される圧縮の種類です。 *data_compression*値は次のいずれかを指定できます。 NONE、行、ページ、列ストア、または COLUMNSTORE_ARCHIVE です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 テーブル、インデックス、またはパーティションの現在のサイズと推定サイズの情報を提供する以下の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|object_name|**sysname**|テーブルまたはインデックス付きビューの名前。|  
|schema_name|**sysname**|テーブルまたはインデックス付きビューのスキーマ。|  
|index_id|**int**|インデックスのインデックス ID。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス|  
|partition_number|**int**|パーティション番号。 非パーティション テーブルまたはインデックスの場合は 1 を返します。|  
|size_with_current_compression_setting (KB)|**bigint**|要求されたテーブル、インデックス、またはパーティションの現在のサイズ。|  
|size_with_requested_compression_setting (KB)|**bigint**|要求された圧縮設定を使用するテーブル、インデックス、またはパーティションの推定サイズ。該当する場合は既存の FILL FACTOR を適用し、断片化が生じていないことを前提としています。|  
|sample_size_with_current_compression_setting (KB)|**bigint**|現在の圧縮設定を使用するサンプルのサイズ。 この列には、断片化も含まれます。|  
|sample_size_with_requested_compression_setting (KB)|**bigint**|要求された圧縮設定を使用して作成されたサンプルのサイズ。該当する場合は既存の FILL FACTOR を適用し、断片化は考慮していません。|  
  
## <a name="remarks"></a>コメント  
 テーブルまたはパーティションの行、ページ、列ストアまたは列ストア アーカイブの圧縮を有効にしたときに発生するコスト削減を推定するには、sp_estimate_data_compression_savings を使用します。 たとえば、行の平均サイズを 40% 削減できれば、オブジェクトのサイズを 40% 削減できる可能性があります。 これは FILL FACTOR と行サイズに左右されるため、領域を削減できない場合もあります。 たとえば、長さ 8,000 バイトの行があり、そのサイズを 40% 削減したとしても、データ ページに収まるのは 1 行のみであることに変わりはないので、 領域は削減されません。  
  
 sp_estimate_data_compression_savings を実行してテーブルが増大するという結果が示される場合は、テーブルの多くの行でデータ型の有効桁数がほとんど使用されており、圧縮された形式に必要なわずかなオーバーヘッドが積み重なって、圧縮による削減量を上回ることを意味しています。 このようなまれなケースでは、圧縮を使用しないでください。  
  
 テーブルで圧縮が有効になっている場合は、sp_estimate_data_compression_savings を使用して、テーブルが圧縮されていない場合の平均行サイズを推定します。  
  
 この操作中に、テーブルで (IS) ロックが取得されます。 (IS) ロックを取得できない場合は、プロシージャがブロックされます。 テーブルは、READ COMMITTED 分離レベルでスキャンされます。  
  
 要求された圧縮設定が現在の圧縮設定と同じである場合は、ストアド プロシージャが既存の FILL FACTOR を使用して、データが断片化されていない状態での推定サイズを返します。  
  
 インデックス ID またはパーティション ID が存在しない場合は、結果が返されません。  
  
## <a name="permissions"></a>アクセス許可  
 テーブルに対する SELECT 権限が必要です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 SQL Server の 2019 の前に、この手順は、列ストア インデックスに適用されなかったし、そのため、データ圧縮パラメーター COLUMNSTORE と COLUMNSTORE_ARCHIVE が受け入れられませんでした。  SQL Server 2019 以降、列ストア インデックスができますを推定するためのソース オブジェクトと、要求された圧縮の種類の両方。

## <a name="considerations-for-columnstore-indexes"></a>列ストア インデックスに関する考慮事項
 列ストアと列ストア アーカイブの圧縮の両方を見積もる sp_estimate_compression_savings サポートに、SQL Server の 2019 以降します。 ページおよび行の圧縮とは異なり、オブジェクトに列ストア圧縮を適用することは新しい列ストア インデックスを作成する必要です。 この理由から、この手順の COLUMNSTORE と COLUMNSTORE_ARCHIVE オプションを使用する場合は、プロシージャに指定されたソース オブジェクトの種類は、圧縮サイズの推定に使用する列ストア インデックスの種類を決定します。 次の表は、参照を示しています。 ときに、各ソース オブジェクトの圧縮による削減量を推定するために使用するオブジェクト型、@data_compressionパラメーターは、列ストアまたは COLUMNSTORE_ARCHIVE のいずれかに設定されます。

 |ソース オブジェクト|参照オブジェクト|
 |-----------------|---------------|
 |ヒープ|クラスター化列ストア インデックス|
 |クラスター化インデックス|クラスター化列ストア インデックス|
 |非クラスター化インデックス|非クラスター化列ストア インデックスが (存在する場合は、キー列と指定された非クラスター化インデックスの付加列とテーブルのパーティション列を含む)|
 |非クラスター化列ストア インデックス|非クラスター化列ストア インデックスを (指定された非クラスター化列ストア インデックスと同じ列を含む)|
 |クラスター化列ストア インデックス|クラスター化列ストア インデックス|

> [!NOTE]  
> Sp_estimate_compression_ 列ストア インデックスでサポートされていないデータ型を持つソース オブジェクト内の列がある場合は、行ストアのソース オブジェクト (クラスター化インデックス、非クラスター化インデックスまたはヒープ) からの列ストア圧縮を推定するときにコスト削減については、エラーで失敗します。

 同様に、ときに、@data_compressionパラメーターが NONE、行、またはページに設定されていると、ソース オブジェクトは、列ストア インデックスを次の表に、使用される参照オブジェクト。

 |ソース オブジェクト|参照オブジェクト|
 |-----------------|---------------|
 |クラスター化列ストア インデックス|ヒープ|
 |非クラスター化列ストア インデックス|非クラスター化インデックスが (付加列として存在する場合、キーの列およびテーブルのパーティション列として非クラスター化列ストア インデックスに含まれる列を含む)|

> [!NOTE]  
> 列ストア オブジェクトのソースから行ストアの圧縮 (NONE、行またはページ) を推定するときに、元のインデックスが含まれていないこと 32 を超える列には行ストア (非クラスター化) インデックスではサポートされている制限してください。
  
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
  
  
