---
title: IHindextypes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHindextypes
- IHindextypes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHindextypes system table
ms.assetid: 5eb67d59-a19d-4dba-9d2b-657f87818f6b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b522f4a1e7de1bc82aca53d48362878f64a8718
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802334"
---
# <a name="ihindextypes-transact-sql"></a>IHindextypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHindextypes**システム テーブルには SQL Server 以外のパブリッシャーがサポートされている SQL Server 以外のインデックスの種類ごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**type**|**nvarchar (255)**|サポートされている非 SQL Server インデックスの種類の名前。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
