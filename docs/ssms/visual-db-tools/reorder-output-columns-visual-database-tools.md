---
title: 列の出力順の変更
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: f168b16ef5407b8ebf47e55f7062b1b7c8c7b180
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008869"
---
# <a name="reorder-output-columns-visual-database-tools"></a>列の出力順の変更 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
選択クエリにデータ列を追加する順序によって、結果での列の表示順序が決まります。 最初にクエリに追加した列は結果の左端に表示され、次に追加した列はその右隣に表示されます。  
  
また、更新クエリや挿入クエリを作成する場合、追加した列の順序は、データの処理順序に反映されます。  
  
そのため、データ列を並べ替えると、結果セットの列が表示される順序や処理される順序を変更できます。  
  
### <a name="to-reorder-columns-for-output"></a>列の出力順を変更するには  
  
1.  [抽出条件ペイン](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)で、対象の列を含む行の左側にある行セレクター ボタンをクリックして、行を選択します。  
  
2.  行セレクター ボタンにポインターを置き、行を新しい場所にドラッグします。  
  
    または  
  
    [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)で列名の順序を編集します。  
  
> [!TIP]  
> 抽出条件ペインの特定の場所にデータ行を追加するには、抽出条件ペインの該当する場所に空白行を挿入し、その行に挿入するデータ列を指定します。 詳しくは、「[クエリに列を追加する方法 (Visual Database Tools)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
