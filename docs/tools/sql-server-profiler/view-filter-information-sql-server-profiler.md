---
title: "フィルター情報の表示 (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フィルター情報の表示"
  - "フィルター [SQL Server]、表示"
  - "トレースのフィルター [SQL Server]"
  - "トレース [SQL Server]、フィルター"
  - "フィルター情報の確認"
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# フィルター情報の表示 (SQL Server Profiler)
  このトピックでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してイベント クラスのデータ列のフィルターを表示する方法について説明します。  
  
### フィルター情報を表示するには  
  
1.  トレース ファイル、トレース テーブル、または SQL スクリプトを開き、**[ファイル]** メニューの **[プロパティ]** をクリックします。 トレース テンプレートを編集している場合、または新しいトレースを作成している場合、この手順は省略します。  
  
2.  **[イベントの選択]** タブで、フィルターを表示するデータ列の名前を右クリックし、**[列フィルターの編集]** をクリックします。  
  
3.  **[フィルターの編集]** ダイアログ ボックスでフィルターの比較演算子を展開し、指定の条件に割り当てられている値を確認します。 フィルター情報を表示するすべての列に対し、手順 2. と 3. を繰り返します。  
  
> [!NOTE]  
>  値が割り当てられている比較演算子は太字で表示されます。  
  
## 参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  