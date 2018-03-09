---
title: "Msmerge_conflict _&lt;パブリケーション&gt;_&lt;記事&gt;(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_conflict_publication_article_TSQL
- MSmerge_conflict_publication_article
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflict_publication_article system table
ms.assetid: dc4490b4-02d8-4dfc-98f5-0cf8de8e11be
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28b48accf52de4f65772a41f9cd05a9d1e71e7dd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msmergeconflictltpublicationgtltarticlegt-transact-sql"></a>Msmerge_conflict _&lt;パブリケーション&gt;_&lt;記事&gt;(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Msmerge_conflict _*パブリケーション*_*記事** * テーブルには、競合がある行またはデータの集約を実現するために元に戻された行変更に関する情報が含まれています。. 競合テーブルはパブリケーション内のレプリケートされたテーブルごとに存在し、競合テーブルの名前にはパブリケーションとアーティクルの名前が付加されます。 このアーティクル固有の競合テーブルは、競合ログで使用するデータベースに保存されます。通常、これはパブリケーション データベースですが、集中型でない競合ログの場合はサブスクリプション データベースの場合もあります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|***article_column_name***|**変数**|レプリケートされたテーブルの列。 このシステム テーブルにはテーブル アーティクルの列ごとに 1 行のデータが格納されます。|  
|**rowguid**|**uniqueidentifier**|競合する行の行識別子。|  
|**ModifiedDate**|**datetime**|競合が発生した時刻。|  
|**origin_datasource_id**|**uniqueidentifier**|行変更が取り消された、または競合が失われたサブスクリプション。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
