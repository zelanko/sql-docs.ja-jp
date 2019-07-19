---
title: sys.dm_db_persisted_sku_features (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: f59d96f9a1aa6598c5acb4fe9a88ea57965ede5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096269"
---
# <a name="sysdmdbpersistedskufeatures-transact-sql"></a>sys.dm_db_persisted_sku_features (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  一部の機能、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]方法を変更する[!INCLUDE[ssDE](../../includes/ssde-md.md)]データベース ファイルの情報を格納します。 これらの機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のエディションでのみ使用できます。 これらの機能を備えたデータベースを、それらをサポートしない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションに移動することはできません。 現在のデータベースで有効なエディション固有の機能を一覧表示するのにには、sys.dm_db_persisted_sku_features 動的管理ビューを使用します。
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] まで)。
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|feature_name|**sysname**|データベースでは有効になっているが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションでサポートされるとは限らない機能の外部名。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の使用可能なすべてのエディションにデータベースを移行するには、この機能を削除する必要があります。|  
|feature_id|**int**|機能に関連付けられている機能 ID。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] 。|  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 データベースでは、特定のエディションを制限できる機能は使用されず場合、ビューに行は返されません。  
  
 特定の制限とは、sys.dm_db_persisted_sku_features に、次のデータベース変更機能が一覧表示可能性があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディション。  
  
-   **ChangeCapture**:変更データ キャプチャ機能がデータベースで有効になっていることを示します。 変更データ キャプチャを削除するには、使用、 [sys.sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)ストアド プロシージャ。 詳細については、「[変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)」を参照してください。  
  
-   **ColumnStoreIndex**:その 1 つ以上のテーブルが列ストア インデックスを示します。 エディションに移動するデータベースを有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]この機能をサポートしていないを使用して、 [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)または[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)列ストア インデックスを削除するステートメント。 詳細については、次を参照してください。[列ストア インデックス](../../relational-databases/indexes/columnstore-indexes-overview.md)します。  
  
    **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] まで)。  
  
-   **圧縮**:少なくとも 1 つのテーブルまたはインデックスで、データ圧縮または vardecimal ストレージ形式を使用していることを示します。 エディションに移動するデータベースを有効にする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]この機能をサポートしていないを使用して、 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)データ圧縮を削除するステートメント。 vardecimal ストレージ形式を削除するには、sp_tableoption ステートメントを使用します。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
-   **MultipleFSContainers**:データベースが複数の FILESTREAM コンテナーを使用することを示します。 データベースでは、複数のコンテナー (ファイル) を含む FILESTREAM ファイル グループがあります。 詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)」をご覧ください。  
  
-   **InMemoryOLTP**:データベースでインメモリ OLTP が使用されていることを示します。 データベースには、MEMORY_OPTIMIZED_DATA ファイル グループがあります。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
  **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] まで)。 
  
-   **パーティション分割します。** パーティション テーブル、パーティション インデックス、パーティション構成、またはパーティション関数が、データベースに含まれていることを示します。 Enterprise Edition と Developer Edition 以外の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションにデータベースを移動できるようにするには、テーブルを単一パーティションに変更するだけでは不十分です。 パーティション テーブルを削除する必要があります。 テーブルにデータが含まれている場合は、SWITCH PARTITION を使用して、各パーティションを非パーティション テーブルに変換します。 その後、パーティション テーブル、パーティション構成、およびパーティション関数を削除します。  
  
-   **TransparentDataEncryption.** 透過的なデータ暗号化を使用してデータベースが暗号化されていることを示します。 透過的なデータ暗号化を削除するには、ALTER DATABASE ステートメントを使用します。 詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)」を参照してください。  

> [!NOTE]
> 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]Service Pack 1 では、これらの機能は使用可能な複数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディション、のみ Enterprise または Developer Edition に限定されずします。

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
  
