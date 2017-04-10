---
title: "テーブル サイズの見積もり | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ページ [SQL Server], 領域"
  - "領域 [SQL Server], テーブル"
  - "行サイズ [SQL Server]"
  - "テーブルのサイズ [SQL Server]"
  - "列のサイズ [SQL Server]"
  - "テーブル サイズの予測 [SQL Server]"
  - "テーブル サイズ [SQL Server]"
  - "テーブル サイズの見積もり"
  - "クラスター化インデックス, テーブル サイズ"
  - "ディスク領域 [SQL Server], テーブル"
  - "領域の割り当て [SQL Server], テーブル サイズ"
  - "データベースの設計 [SQL Server], サイズの見積もり"
  - "1 ページあたりの予約済みの空き行数 [SQL Server]"
  - "テーブル サイズの計算"
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# テーブル サイズの見積もり
  次の手順を実行して、テーブルにデータを格納するために必要な領域を見積もることができます。  
  
1.  「[ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md)」または「[クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)」の説明に従って、ヒープまたはクラスター化インデックスに必要な領域を計算します。  
  
2.  「[非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)」に記載されている手順に従って、非クラスター化インデックスごとに必要な領域を計算します。  
  
3.  手順 1. と手順 2. で計算した値を加算します。  
  
## 参照  
 [データベース サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  