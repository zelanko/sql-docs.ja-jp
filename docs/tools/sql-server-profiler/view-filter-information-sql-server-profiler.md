---
title: "フィルター情報 (SQL Server Profiler) を表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: "23"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04c9af7d7f050918c00af72165478a59aa76e0f9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="view-filter-information-sql-server-profiler"></a>フィルター情報の表示 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックを使用してイベント クラスのデータ列にフィルターを表示する方法について説明[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。  
  
### <a name="to-view-filter-information"></a>フィルター情報を表示するには  
  
1.  トレース ファイル、トレース テーブル、または SQL スクリプトを開き、 **[ファイル]** メニューの **[プロパティ]**をクリックします。 トレース テンプレートを編集している場合、または新しいトレースを作成している場合、この手順は省略します。  
  
2.  **[イベントの選択]** タブで、フィルターを表示するデータ列の名前を右クリックし、 **[列フィルターの編集]**をクリックします。  
  
3.  **[フィルターの編集]** ダイアログ ボックスでフィルターの比較演算子を展開し、指定の条件に割り当てられている値を確認します。 フィルター情報を表示するすべての列に対し、手順 2. と 3. を繰り返します。  
  
> [!NOTE]  
>  値が割り当てられている比較演算子は太字で表示されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
