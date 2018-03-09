---
title: "クエリでの TOP 句の指定 (Visual Database Tools) | Microsoft Docs"
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
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25864b7e96a36e38e1ec31cdee4e902e75033da9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>クエリでの TOP 句の指定 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] TOP 句は、クエリから最初の *n* 行または *n %* 行だけを返します。 TOP 句は、すべてのクエリ結果を返すために必要なリソースを使用する前に、結果の一部を検査して、必要なクエリが実行されるかどうかを確認する場合に便利です。  
  
### <a name="to-specify-the-top-clause-in-queries"></a>クエリで TOP 句を指定するには  
  
1.  ソリューション エクスプローラーでクエリを開くか、新しいクエリを作成します。  
  
2.  **[表示]** メニューの **[プロパティ ウィンドウ]**をクリックします。  
  
3.  **[プロパティ ウィンドウ]**で、 **[Top の指定]** プロパティを検索して展開します。  
  
4.  **[(Top)]** 子プロパティをクリックして、 **[はい]**に設定します。  
  
5.  **[式]** 子プロパティで、数値の結果を返す式を入力します ("10"、"2*5" など)。  
  
6.  **[PERCENT]** 子プロパティをクリックして、 **[式]** プロパティを、返されるすべての行のパーセントとして処理するか (はい)、返される行の絶対数として処理するか (いいえ) を指定します。  
  
7.  クエリで ORDER BY 句が使用される場合は、 **[WITH TIES 使用]** 子プロパティをクリックして、グループの一部だけが含まれる場合にグループ内のすべての行を表示するときは **[はい]** 、行を切り捨てるときは **[いいえ]** を選択します。  
  
上記の手順を実行していくと、TOP 句が SQL ペインに表示され、プロパティの現在の設定を反映するように変更されます。  
  
> [!NOTE]  
> SQL ペインで TOP 句を編集することで、 **[Top の指定]** の子プロパティの値を変更することもできます。  
  
## <a name="see-also"></a>参照  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[クエリのプロパティ (Visual Database Tools)](../../ssms/visual-db-tools/query-properties-visual-database-tools.md)  
  
