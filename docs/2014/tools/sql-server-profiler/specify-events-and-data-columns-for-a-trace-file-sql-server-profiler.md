---
title: トレース ファイルに含めるイベントとデータ列の指定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: daef2308b3a97ddd0fe799eb81dcacf74fa78383
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275678"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a>トレース ファイルに含めるイベントとデータ列の指定 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してトレースに含めるイベント クラスとデータ列を指定する方法について説明します。  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a>トレースに含めるイベントとデータ列を指定するには  
  
1.  **[トレースのプロパティ]** または **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。  
  
     **[イベントの選択]** タブにはグリッド コントロールがあります。 グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。 このテーブルには、各イベント クラスが 1 行で表示されます。 表示されるイベント クラスは、接続しているサーバーの種類とバージョンによって多少異なります。 イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別に分類されています。 残りの列には、各イベント クラスに対応するデータ列が表示されます。  
  
2.  **[イベントの選択]** タブで、グリッド コントロールを使用して、トレース ファイルに対するイベントとデータ列の追加または削除を行います。  
  
3.  トレースからイベントを削除するには、各イベント クラスの **[Events]** 列のチェック ボックスをオフにします。  
  
4.  トレースにイベントを含めるには、各イベント クラスの **[Events]** 列のチェック ボックスをオンにするか、イベントに対応するデータ列のチェック ボックスをオンにします。  
  
> [!IMPORTANT]  
>  このトレースをシステム モニターやパフォーマンス モニターのデータと関連付ける場合は、 **Start Time** データ列と **End Time** データ列の両方をトレースに含める必要があります。  
  
 イベント クラスを含める場合、イベントに対応するイベント クラスのチェック ボックスをオンにしていると、関連するデータ列もすべてトレースに含まれます。 特定の列のチェック ボックスをオンにしている場合は、その列だけがトレースに含まれます。  
  
1.  イベント クラスからデータ列を削除するには、イベント クラス行のデータ列のチェック ボックスをオフにするか、列ヘッダーを右クリックして、 **[列の選択解除]** をクリックします。  
  
2.  必要に応じて、トレースにフィルターを適用します。 詳細については、「[トレース内のイベントへのフィルターの適用 &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
