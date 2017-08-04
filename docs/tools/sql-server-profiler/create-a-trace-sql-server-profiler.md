---
title: "トレース (SQL Server Profiler) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f0008f30aa031c98e251fd1e4fc764b801a16858
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-trace-sql-server-profiler"></a>トレースの作成 (SQL Server Profiler)
  このトピックでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してトレースを作成する方法について説明します。  
  
### <a name="to-create-a-trace"></a>トレースを作成するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > **注:** **[接続の確立直後にトレースを開始する]** を選択している場合は、 **[トレースのプロパティ]** ダイアログ ボックスは表示されずに、トレースが開始されます。 この設定は、オフにする、**ツール** メニューのをクリックして**オプション**、し、チェック ボックスを接続の確立直後後にトレースを開始をオフにします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **[使用するテンプレート]** ボックスの一覧で、トレースの基本として使用するトレース テンプレートを選択します。テンプレートを使用しない場合は、 **[空白]** を選択します。  
  
4.  トレース結果を保存するには、次のいずれかの操作を実行します。  
  
    -   **[ファイルに保存する]** をクリックし、トレースをファイルにキャプチャします。 **[最大ファイル サイズの設定]**ボックスに値を指定します。 既定値は 5 MB です。  
  
         ファイル サイズが最大に達したとき新しいファイルを自動的に作成する場合は、 **[ファイル ロールオーバーを有効にする]** チェック ボックスをオンにします。 または、 **[サーバーがトレース データを処理する]**を選択することもできます。これを選択すると、トレースを実行しているサービスが、クライアント アプリケーションに代わってトレース データを処理します。 サーバーがトレース データを処理する場合、ストレス条件下でもイベントはスキップされません。ただし、サーバー パフォーマンスは低下する場合があります。  
  
    -   トレースをデータベース テーブルに記録する場合は、 **[テーブルに保存]** をクリックします。  
  
         必要に応じて、 **[最大行数の設定 (1000 行単位)]**チェック ボックスをオンにし、値を指定します。  
  
    > **注意!!** トレース結果をファイルにもテーブルにも保存しない場合は、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を開いているときにトレースを表示できます。 ただし、トレースを停止して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を終了した場合、トレース結果は失われます。 このようにトレース結果が失われないようにするには、**[ファイル]** メニューの **[保存]** をクリックして、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を終了する前にトレース結果を保存します。  
  
5.  必要に応じて、 **[トレース停止時刻を有効にする]** チェック ボックスをオンにして、停止日時を指定します。  
  
6.  イベント、データ列、フィルターを追加または削除するには、**[イベントの選択]** タブをクリックします。 詳細については、「[トレース ファイルに含めるイベントとデータ列の指定 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)」を参照してください。  
  
7.  **[実行]** をクリックしてトレースを開始します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler の実行に必要な権限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)   
 [SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  

