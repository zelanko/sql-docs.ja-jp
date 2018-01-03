---
title: "クエリ結果の要約 (Visual Database Tools) | Microsoft Docs"
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
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23be6f5ada4c862e4f55d71d3023a8e0c56fdb7a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="summarize-query-results-visual-database-tools"></a>クエリ結果の要約 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] 集計クエリを作成するときには、一定の論理原則が適用されます。 たとえば、サマリ クエリでは個別の行の内容は表示できません。 クエリおよびビュー デザイナーでは、 [ダイアグラム ペイン](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) および [抽出条件ペイン](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md) を使用してこのような原則に従い、作業を行うことができます。  
  
集計クエリの原則やクエリおよびビュー デザイナーの動作を理解することによって、論理的に正しい集計クエリを作成できます。 最優先される原則は、集計クエリで作成できるのは集計情報だけであるということです。 したがって、次に示す原則のほとんどは、集計クエリ内で個別のデータ列を参照する方法を示したものです。  
  
## <a name="in-this-section"></a>このセクションの内容  
[集計クエリにおける列の使用 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-columns-in-aggregate-queries-visual-database-tools.md)  
GROUP BY 句、WHERE 句、および HAVING 句を使用して、列のグループ化と集計に関する概念を説明します。  
  
[テーブルの行数のカウント (Visual Database Tools)](../../ssms/visual-db-tools/count-rows-in-a-table-visual-database-tools.md)  
テーブル内の行数、または一連の基準を満たすテーブル内の行数をカウントする手順を説明します。  
  
[テーブルにあるすべての行の値の要約または集計 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
グループ化された一連の行ではなく、すべての行を集計する手順を説明します。  
  
[カスタム式を使用して値を要約または集計する (Visual Database Tools)](../../ssms/visual-db-tools/summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
定義済みの句を使用するのではなく、集計または集約用の式を使用する手順を説明します。  
  
## <a name="related-sections"></a>関連項目  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
クエリおよびビュー デザイナーの使用方法を説明するトピックへのリンクが用意されています。  
  
