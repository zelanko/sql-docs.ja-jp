---
title: テーブル サイズの見積もり | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f7e8e39f5bf3eb0464907a480e33223ec6d9885c
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558569"
---
# <a name="estimate-the-size-of-a-table"></a>テーブル サイズの見積もり
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  次の手順を実行して、テーブルにデータを格納するために必要な領域を見積もることができます。  
  
1.  「 [ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md) 」または「 [クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)」の説明に従って、ヒープまたはクラスター化インデックスに必要な領域を計算します。  
  
2.  「 [非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)」に記載されている手順に従って、非クラスター化インデックスごとに必要な領域を計算します。  
  
3.  手順 1. と手順 2. で計算した値を加算します。  
  
## <a name="see-also"></a>参照  
 [データベース サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
