---
title: 自己結合の自動作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 7958ed99aa26de79893329d57471ead88ea4519b
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67680246"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>自己結合の自動作成 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
データベースのテーブルに再帰リレーションシップが設定されている場合、テーブルをテーブル自身に自動的に結合できます。  
  
### <a name="to-create-a-self-join-automatically"></a>自己結合を自動作成するには  
  
1.  処理するテーブルを [ダイアグラム ペイン](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) に追加します。  
  
2.  同じテーブルを再度追加します。ダイアグラム ペインに同じテーブルが 2 つ表示されます。  
  
    2 番目のインスタンスには、テーブル名の後に順序番号が付加された別名が、 [クエリおよびビュー デザイナー](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) により割り当てられます。 さらに、2 つの四角形の間に結合線が表示され、テーブルが 2 つの異なる方法でクエリに関連していることを示します。  
  
## <a name="see-also"></a>参照  
[結合を使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
