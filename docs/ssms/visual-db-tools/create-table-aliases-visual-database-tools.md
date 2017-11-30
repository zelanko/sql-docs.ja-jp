---
title: "テーブルの別名の作成 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e7c4230e0e72e3de7a636e822a6f89b94b379fb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-table-aliases-visual-database-tools"></a>テーブルの別名の作成 (Visual Database Tools)
別名を使用すると、テーブル名を使った操作が容易になります。 別名は、次の場合に使用すると便利です。  
  
-   [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) のステートメントを短くして、読みやすくする場合。  
  
-   クエリでテーブル名を列名の修飾などに頻繁に参照する場合で、クエリの文字数を一定文字数にする場合。 一部のデータベースでは、クエリの最大文字数が決まっています。  
  
-   自己結合などで同一テーブルの複数のインスタンスを使用し、いずれかのインスタンスを参照する方法が必要な場合。  
  
たとえば、テーブル名 `employee_information` に対して別名 `"e"` を作成すると、クエリの残りの部分でテーブルを `"e"` として参照できます。  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>テーブルまたはテーブル値オブジェクトの別名を作成するには  
  
1.  クエリにテーブルまたはテーブル値オブジェクトを追加します。  
  
2.  **ダイアグラム ペイン**で、別名を作成するオブジェクトを右クリックし、ショートカット メニューの **[プロパティ]** をクリックします。  
  
3.  **[プロパティ]** ウィンドウの **[エイリアス]** フィールドに別名を入力します。  
  
## <a name="see-also"></a>参照  
[クエリへのテーブルの追加 (Visual Database Tools)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
