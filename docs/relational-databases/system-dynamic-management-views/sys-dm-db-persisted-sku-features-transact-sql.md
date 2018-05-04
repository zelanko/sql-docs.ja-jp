---
title: sys.dm_db_persisted_sku_features (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_persisted_sku_features_TSQL
- sys.dm_db_persisted_sku_features
- dm_db_persisted_sku_features_TSQL
- dm_db_persisted_sku_features
dev_langs:
- TSQL
helpviewer_keywords:
- editions [SQL Server], feature restrictions
- sys.dm_db_persisted_sku_features dynamic management view
ms.assetid: b4b29e97-b523-41b9-9528-6d4e84b89e09
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92ffc2534ed98b3f4ce03c03082b1cee2e14ae6f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdbpersistedskufeatures-transact-sql"></a>sys.dm_db_persisted_sku_features (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  一部の機能、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]方法を変更する[!INCLUDE[ssDE](../../includes/ssde-md.md)]データベース ファイルに情報を格納します。 これらの機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のエディションでのみ使用できます。 これらの機能を備えたデータベースを、それらをサポートしない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションに移動することはできません。 現在のデータベースで有効なエディション固有の機能を一覧表示するのにには、sys.dm_db_persisted_sku_features 動的管理ビューを使用します。
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|feature_name|**sysname**|データベースでは有効になっているが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションでサポートされるとは限らない機能の外部名。 使用可能なすべてのエディションにデータベースを移行できる前に、この機能を削除する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|feature_id|**int**|機能に関連付けられている機能 ID。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]」を参照してください。|  
  
## <a name="permissions"></a>権限  
 データベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 データベースに制限できるは特定のエディションで機能を使用しない場合、ビューは行を返しません。  
  
 sys.dm_db_persisted_sku_features を特定の制限として、次のデータベース変更機能が一覧表示ことがあります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディション。  
  
-   **ChangeCapture**: データベースの変更データ キャプチャが有効になっていることを示します。 削除するには変更データ キャプチャを使用して、 [sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)ストアド プロシージャです。 詳細については、「[変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)」を参照してください。  
  
-   **ColumnStoreIndex**: その 1 つ以上のテーブルが列ストア インデックスを示します。 エディションに移動するデータベースを有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]この機能をサポートしていないを使用して、 [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)または[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)列ストア インデックスを削除するステートメント。 詳細については、次を参照してください。[列ストア インデックス](../../relational-databases/indexes/columnstore-indexes-overview.md)です。  
  
    **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
-   **圧縮**: データ圧縮または vardecimal ストレージ形式の少なくとも 1 つのテーブルまたはインデックスを使用することを示します。 エディションに移動するデータベースを有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]この機能をサポートしていないを使用して、 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)データ圧縮を削除するステートメント。 vardecimal ストレージ形式を削除するには、sp_tableoption ステートメントを使用します。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
-   **MultipleFSContainers**: データベースが複数の FILESTREAM コンテナーを使用することを示します。 データベースでは、複数のコンテナー (ファイル) での FILESTREAM ファイル グループに存在します。 詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)」をご覧ください。  
  
-   **InMemoryOLTP**: データベースがインメモリ OLTP を使用することを示します。 データベースには、MEMORY_OPTIMIZED_DATA ファイル グループがあります。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
  **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。 
  
-   **パーティション分割します。** パーティション テーブル、パーティション インデックス、パーティション構成、またはパーティション関数が、データベースに含まれていることを示します。 エディションに移動するデータベースを有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Enterprise または Developer の場合は、以外は 1 つのパーティション上にあるテーブルを変更するだけで十分です。 パーティション テーブルを削除する必要があります。 テーブルにデータが含まれている場合は、SWITCH PARTITION を使用して、各パーティションを非パーティション テーブルに変換します。 その後、パーティション テーブル、パーティション構成、およびパーティション関数を削除します。  
  
-   **TransparentDataEncryption.** 透過的なデータ暗号化を使用してデータベースが暗号化されていることを示します。 透過的なデータ暗号化を削除するには、ALTER DATABASE ステートメントを使用します。 詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。  

> [!NOTE]
> 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]Service Pack 1 では、これらの機能は使用可能な複数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディションでは、これらに限定されない Enterprise または Developer Edition のみとします。

 特定のエディションでのみ使用できる機能がデータベースで使用されているかどうかを確認するには、データベースで次のステートメントを実行します。  
  
```sql  
SELECT feature_name FROM sys.dm_db_persisted_sku_features;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [エディションと SQL Server 2016 のサポートされる機能](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [エディションと SQL Server 2017 のサポートされる機能](../../sql-server/editions-and-components-of-sql-server-2017.md)  
  
