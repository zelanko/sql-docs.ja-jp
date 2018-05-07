---
title: SQL Server Profiler の実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 7/7/2017
ms.prod: sql
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
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0179f93aa874667098d6f8ba2550129dec281ada
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="run-sql-server-profiler"></a>SQL Server Profiler の実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  さまざまなシナリオでのトレース出力の収集をサポートするために、いくつかの異なる方法で [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、Windows 10 の **[スタート]** メニューや[!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの **[ツール]** メニューから起動できるほか、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から起動することもできます。  
  
最初に [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動し、**[ファイル]** メニューから **[新しいトレース]** を選択すると、**[サーバーへの接続]** ダイアログ ボックスが表示されるので、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定できます。  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Windows 10 の [スタート] メニューから SQL Server Profiler を起動するには  
-  [Windows] をクリックして**開始**アイコンまたはキーを押して、Windows キーおよび"SQL Server Profiler 17"の入力を開始します。 ときに、 **SQL Server Profiler 17**にタイルが表示されたら、 をクリックします。   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>データベース エンジン チューニング アドバイザーで SQL Server Profiler を起動するには  
-  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで、 **[ツール]** メニューの **[SQL Server Profiler]** をクリックします。  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>SQL Server Management Studio での SQL Server Profiler を起動するには  
 開始する[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で複数の場所から[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動すると、その時点の接続コンテキスト、トレース テンプレート、およびフィルター コンテキストが読み込まれます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 独自のインスタンスで各 SQL Server Profiler セッションを開始し、プロファイラーをシャット ダウンする場合に実行する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>[ツール] メニューから SQL Server Profiler を起動するには  
-  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **チューニング アドバイザーの** メニューの **[SQL Server Profiler]** から起動することもできます。  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>クエリ エディターから SQL Server Profiler を起動するには  
- クエリ エディター内で右クリックし、 **[SQL Server Profiler でクエリをトレース]** を選択します。  

  > [!NOTE]  
  >  接続コンテキストはエディター接続、トレース テンプレートは TSQL_SPs、適用されているフィルターは SPID = query window SPID です。  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>利用状況モニターから SQL Server Profiler を起動するには  
- 利用状況モニターで、**[プロセス]** ウィンドウをクリックし、プロファイルするプロセスを右クリックします。次に、**[SQL Server Profiler のトレース プロセス]** をクリックします。  

    > [!NOTE]  
    >  プロセスを選択したときに、利用状況モニターが開いていた場合、接続コンテキストはオブジェクト エクスプローラー接続になります。 トレース テンプレートはサーバーの種類に応じた既定値になります。SPID は、選択されたプロセスの SPID と等しくなります。  
    
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  
- Windows 認証モードでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行するユーザー アカウントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続するアクセス許可を持っている必要があります。  
- [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]でトレースを実行するには、ユーザーが ALTER TRACE 権限も持っている必要があります。  

## <a name="next-steps"></a>次の手順  
 [SQL Server Profiler の概要](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Management Studio の使用 [SQL Server]](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
