---
title: トレース (SQL Server Profiler) 内のイベントをフィルター処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6d6716cfcdf8bd6ce495f8aefe0e0df34fddb1c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>トレース内のイベントへのフィルターの適用 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] フィルターを使用すると、トレースに出力するイベントを制限することができます。 フィルターが設定されていない場合は、選択したイベント クラスのすべてのイベントがトレースに出力されます。 トレースのフィルター設定は必須ではありません。 ただし、フィルターを設定すると、トレース中に発生するオーバーヘッドを低減できます。  
  
 フィルターをトレース定義に追加するには、 **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用します。  
  
### <a name="to-filter-events-in-a-trace"></a>トレース内のイベントにフィルターを適用するには  
  
1.  **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。  
  
     **[イベントの選択]** タブにはグリッド コントロールがあります。 グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。 このテーブルには、各イベント クラスが 1 行で表示されます。 イベント クラスは、接続先のサーバーの種類やバージョンによって多少異なる場合があります。 イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別に分類されています。 残りの列には、各イベント クラスに対応するデータ列が表示されます。  
  
2.  **[列フィルター]** をクリックします。  
  
     **[フィルターの編集]** ダイアログ ボックスが表示されます。 **[フィルターの編集]** ダイアログ ボックスには、トレース内のイベントにフィルターを適用するための比較演算子が一覧表示されます。  
  
3.  フィルターを適用するには、比較演算子をクリックして、フィルターに対して使用する値を入力します。  
  
4.  **[OK]** をクリックします。  
  
 **注意点 :**  
  
-   [イベントの選択] タブの **[StartTime]** データ列および **[EndTime]** データ列に対してフィルター条件を設定するには、次の操作を実行します。  
  
    -   日付は `YYYY/MM/DD HH:mm:sec`の形式で入力します。  
  
         -または-  
  
    -   **[全般オプション]** ダイアログ ボックスで、 **[日時の値の表示に地域別設定を使用する]** チェック ボックスをオンにします。 **[全般オプション]** ダイアログ ボックスを表示するには、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で **[ツール]** メニューの **[オプション]** をクリックします。  
  
         および  
  
    -   1753 年 1 月 1 日～ 9999 年 12 月 31 日の日付を入力します。  
  
-   **osql** ユーティリティまたは **sqlcmd** ユーティリティからイベントをトレースしている場合は必ず、 **%** を **TextData** データ列のフィルターに付加します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
