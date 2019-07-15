---
title: トレース (SQL Server Profiler) 内のイベントをフィルター処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: afdbe68aa8da7fbc6a6aa812d5e89b7ed089c158
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729946"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>トレース内のイベントへのフィルターの適用 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  フィルターを使用すると、トレースに出力するイベントを制限することができます。 フィルターが設定されていない場合は、選択したイベント クラスのすべてのイベントがトレースに出力されます。 トレースのフィルター設定は必須ではありません。 ただし、フィルターを設定すると、トレース中に発生するオーバーヘッドを低減できます。  
  
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
  
  
