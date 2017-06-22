---
title: "データベース サイズの見積もり | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d2d986d7e899e630429f431f040addb9076f081a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="estimate-the-size-of-a-database"></a>データベース サイズの見積もり
  データベースをデザインするときは、データを格納したときにデータベースのサイズがどのくらい大きくなるかを見積もる必要性が生じる場合があります。 データベースのサイズを見積もると、次の目的に必要なハードウェア構成の決定に役立ちます。  
  
-   アプリケーションが必要とするパフォーマンスの実現。  
  
-   データとインデックスの格納に必要となる適切な量の物理ディスク領域の確保。  
  
 データベースのサイズを見積もると、データベースのデザインを改良する必要があるかどうかを判断する場合にも役立ちます。 たとえば、見積もったデータベースのサイズが大きすぎて組織内で実装できず、正規化の必要性があるとわかる場合があります。 逆に、見積もったサイズが予想より小さい場合もあります。 この場合は、データベースを非正規化してクエリのパフォーマンスを向上させることができます。  
  
 データベースのサイズを見積もるには、各テーブルのサイズを個別に見積もり、それぞれの値を合計します。 テーブルのサイズは、テーブルにインデックスが含まれているかどうかにより異なり、インデックスが含まれている場合はそのインデックスの種類によって異なります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[テーブル サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-table.md)|テーブルおよび関連付けられたインデックスにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。|  
|[ヒープ サイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-heap.md)|ヒープにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。 ヒープとは、クラスター化インデックスを含まないテーブルのことです。|  
|[クラスター化インデックスのサイズの見積もり](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)|クラスター化インデックスにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。|  
|[非クラスター化インデックスのサイズの算出](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)|非クラスター化インデックスにデータを格納するために必要な領域を見積もる手順や計算方法について説明します。|  
  
  
