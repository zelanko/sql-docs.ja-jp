---
title: "SQL Server Profiler の起動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロファイラー [SQL Server Profiler], 起動"
  - "SQL Server Profiler, 起動"
  - "SQL Server Profiler の起動"
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# SQL Server Profiler の起動
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、さまざまなシナリオでのトレース出力の収集をサポートするために、いくつかの異なる方法で起動することができます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、**[スタート]** メニューや [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの **[ツール]** メニューから起動できるほか、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から起動することもできます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動し、**[ファイル]** メニューの **[新しいトレース]** をクリックすると、**[サーバーへの接続]** ダイアログ ボックスが表示されるので、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定できます。  
  
### [スタート] メニューから SQL Server Profiler を起動するには  
  
1.  **[スタート]** ボタンをクリックし、**[すべてのプログラム]**、[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、**[パフォーマンス ツール]** の順にポイントして、**[SQL Server Profiler]** をクリックします。  
  
### データベース エンジン チューニング アドバイザーで SQL Server Profiler を起動するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで、**[ツール]** メニューの **[SQL Server Profiler]** をクリックします。  
  
## Management Studio での SQL Server Profiler の起動  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  は、それぞれのインスタンスで各プロファイラー セッションを開始します。このセッションは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をシャットダウンしても実行が続きます。  
  
 以降の各手順に示すように、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の複数の場所から起動できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動すると、その時点の接続コンテキスト、トレース テンプレート、およびフィルター コンテキストが読み込まれます。  
  
#### [ツール] メニューから SQL Server Profiler を起動するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ツール]** メニューの **[SQL Server Profiler]** をクリックします。  
  
#### クエリ エディターから SQL Server Profiler を起動するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のメニュー バーの **[新しいクエリ]** をクリックします。  
  
2.  クエリ エディター内で右クリックし、**[SQL Server Profiler でクエリをトレース]** を選択します。  
  
    > [!NOTE]  
    >  接続コンテキストはエディター接続、トレース テンプレートは TSQL_SPs、適用されているフィルターは SPID = query window SPID です。  
  
#### 利用状況モニターから SQL Server Profiler を起動するには  
  
1.  オブジェクト エクスプローラーで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを右クリックし、**[利用状況モニター]** をクリックします。  
  
2.  **プロセス** ペインをクリックし、プロファイルするプロセスを右クリックして **[SQL Server Profiler のトレース プロセス]** をクリックします。  
  
    > [!NOTE]  
    >  プロセスを選択したときに、利用状況モニターが開いていた場合、接続コンテキストはオブジェクト エクスプローラー接続になります。 トレース テンプレートはサーバーの種類に応じた既定値になります。SPID は、選択されたプロセスの SPID と等しくなります。  
  
## .NET Framework のセキュリティ  
 Windows 認証モードでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行するユーザー アカウントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する権限を持っている必要があります。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でトレースを実行するには、ユーザーが ALTER TRACE 権限も持っている必要があります。  
  
## 参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Management Studio の使用 [SQL Server]](../../ssms/use-sql-server-management-studio.md)  
  
  