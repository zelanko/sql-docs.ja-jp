---
title: IHpublishercolumns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6a8a2c4d6850b814d79b360ff9748579cf44b7b1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757570"
---
# <a name="ihpublishercolumns-transact-sql"></a>IHpublishercolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumns**システム テーブルは、パブリッシャー側で格納されているメタデータを表します。 このテーブルには、1 行から SQL Server 以外のパブリッシャー、現在のディストリビューターを使用してレプリケートされた各列のデータが含まれています。 データ型情報**IHpublishercolumns**データの発行元の SQL Server データベース管理システム (DBMS) に固有です。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|パブリッシュされた列の識別子。|  
|**table_id**|**int**|ソース テーブルを識別する[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)列が属しています。|  
|**publisher_id**|**smallint**|-SQL Server 以外のパブリッシャーの列がパブリッシュされる元を識別します。|  
|**name**|**sysname**|パブリッシュされた列の名前。|  
|**column_ordinal**|**int**|順序に基づいた列の識別子。|  
|**type**|**varchar(255)**|パブリッシャー側にあるパブリッシュ元となる列の列データ型。|  
|**length**|**bigint**|パブリッシャー側にあるパブリッシュ元となる列の長さ。|  
|**prec**|**int**|パブリッシャー側にあるパブリッシュ元となる列の有効桁数。|  
|**scale**|**int**|パブリッシャー側にあるパブリッシュ元となる列の小数点以下桁数。|  
|**isnullable**|**bit**|列に NULL 値を受け入れるかどうかを示す、 **1** NULL 値を受け入れることを意味します。|  
|**iscaptured**|**bit**|列にトリガーが存在するかどうかを示します。列がアーティクルにパブリッシュされない場合もトリガーが存在することがあります。 値**1**列に、トリガーが存在することを意味します。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sysarticlecolumns&#40;システム ビュー&#41; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
