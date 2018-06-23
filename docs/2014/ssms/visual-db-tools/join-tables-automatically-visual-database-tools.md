---
title: テーブルの自動結合 (Visual Database Tools) | Microsoft Docs
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
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 373264e421362d29ee00909707abc2be41ce1956
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176074"
---
# <a name="join-tables-automatically-visual-database-tools"></a>テーブルの自動結合 (Visual Database Tools)
  クエリに複数のテーブルを追加すると、 [クエリおよびビュー デザイナー](visual-database-tools.md) により、これらのテーブルが相互に関連しているかどうかの確認が行われます。 関連している場合は、テーブルまたはテーブル構造オブジェクトを示す四角形の間に、結合線が自動的に表示されます。  
  
 クエリおよびビュー デザイナーでは、次の場合にテーブルの結合が認識されます。  
  
-   データベースにテーブルの関連を指定する情報がある場合。  
  
-   各テーブルの 1 つの列が、それぞれ同じ名前および同じデータ型を持っている場合。 少なくとも一方のテーブルの列は、主キーである必要があります。 たとえば、 `employee` テーブルおよび `jobs` テーブルを追加し、 `job_id` テーブルに `jobs` 列という主キーがあり、それぞれのテーブルに同じデータ型の `job_id` という列がある場合、これらのテーブルは自動的に結合されます。  
  
    > [!NOTE]  
    >  クエリおよびビュー デザイナーでは、同じ名前および同じデータ型の列の間で結合が 1 つだけ作成されます。 複数の結合が作成できる場合でも、クエリおよびビュー デザイナーは、最初に検出された一致列から結合を 1 つだけ作成します。  
  
-   検索条件 (WHERE 句) が、実際には結合条件であると検出された場合。 たとえば、 `employee` テーブルおよび `jobs`テーブルを追加し、両方のテーブルの `job_id` 列の値が一致する行を検索する検索条件を作成する場合があります。 その場合、検索条件が結合になることが検出され、検索条件に基づいて結合条件が作成されます。  
  
 クエリおよびビュー デザイナーによって作成された結合がクエリに適していない場合、結合の変更または削除を行うことができます。 詳しくは、「[結合演算子の変更 (Visual Database Tools)](modify-join-operators-visual-database-tools.md)」および「[結合の削除 (Visual Database Tools)](remove-joins-visual-database-tools.md)」をご覧ください。  
  
 クエリでテーブルが自動的に結合されない場合は、結合を手動で作成できます。 詳しくは、「[手動でのテーブルの結合 (Visual Database Tools)](join-tables-manually-visual-database-tools.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [クエリおよびビュー デザイナーでの結合の表現方法&#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)   
 [クエリおよびビューの操作方法に関するトピックをデザイン&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [結合を使用したクエリ (Visual Database Tools)](query-with-joins-visual-database-tools.md)  
  
  