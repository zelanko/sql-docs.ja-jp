---
title: イベントの開始時刻に基づいたイベントのフィルター選択 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41335c0567ca903e1477f4725b2a599de1eaa4a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092552"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>イベントの開始時刻に基づいたイベントのフィルター選択 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース イベントをイベントの開始時刻に基づいてフィルター選択する方法について説明します。  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>イベントの開始時刻に基づいてイベントをフィルター選択するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **[使用するテンプレート]** ボックスの一覧で、トレース テンプレートを選択します。  
  
4.  必要に応じて、トレース結果の保存先を指定します。  
  
5.  **[イベントの選択]** タブで、 **[StartTime]** 列見出しをクリックします。 また、この列見出しを右クリックし、 **[列フィルターの編集]** をクリックして **[フィルターの編集]** ダイアログ ボックスを開く方法もあります。  
  
6.  展開**より大きい**または**未満**、し、入力、`datetime`比較演算子の下に表示されるフィールドの値。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
