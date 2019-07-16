---
title: sys.partitions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- partitions
- partitions_TSQL
- sys.partitions_TSQL
- sys.partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partitions catalog view
ms.assetid: 1c19e1b1-c925-4dad-a652-581692f4ab5e
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 661a37b4136202b9a83b863535670a88a3f100dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102185"
---
# <a name="syspartitions-transact-sql"></a>sys.partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース内のすべてのテーブルとほとんどの種類のインデックスのパーティションごとに 1 行のデータを保持します。 このビューでは、フルテキスト、空間、XML などの特殊なインデックスの種類は含まれません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルとインデックスは、明示的にパーティション分割されているかどうかに関係なく、1 つ以上のパーティションが保持されているものと見なされます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|object_id|**int**|このパーティションが所属するオブジェクトの ID を示します。 すべてのテーブルまたはビューは、少なくとも 1 つのパーティションで構成されます。|  
|index_id|**int**|このパーティションが所属するオブジェクト内のインデックスの ID を示します。<br /><br /> 0 = ヒープ<br />1 = クラスター化インデックス<br />2 以上 = 非クラスター化インデックス|  
|partition_number|**int**|所有しているインデックスまたはヒープ内で 1 から始まるパーティション番号です。 非パーティション テーブルとインデックスの場合は、この列の値は 1 です。|  
|hobt_id で|**bigint**|このパーティションの行を保持するデータ ヒープまたは B ツリーの ID を示します。|  
|rows|**bigint**|このパーティション内の行の概算数を示します。|  
|filestream_filegroup_id|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このパーティションに格納されている FILESTREAM ファイル グループの ID を示します。|  
|data_compression|**tinyint**|各パーティションの圧縮の状態を示します。<br /><br /> 0 = NONE <br />1 行を = <br />2 ページを = <br />3 = 列ストア。**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />4 = COLUMNSTORE_ARCHIVE:**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> **注:** 任意のエディションでフルテキスト インデックスが圧縮される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|data_compression_desc|**nvarchar(60)**|各パーティションの圧縮の状態を示します。 行ストア テーブルに指定できる値は、NONE、ROW、および PAGE です。 列ストア テーブルに指定できる値は COLUMNSTORE および COLUMNSTORE_ARCHIVE です。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
