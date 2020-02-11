---
title: IHpublisherindexes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 114ffee3ca13d7b5a42c3843957df0a2450b787f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990247"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublisherindexes**システムテーブルには、現在のディストリビューターを使用して SQL Server 以外のパブリッシャーからレプリケートされたインデックスごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|パブリッシュされたインデックスを識別します。|  
|**table_id**|**int**|インデックスが属している[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)からテーブルを識別します。|  
|**publisher_id**|**smallint**|インデックスをパブリッシュしている SQL&#xA0;Server 以外のパブリッシャーを識別します。|  
|**name**|**sysname**|パブリッシュされたインデックスの名前。|  
|**type**|**nvarchar(255)**|[IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md)システムテーブルからサポートされているインデックスの種類。|  
  
## <a name="see-also"></a>参照  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
