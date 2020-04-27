---
title: '[トレースファイルのプロパティ] ([イベントの選択] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0a6c6da76bd89b4686791087e558ae1f329f57a3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088796"
---
# <a name="trace-file-properties-events-selection-tab"></a>[トレース ファイルのプロパティ] ([イベントの選択] タブ)
  **[トレース ファイルのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用すると、トレースの列プロパティを表示したり、トレースからデータ列を削除したりできます。  
  
 このウィンドウを表示するには、トレース ファイルを開きます。 次に、 **[ファイル]** メニューの **[プロパティ]** をクリックした後、 **[イベントの選択]** タブをクリックします。  
  
## <a name="options"></a>オプション  
 **[イベント]** 列  
 イベント カテゴリにより分類された、ビューによりトレースされるイベントです。 最初は、トレースのイベントがすべて選択されています。 イベントのチェック ボックスをオンにするか、データ列をオンにすることでイベントを選択できます。 イベントのチェック ボックスをオンにすると、そのイベントで使用できるデータ列がすべて選択されます。 イベントのデータ列をオンにすると、イベントが選択されるだけでなく、そのほかに必要な列がすべて自動的に選択されます。 トレース ファイルまたはトレース テーブルを表示した場合、イベントのチェック ボックスやデータ列をオフにすることで、トレース ウィンドウに表示されるデータ量が減り、分析が容易になります。 列のフィルターを変更して、トレース ウィンドウに表示されるデータ量を減らすこともできます。 イベント クラスの詳細については、「 [SQL Server イベント クラスの参照](../relational-databases/event-classes/sql-server-event-class-reference.md)」を参照してください。  
  
 データ列  
 トレースされるデータ列を表示します。 トレースに含まれる各イベントでは、トレースの関連するデータ列は既定ですべてオンになっています。  
  
 フィルターを指定するには、データ列のヘッダーをクリックし、フィルター基準を入力します。 フィルター選択されるデータ列については、 **[フィルターの編集]** ダイアログ ボックスの列ラベルの左側にフィルターのアイコンが表示されます。  
  
 **[すべてのイベントを表示する]**  
 表示できるイベントをすべて表示します。 既定では、 **[イベントの選択]** グリッドで選択されている行だけが表示されます。 このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないイベントがすべて非表示になります。 **[すべてのイベントを表示する]** がオンで、トレース ファイルまたはトレース テーブルを表示している場合、トレースに記録されたすべてのイベントがトレース ウィンドウに表示されます。  
  
 **[すべての列を表示]**  
 表示できるデータ列をすべて表示します。 既定では、選択されているデータ列だけが表示されます。 このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないデータ列がすべて非表示になります。  
  
 **列フィルター**  
 [ **フィルターの編集** ] ダイアログ ボックスを起動します。フィルター選択されるデータ列の列ラベルの左側には、フィルターのアイコンが表示されます。 **[フィルターの編集]** ダイアログ ボックスを使用して、データ列のフィルターを編集します。  
  
 **[列の構成]**  
 **[イベント]** およびトレースするデータ列を選択した後、 **[列の構成]** をクリックすると、トレース結果のウィンドウの列が並べ替えられます。  
  
## <a name="see-also"></a>参照  
 [トレースファイルのイベントとデータ列を指定する &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [トレース &#40;SQL Server プロファイラーのイベントをフィルター処理し&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [フィルター情報の表示 &#40;SQL Server プロファイラー&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [フィルター &#40;SQL Server プロファイラーの変更&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [SQL Server プロファイラー](../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
