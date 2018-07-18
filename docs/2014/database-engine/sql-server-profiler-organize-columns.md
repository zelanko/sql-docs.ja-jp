---
title: SQL Server Profiler - 列の構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
caps.latest.revision: 8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1bfa74b1d6f8eb7f3c13c294aba37bfb88f7e995
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162913"
---
# <a name="sql-server-profiler---organize-columns"></a>[SQL Server Profiler] - [列の構成]
  大きなトレース ファイルまたはトレース テーブルの表示や分析を簡単に行えるように、トレースに表示されるイベントをグループ化または集計する場合は、 **[列の構成]** ダイアログ ボックスを使用してデータ列を選択します。  
  
 集計を実行すると、トレース内のすべてのイベントはそれぞれのイベント クラスの種類の下に移動され、折りたたまれます。 イベント クラス名の左側にプラス記号 (**[+]**) が表示されます。 プラス記号をクリックしてイベント クラスを展開すると、その種類のイベントがすべて表示されます。  
  
 グループ化を実行すると、特定の種類のすべてのイベント クラスがトレース ウィンドウ表示にまとめて構成されます。 ただし、イベントはイベント クラスの種類の下に折りたたまれません。  
  
 トレース ウィンドウ表示内でイベントのグループ化または集計を行うときに、選択されている列は表示ウィンドウ内で固定された状態のままですが、左右にスクロールして他のデータ列をすべて見ることができます。  
  
 このダイアログ ボックスを表示するには、既存のトレース ファイルまたはトレース テーブルを開き、 **の** [ファイル] [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **[プロパティ]** をクリックします。 **[トレースのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックし、次に **[列の構成]** をクリックします。 新しいトレースを作成する場合も、 **[イベントの選択]** タブの **[列の構成]** をクリックします。  
  
## <a name="options"></a>および  
 **グループ**  
 **[グループ]** でデータ列名を移動することにより、トレース ウィンドウでイベント クラスのグループ化または集計を実行できます。  
  
 イベントを集計するには、1 つのデータ列を **[グループ]** に移動します。 これにより、特定の種類のすべてのイベントが、トレース ウィンドウ表示のイベント クラスの種類名の下に折りたたまれます。 イベント クラス名の左側にプラス記号 (**[+]**) が表示されます。 このプラス記号をクリックすると、イベント クラスの種類が展開され、すべてのイベントが表示されます。 集計とグループ化のオンとオフを設定するには、 **[表示]** メニューの **[集計ビュー]** または **[グループ化ビュー]** をクリックします。  
  
 イベントをグループ化するには、複数のデータ列を **[グループ]** に移動します。 これにより、トレース ウィンドウ表示で特定の種類のすべてのイベントがグループ化されますが、イベントは各イベント クラスの種類名の下には折りたたまれません。 グループ化ビューとグループ化されていないビューを切り替えるには、[表示] メニューの **[グループ化ビュー]** をクリックします。 複数のデータ列を **[グループ]** に移動した場合、 **[集計ビュー]** に切り替えることはできません。  
  
 **[列]**  
 **[グループ]** への移動に使用できるデータ列の一覧です。 **[列]** の左にあるプラス記号 (**[+]**) をクリックすると、一覧が展開されます。  
  
 **[上へ]**  
 データ列を選択した後で、 **[上へ]** をクリックすると、データ列を上に移動して **[グループ]** に入れることができます。 また、 **[上へ]** をクリックして、トレース ウィンドウ表示内の列の表示を再構成することもできます。  
  
 **[下へ]**  
 データ列を選択した後で、 **[下へ]** をクリックすると、データ列を下に移動して **[グループ]** から除外することができます。 また、 **[下へ]** をクリックして、トレース ウィンドウ表示内の列の表示を再構成することもできます。  
  
## <a name="see-also"></a>参照  
 [トレースに表示される列を整理&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [トレースを作成する&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [トレース テンプレートを作成&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)   
 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  
