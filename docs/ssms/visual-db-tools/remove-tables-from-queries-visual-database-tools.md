---
title: クエリからのテーブルの削除
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 32c25c3ded07e84e436b69af5baac5634909998c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75255248"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>クエリからのテーブルの削除 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
クエリからテーブルまたはテーブル値オブジェクトを削除できます。  
  
> [!NOTE]  
> テーブルまたはテーブル値オブジェクトを削除しても、現在のクエリから削除されるだけです。データベースからは何も削除されません。 データベースからテーブルを削除する方法の詳細については、データベースからテーブルを削除する方法(https://msdn.microsoft.com/ca6aa3e9-9885-44c3-bafc-aec441fd97ec) に関するぺージを参照してください。  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>テーブルまたはテーブル構造オブジェクトを削除するには  
  
-   **ダイアグラム ペイン**で、テーブル、ビュー、ユーザー定義関数、シノニム、またはクエリを選択し、Del キーを押すか、オブジェクトを右クリックして、表示されるダイアログ ボックスの **[削除]** をクリックします。 同時に複数のオブジェクトを選択して削除することもできます。  
  
    または  
  
-   **SQL ペイン**でオブジェクトへのすべての参照を削除します。  
  
テーブルまたはテーブル値オブジェクトを削除すると、クエリおよびビュー デザイナーでは、そのテーブルまたはテーブル値オブジェクトを含む結合が自動的に削除され、これらのオブジェクトの列に対する参照も **SQL ペイン** および **抽出条件ペイン**から自動的に削除されます。 ただし、オブジェクトを含む複合式がクエリに含まれる場合、オブジェクトに対する参照がすべて削除されるまで、オブジェクトが自動的に削除されることはありません。  
  
## <a name="see-also"></a>参照  
[クエリにテーブルを追加する](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[テーブルの別名の作成](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[検索条件を指定する](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[クエリ結果の集計](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリに関する基本操作の実行](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
