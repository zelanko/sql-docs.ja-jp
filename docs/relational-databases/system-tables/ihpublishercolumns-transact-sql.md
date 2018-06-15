---
title: IHpublishercolumns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
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
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4bd15161e658348ea68c2f87c1468ede00bac5e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33003759"
---
# <a name="ihpublishercolumns-transact-sql"></a>IHpublishercolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumns**システム テーブルは、パブリッシャー側で格納されているメタデータを表します。 このテーブルには、レプリケートから SQL Server 以外のパブリッシャー、現在のディストリビューターを使用して各列の 1 つの行が含まれています。 データ型の情報が**IHpublishercolumns**データのパブリッシュ元となる SQL Server データベース管理システム (DBMS) に固有です。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|パブリッシュされた列の識別子。|  
|**table_id**|**int**|ソース テーブルからの識別[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)列が属しています。|  
|**publisher_id**|**smallint**|-SQL Server 以外のパブリッシャー、列の発行元を識別します。|  
|**name**|**sysname**|パブリッシュされた列の名前。|  
|**column_ordinal**|**int**|順序に基づいた列の識別子。|  
|**type**|**varchar(255)**|パブリッシャー側にあるパブリッシュ元となる列の列データ型。|  
|**長さ**|**bigint**|パブリッシャー側にあるパブリッシュ元となる列の長さ。|  
|**prec**|**int**|パブリッシャー側にあるパブリッシュ元となる列の有効桁数。|  
|**scale**|**int**|パブリッシャー側にあるパブリッシュ元となる列の小数点以下桁数。|  
|**isnullable**|**bit**|列が NULL 値を受け入れるかどうかを示す、 **1** NULL 値を受け入れることを意味します。|  
|**iscaptured**|**bit**|列にトリガーが存在するかどうかを示します。列がアーティクルにパブリッシュされない場合もトリガーが存在することがあります。 値**1**列にトリガーが存在することを意味します。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sysarticlecolumns&#40;システム ビュー&#41; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
