---
title: "IHpublishers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHpublishers
- IHpublishers_TSQL
dev_langs: TSQL
helpviewer_keywords: IHpublishers system table
ms.assetid: 77007246-f10b-4b87-8edf-7afc3c2096af
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a53ef3960364ea40ccd1911f26a31270ffd9b09b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihpublishers-transact-sql"></a>IHpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishers**システム テーブルには、1 つの行各 SQL Server 以外のパブリッシャー、現在のディストリビューターを使用してにはが含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id などがあります。**|**smallint**|-SQL Server 以外のパブリッシャーを識別します。|  
|**仕入先**|**sysname**|SQL Server 以外のデータベースのベンダーの名前。|  
|**publisher_guid**|**uniqueidentifier**|SQL Server 以外のパブリッシャーを識別する GUID です。|  
|**flush_request_time**|**datetime**|メタデータ キャッシュを更新するためにログ リーダー エージェントを必要としたアーティクル メタデータに対して最後の変更が発生した日付と時刻を示します。|  
|**version**|**sysname**|SQL Server 以外のパブリッシャーのバージョンを表すテキスト文字列。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_adddistpublisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)  
  
  
