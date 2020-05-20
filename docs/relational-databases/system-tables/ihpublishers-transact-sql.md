---
title: IHpublishers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishers
- IHpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishers system table
ms.assetid: 77007246-f10b-4b87-8edf-7afc3c2096af
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9035598991b846fa36edf17631b9d9bf9ec878e3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832373"
---
# <a name="ihpublishers-transact-sql"></a>IHpublishers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishers**システムテーブルには、現在のディストリビューターを使用する非 SQL Server パブリッシャーごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|SQL Server 以外のパブリッシャーを識別します。|  
|**業者**|**sysname**|SQL&#xA0;Server 以外のデータベースの製造元の名前です。|  
|**publisher_guid**|**uniqueidentifier**|SQL Server 以外のパブリッシャーを識別する GUID。|  
|**flush_request_time**|**datetime**|メタデータキャッシュを更新するためにログリーダーエージェントが必要とした、アーティクルメタデータに対して最後に変更が行われた日時を示します。|  
|**version**|**sysname**|SQL&#xA0;Server 以外のパブリッシャーのバージョンの特徴を表すテキスト文字列です。|  
  
## <a name="see-also"></a>参照  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)  
  
  
