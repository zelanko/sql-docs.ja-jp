---
title: サポートされるクエリの種類 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db00234849e885c82898a379bd3546e193a1a634
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176743"
---
# <a name="supported-query-types-visual-database-tools"></a>サポートされるクエリの種類 (Visual Database Tools)
  [クエリおよびビュー デザイナー](visual-database-tools.md)のダイアグラム ペインと抽出条件ペイン (グラフィカルなペイン) では、次のクエリを作成できます。  
  
-   **選択クエリ** 1 つ以上のテーブルまたはビューからデータを取得します。 このクエリは、SQL の SELECT ステートメントを作成します。  
  
-   **結果の挿入クエリ** あるテーブルの既存の行を別のテーブルにコピーして、新しい行を作成します。または、同じテーブルに行をコピーして新しい行を作成します。 このクエリは、SQL の INSERT INTO...SELECT ステートメントを作成します。  
  
-   **値の挿入クエリ** 新しい行を作成し、指定された列に値を挿入します。 このクエリは、SQL の INSERT INTO...VALUES ステートメントを作成します。  
  
-   **更新クエリ** テーブル内の 1 つ以上の既存の行にある特定の列の値を変更します。 このクエリは、SQL の UPDATE...SET ステートメントを作成します。  
  
-   **削除クエリ** テーブルから 1 つ以上の行を削除します。 このクエリは、SQL の DELETE ステートメントを作成します。  
  
    > [!NOTE]  
    >  削除クエリは、テーブルから行全体を削除します。 特定のデータ列から値を削除する場合は、更新クエリを使用します。  
  
-   **テーブルの作成クエリ** 新しいテーブルを作成し、クエリの結果をコピーしてテーブル内に行を作成します。 このクエリは、SQL の SELECT...INTO ステートメントを作成します。  
  
 クエリを作成するには、グラフィカルなペインを使用する方法だけでなく、UNION クエリなど、任意の SQL ステートメントを SQL ペインに入力して作成する方法があります。  
  
 グラフィカルなペインで表示できない SQL ステートメントを使用してクエリを作成すると、グラフィカルなペインは淡色表示になります。これは、これらのペインに作成中のクエリが反映されていないことを示します。 ただし、これらのペインは淡色表示されていてもアクティブ状態なので、多くの場合、ペインに表示されているクエリを変更できます。 変更の結果、グラフィカルなペインで表示できるクエリになった場合、ペインの淡色表示は解除されます。  
  
## <a name="see-also"></a>参照  
 [クエリおよびビューの操作方法に関するトピックをデザイン&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [クエリの種類 (Visual Database Tools)](types-of-queries-visual-database-tools.md)  
  
  