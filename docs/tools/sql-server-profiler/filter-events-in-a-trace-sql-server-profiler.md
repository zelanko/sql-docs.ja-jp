---
title: トレース内のイベントにフィルターを適用する
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 66780fe3a71f784679e80779985740a3d9069777
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307236"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>トレース内のイベントへのフィルターの適用 (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

フィルターを使用すると、トレースに出力するイベントを制限することができます。 フィルターが設定されていない場合は、選択したイベント クラスのすべてのイベントがトレースに出力されます。 トレースのフィルター設定は必須ではありません。 ただし、フィルターを設定すると、トレース中に発生するオーバーヘッドを低減できます。  
  
 フィルターをトレース定義に追加するには、 **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用します。  
  
### <a name="to-filter-events-in-a-trace"></a>トレース内のイベントにフィルターを適用するには  
  
1.  **[トレースのプロパティ]** ダイアログ ボックスまたは **[トレース テンプレートのプロパティ]** ダイアログ ボックスで、 **[イベントの選択]** タブをクリックします。  
  
     **[イベントの選択]** タブにはグリッド コントロールがあります。 グリッド コントロールは、トレース可能な各イベント クラスを含んでいるテーブルです。 このテーブルには、各イベント クラスが 1 行で表示されます。 イベント クラスは、接続先のサーバーの種類やバージョンによって多少異なる場合があります。 イベント クラスは、グリッドの **[イベント]** 列で識別され、イベント カテゴリ別にグループ化されます。 残りの列には、各イベント クラスに対応するデータ列が表示されます。  
  
2.  **[列フィルター]** をクリックします。  
  
     **[フィルターの編集]** ダイアログ ボックスが表示されます。 **[フィルターの編集]** ダイアログ ボックスには、トレース内のイベントをフィルター処理するために使用できる比較演算子の一覧が表示されます。  
  
3.  フィルターを適用するには、比較演算子をクリックして、フィルターに対して使用する値を入力します。  
  
4.  **[OK]** をクリックします。  
  
 **考慮事項:**  
  
-   [イベントの選択] タブの **[StartTime]** データ列および **[EndTime]** データ列に対してフィルター条件を設定するには、次の操作を実行します。  
  
    -   日付は `YYYY/MM/DD HH:mm:sec`の形式で入力します。  
  
         \- または -  
  
    -   **[全般オプション]** ダイアログ ボックスで、 **[日時の値の表示に地域別設定を使用する]** チェック ボックスをオンにします。 **[全般オプション]** ダイアログ ボックスを表示するには、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で **[ツール]** メニューの **[オプション]** をクリックします。  
  
         および  
  
    -   1753 年 1 月 1 日～ 9999 年 12 月 31 日の日付を入力します。  
  
-   **osql** ユーティリティまたは **sqlcmd** ユーティリティからイベントをトレースしている場合は必ず、 **%** を **TextData** データ列のフィルターに付加します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
