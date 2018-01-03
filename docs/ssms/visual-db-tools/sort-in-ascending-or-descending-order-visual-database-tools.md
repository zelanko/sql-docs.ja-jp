---
title: "昇順または降順の並べ替え (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d9dc0f7b18b198a7c31a658c5f4de90dc12ebb8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a>昇順または降順の並べ替え (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] **ORDER BY** 句で **ASC** または **DESC** キーワードを使用すると、結果セットの 1 つ以上の列を基準に、クエリ結果を昇順または降順に並べ替えることができます。  
  
> [!NOTE]  
> 並べ替え順序を決定する要素として列の照合順序があります。 この照合順序は、 [[照合順序] ダイアログ ボックス](../../ssms/visual-db-tools/collation-dialog-box-visual-database-tools.md)で変更できます。  
  
次の手順は、ORDER BY 句を使用して 1 つ以上の列を並べ替えるクエリを、クエリおよびビュー デザイナーで開いていると想定しています。  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a>結果の並べ替え順序を指定または変更するには  
  
1.  [抽出条件ペイン](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)で、並べ替えを行う列の **[並べ替えの種類]** フィールドをクリックします。  
  
2.  **[昇順]** または **[降順]** を選択して、列の並べ替え順序を指定します。  
  
抽出条件ペインで操作を行うと、最後に行った操作に合わせてクエリの UNION 句が変化します。  
  
> [!NOTE]  
> 複数の列を使用して結果を並べ替えるときは、[並べ替え順序] 列を使用して、列を検索する順序を互いの列を基準にして指定します。 詳細については、「[クエリ内の複数の列の並べ替え (Visual Database Tools)](../../ssms/visual-db-tools/sort-multiple-columns-in-queries-visual-database-tools.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
