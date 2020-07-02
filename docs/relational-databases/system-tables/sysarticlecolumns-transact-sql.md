---
title: sysarticlecolumns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3c295da10074efbd6e4ee1b014b754ac8622ba73
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753856"
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **Sysarticlecolumns**テーブルには、スナップショットパブリケーションまたはトランザクションパブリケーションでパブリッシュされるテーブル列ごとに1つの行が含まれ、各列がアーティクルにマップされます。 このテーブルは、パブリケーションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルを識別します。|  
|**colid**|**smallint**|アーティクル内の列を識別します。|  
|**is_udt**|**bit**|列がユーザー定義データ型 (UDT) 列であるかどうかを示します。 値**1**は UDT 列を示します。|  
|**is_xml**|**bit**|列が**xml**列かどうかを示します。 値**1**は xml 列を示します。|  
|**is_max**|**bit**|列が大きな値のデータ型の列、 **varchar (max)**、 **nvarchar (max)**、および**varbinary (max)** であるかどうかを示します。 値**1**は大きな値の列を示します。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
