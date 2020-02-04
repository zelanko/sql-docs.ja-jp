---
title: クエリの作成
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: f3b3719ae80dca63f8755e3c2a57179e219e1414
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254291"
---
# <a name="create-queries-visual-database-tools"></a>クエリの作成 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
クエリを使用すると、データベース内のテーブルおよびビューからデータを取得できます。 クエリの作成と処理には、 **クエリおよびビュー デザイナー**を使用します。クエリおよびビュー デザイナーは、 [ダイアグラム ペイン](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)、 [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)、 [抽出条件ペイン](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)、および [結果ペイン](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)の 4 つのペインで構成されています。  
  
### <a name="to-create-a-new-query"></a>新しいクエリを作成するには  
  
1.  **オブジェクト エクスプローラー**で、問い合わせるデータベースの **[テーブル]** ノードを展開し、 問い合わせるテーブルを右クリックして、 **[テーブルを開く]** をクリックします。  
  
2.  クエリにテーブルを追加するには、[クエリ デザイナー] メニューの **[テーブルの追加]** をクリックします。  
  
    > [!NOTE]  
    > **ダイアグラム**ペイン、 **SQL**ペイン、 **抽出条件**ペイン、または **結果ペイン** が表示されない場合は、[クエリ デザイナー] メニューの **[ペイン]** をポイントして、開くペインをクリックします。  
  
3.  **[テーブルの追加]** ダイアログ ボックスで、問い合わせるテーブルを選択し、テーブルごとに **[追加]** をクリックします。  
  
4.  問い合わせるすべてのテーブルを追加したら、 **[閉じる]** をクリックします。  
  
    後でテーブルを追加するには、 **ダイアグラム** ペインの空の領域を右クリックし、ショートカット メニューの **[テーブルの追加]** をクリックします。  
  
5.  **ダイアグラム ペイン**で、問い合わせる各列のテーブル値オブジェクトのボックスをオンにします。  
  
6.  [クエリ デザイナー] メニューの **[SQL の実行]** をクリックして、クエリを実行します。  
  
より的確な結果を得るために、 **SQL ペイン** で SQL コードを変更するか、 **抽出条件ペイン**で並べ替え順序や列の別名などのオプションを選択することもできます。  
  
## <a name="see-also"></a>参照  
[クエリの保存 (Visual Database Tools)](../../ssms/visual-db-tools/save-queries-visual-database-tools.md)  
[クエリの種類 (Visual Database Tools)](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
[検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
