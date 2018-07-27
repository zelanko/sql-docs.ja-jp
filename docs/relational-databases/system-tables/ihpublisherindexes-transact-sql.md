---
title: IHpublisherindexes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 657d8d364d0691ec2c0150b4ca933fcd46ce8f9f
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103840"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublisherindexes**システム テーブルにはから SQL Server 以外のパブリッシャー、現在のディストリビューターを使用してレプリケートされたインデックスごとに 1 行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|パブリッシュされたインデックスを識別します。|  
|**table_id**|**int**|テーブルを識別する[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)インデックスが属しています。|  
|**publisher_id**|**smallint**|-SQL Server 以外のパブリッシャー、インデックスの発行元を識別します。|  
|**name**|**sysname**|パブリッシュされたインデックスの名前です。|  
|**type**|**nvarchar (255)**|サポートされているインデックスの種類、 [IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md)システム テーブル。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
