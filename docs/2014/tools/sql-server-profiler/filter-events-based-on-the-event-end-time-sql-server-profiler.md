---
title: イベントの終了時刻に基づいたフィルターでのイベントの選択 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7ccb13828235b690bad83e3791b945d8584d5e1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054391"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>イベントの終了時刻に基づいたフィルターでのイベントの選択 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、イベントの終了時刻に基づいてフィルターでトレース イベントを選択する方法について説明します。  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>イベントの終了時刻に基づいてフィルターでイベントを選択するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレースのプロパティ]** ダイアログ ボックスで、 **[全般]** タブをクリックして、 **[トレース名]** ボックスに名前を入力します。  
  
3.  **[使用するテンプレート]** の一覧からトレース テンプレートを選択します。  
  
4.  必要に応じて、トレース結果の保存先ファイルまたは保存先テーブルを指定します。  
  
5.  **[イベントの選択]** タブで、 **[EndTime]** データ列をクリックして **[フィルターの編集]** ダイアログ ボックスを表示します。 このダイアログ ボックスは、列見出しを右クリックして **[列フィルターの編集]** をクリックしても表示することができます。  
  
6.  [より**大きい**] または [**より小さい**] を展開し、 `datetime` 比較演算子の下に表示されるフィールドに値を入力します。  
  
## <a name="see-also"></a>参照  
 [[SQL Server Profiler]](sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
