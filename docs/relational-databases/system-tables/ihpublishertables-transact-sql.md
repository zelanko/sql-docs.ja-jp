---
title: IHpublishertables (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishertables
- IHpublishertables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishertables system table
ms.assetid: 7d16ac39-633a-4fe2-8f22-1d9afc191ee9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f9c80d1f3a4ac02cac11c4ecbd912fe766a58050
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813267"
---
# <a name="ihpublishertables-transact-sql"></a>IHpublishertables (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishertables**システムテーブルは、パブリッシャーに格納されているメタデータを表します。 このテーブルは、現在のディストリビューターを使用する SQL&#xA0;Server 以外のパブリッシャーからパブリッシュされたソース テーブルごとに 1 行を保持します。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|パブリッシュされたテーブルを識別します。|  
|**publisher_id**|**smallint**|テーブルをパブリッシュしている SQL&#xA0;Server 以外のパブリッシャーを識別します。|  
|**name**|**sysname**|パブリッシュされたテーブルの名前。|  
|**責任**|**sysname**|テーブルの所有者。|  
  
## <a name="see-also"></a>参照  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
