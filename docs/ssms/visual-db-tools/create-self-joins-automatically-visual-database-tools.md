---
title: "自己結合の自動作成 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c25ca1aa33e069fdb08d58196d274aa2198ae3af
ms.contentlocale: ja-jp
ms.lasthandoff: 08/18/2017

---
# <a name="create-self-joins-automatically-visual-database-tools"></a>自己結合の自動作成 (Visual Database Tools)
データベースのテーブルに再帰リレーションシップが設定されている場合、テーブルをテーブル自身に自動的に結合できます。  
  
### <a name="to-create-a-self-join-automatically"></a>自己結合を自動作成するには  
  
1.  処理するテーブルを [ダイアグラム ペイン](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) に追加します。  
  
2.  同じテーブルを再度追加します。ダイアグラム ペインに同じテーブルが 2 つ表示されます。  
  
    2 番目のインスタンスには、テーブル名の後に順序番号が付加された別名が、 [クエリおよびビュー デザイナー](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) により割り当てられます。 さらに、2 つの四角形の間に結合線が表示され、テーブルが 2 つの異なる方法でクエリに関連していることを示します。  
  
## <a name="see-also"></a>参照  
[結合を使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  

