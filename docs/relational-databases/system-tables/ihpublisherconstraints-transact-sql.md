---
title: IHpublisherconstraints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- IHpublisherconstraints
- IHpublisherconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherconstraints system table
ms.assetid: 537b1e1a-7228-4680-aa27-5ad7072ea01e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d924e432a45d900092be6e84ed110afd66951d6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732530"
---
# <a name="ihpublisherconstraints-transact-sql"></a>IHpublisherconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublisherconstraints**システム テーブルにはから SQL Server 以外のパブリッシャー、現在のディストリビューターを使用してレプリケートされた制約ごとに 1 行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisherconstraint_id**|**int**|パブリッシュされた制約を識別します。|  
|**table_id**|**int**|テーブルを識別する[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)制約が属しています。|  
|**publisher_id**|**smallint**|-SQL Server 以外のパブリッシャーの列がパブリッシュされる元を識別します。|  
|**名前**|**sysname**|パブリッシュされた制約の名前です。|  
|**型**|**nvarchar (255)**|サポートされている制約の種類から、 [IHconstrainttypes](../../relational-databases/system-tables/ihconstrainttypes-transact-sql.md)システム テーブル。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
