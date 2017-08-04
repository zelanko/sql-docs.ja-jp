---
title: "トレース (SQL Server Profiler) 内のイベントをフィルター処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 327577ab8656b2af5894c38676c200ea4095edf4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>トレース内のイベントへのフィルターの適用 (SQL Server Profiler)
  フィルターを使用すると、トレースに出力するイベントを制限することができます。 フィルターが設定されていない場合は、選択したイベント クラスのすべてのイベントがトレースに出力されます。 トレースのフィルター設定は必須ではありません。 ただし、フィルターを設定すると、トレース中に発生するオーバーヘッドを低減できます。  
  
 フィルターをトレース定義に追加するには、 **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用します。  
  
### <a name="to-filter-events-in-a-trace"></a>トレース内のイベントにフィルターを適用するには  
  
1.  **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。  
  
     **[イベントの選択]** タブにはグリッド コントロールがあります。 グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。 このテーブルには、各イベント クラスが 1 行で表示されます。 イベント クラスは、接続先のサーバーの種類やバージョンによって多少異なる場合があります。 イベント クラスは、グリッドの **[イベント]**列で識別され、イベント カテゴリ別に分類されています。 残りの列には、各イベント クラスに対応するデータ列が表示されます。  
  
2.  **[列フィルター]**をクリックします。  
  
     **[フィルターの編集]**ダイアログ ボックスが表示されます。 **[フィルターの編集]**ダイアログ ボックスには、トレース内のイベントにフィルターを適用するための比較演算子が一覧表示されます。  
  
3.  フィルターを適用するには、比較演算子をクリックして、フィルターに対して使用する値を入力します。  
  
4.  クリックして **OK**です。  
  
 **注意点 :**  
  
-   [イベントの選択] タブの **[StartTime]** データ列および **[EndTime]** データ列に対してフィルター条件を設定するには、次の操作を実行します。  
  
    -   日付は `YYYY/MM/DD HH:mm:sec`の形式で入力します。  
  
         - または -  
  
    -   **[全般オプション]** ダイアログ ボックスで、 **[日時の値の表示に地域別設定を使用する]** チェック ボックスをオンにします。 表示する、**全般オプション** ダイアログ ボックスで、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **ツール** メニューのをクリックして**オプション**です。  
  
         および  
  
    -   1753 年 1 月 1 日～ 9999 年 12 月 31 日の日付を入力します。  
  
-   **osql** ユーティリティまたは **sqlcmd** ユーティリティからイベントをトレースしている場合は必ず、 **%** を **TextData** データ列のフィルターに付加します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
