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
ms.openlocfilehash: 6440eff0121b54f0b7747bef04649dada0599f4c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755473"
---
# <a name="ihpublishertables-transact-sql"></a>IHpublishertables (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **IHpublishertables**システムテーブルは、パブリッシャーに格納されているメタデータを表します。 このテーブルは、現在のディストリビューターを使用する SQL&#xA0;Server 以外のパブリッシャーからパブリッシュされたソース テーブルごとに 1 行を保持します。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|パブリッシュされたテーブルを識別します。|  
|**publisher_id**|**smallint**|テーブルをパブリッシュしている SQL&#xA0;Server 以外のパブリッシャーを識別します。|  
|**name**|**sysname**|パブリッシュされたテーブルの名前。|  
|**責任**|**sysname**|テーブルの所有者。|  
  
## <a name="see-also"></a>関連項目  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
