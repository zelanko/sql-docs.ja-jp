---
title: "外部結合の作成 (Visual Database Tools) | Microsoft Docs"
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
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b9098896a6389489eac2c2d5adae26e82e863df9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/18/2017

---
# <a name="create-outer-joins-visual-database-tools"></a>外部結合の作成 (Visual Database Tools)
[クエリおよびビュー デザイナー](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) の既定では、テーブル間に内部結合が作成されます。 つまり、内部結合では、他方のテーブルの行と一致しない行は除外されます。 これに対し、外部結合からは、FROM 句で指定された少なくとも 1 つのテーブルまたはビューにあり、任意の WHERE 検索条件または HAVING 検索条件を満たしているすべての行が返されます。 結合テーブルに一致しないデータ行を結果セットに含める場合は、外部結合を作成します。  
  
外部結合を作成するときは、SQL ステートメントでのテーブルの表示順序 (SQL ペインに反映される) が重要です。 最初に追加したテーブルは "左" テーブルに、次に追加したテーブルが "右" テーブルになります。 ([ダイアグラム ペイン](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)に実際に表示されるテーブルの順序は重要ではありません)。左外部結合または右外部結合とは、クエリにテーブルを追加した順序、および [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)の SQL ステートメントでテーブルが表示される順序を示します。  
  
### <a name="to-create-an-outer-join"></a>外部結合を作成するには  
  
1.  結合を自動または手動で作成します。 詳細については、「[テーブルの自動結合 (Visual Database Tools)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)」または「[手動でのテーブルの結合 (Visual Database Tools)](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)」を参照してください。  
  
2.  ダイアグラム ペインで結合線を選択し、**[クエリ デザイナー]** メニューの **[<tablename> からすべての行を選択]** をクリックして、結合する行が含まれるテーブルを結合するコマンドを実行します。  
  
    -   左外部結合を作成するには、最初のテーブルを選択します。  
  
    -   右外部結合を作成するには、2 番目のテーブルを選択します。  
  
    -   完全外部結合を作成するには、両方のテーブルを選択します。  
  
外部結合を指定すると、結合線が外部結合を示す線に変更されます。  
  
さらに、SQL ペインの SQL ステートメントが変更され、次のステートメントのように結合の種類の変更が反映されます。  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
外部結合には不一致行が含まれるため、外部結合を使用すれば、外部キー制約に違反する行を検出することができます。 そのためには、外部結合を作成し、最も右のテーブルの主キー列から NULL の行を検索する検索条件を追加します。 たとえば、次の外部結合は、 `employee` テーブルに対応する行のない `jobs` テーブルの行を検索します。  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a>参照  
[結合を使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
[[結合] ダイアログ ボックス (Visual Database Tools)](../../ssms/visual-db-tools/join-dialog-box-visual-database-tools.md)  
  

