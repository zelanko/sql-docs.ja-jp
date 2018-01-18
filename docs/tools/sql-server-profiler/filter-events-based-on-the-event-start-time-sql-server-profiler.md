---
title: "イベントの開始時刻 (SQL Server Profiler) に基づいてイベントをフィルター処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfd8b7593b4e43613483a6ce91cf279ade6b91bc
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>イベントの開始時刻に基づいたイベントのフィルター選択 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックを使用して、イベントの開始時刻に基づいたイベントのトレースをフィルター処理する方法について説明[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>イベントの開始時刻に基づいてイベントをフィルター選択するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]**をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。  
  
     **[トレースのプロパティ]**ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]**チェック ボックスがオンになっている場合、 **[トレースのプロパティ]**ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、 **[ツール]**メニューの **[オプション]**をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **[使用するテンプレート]**ボックスの一覧で、トレース テンプレートを選択します。  
  
4.  必要に応じて、トレース結果の保存先を指定します。  
  
5.  **[イベントの選択]**タブで、 **[StartTime]** 列見出しをクリックします。 また、この列見出しを右クリックし、 **[列フィルターの編集]** をクリックして **[フィルターの編集]** ダイアログ ボックスを開く方法もあります。  
  
6.  **[次の値より大きい]** または **[次の値より小さい]**を展開して、その下に表示されるフィールドに **datetime** 値を入力します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
