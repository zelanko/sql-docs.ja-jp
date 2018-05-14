---
title: レッスン 1:テーブルの階層構造への変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a38cbcec7f42ff99e0e7c56de16fc30a3187dded
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>レッスン 1:テーブルの階層構造への変換
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
階層リレーションシップを表すために自己結合を使っているテーブルがある場合、このレッスンの説明に従って、それらのテーブルを階層構造に変換できます。 現在の表示から、 **hierarchyid**を使用した表示に移行するのは比較的簡単です。 移行後は、コンパクトで理解しやすい階層表示が可能になるため、ユーザーはさまざまな方法でインデックスを作成して効率的なクエリを実現できます。  
  
このレッスンでは、既存のテーブルを検証した後、 **hierarchyid** 列を含む新しいテーブルを作成し、そのテーブルにソース テーブルのデータを取り込みます。さらに、3 とおりのインデックス作成方法を紹介します。 このレッスンの内容は次のとおりです。  
  
-   [Employee テーブルの現在の構造の確認](../../relational-databases/tables/lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [既存の階層データを使用したテーブルの設定](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [NewOrg テーブルの最適化](../../relational-databases/tables/lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [まとめ : テーブルの階層構造への変換](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Prerequisites  
このレッスンを学習するには、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースが必要です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[Employee テーブルの現在の構造の確認](../../relational-databases/tables/lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2: 階層テーブルでのデータの作成と管理](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
