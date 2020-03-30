---
title: SQL Server Profiler の実行
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 07/07/2017
ms.openlocfilehash: 89089c07a3b13ee7764770df3d582ba449b65f53
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307796"
---
# <a name="run-sql-server-profiler"></a>SQL Server Profiler の実行

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

さまざまなシナリオでのトレース出力の収集をサポートするために、いくつかの異なる方法で [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、Windows 10 の **[スタート]** メニューや**チューニング アドバイザーの**[ツール][!INCLUDE[ssDE](../../includes/ssde-md.md)] メニューから起動できるほか、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から起動することもできます。  
  
最初に [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動し、 **[ファイル]** メニューから **[新しいトレース]** を選択すると、 **[サーバーへの接続]** ダイアログ ボックスが表示されるので、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定できます。  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Windows 10 の [スタート] メニューから SQL Server Profiler を起動するには  
-  Windows の **[スタート]** アイコンをクリックするか、Windows キーを押して、「SQL Server Profiler 17」と入力し始めます。 **[SQL Server Profiler 17]** タイルが表示されたら、それをクリックします。   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>データベース エンジン チューニング アドバイザーで SQL Server Profiler を起動するには  
-  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーで、 **[ツール]** メニューの **[SQL Server Profiler]** をクリックします。  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>SQL Server Management Studio で SQL Server Profiler を開始するには  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の複数の場所から開始できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を起動すると、その時点の接続コンテキスト、トレース テンプレート、およびフィルター コンテキストが読み込まれます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、各 SQL Server Profiler セッションがそれぞれのインスタンスで開始されます。Profiler は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をシャットダウンしても引き続き実行されます。  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>[ツール] メニューから SQL Server Profiler を起動するには  
-  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ツール]** メニューで、 **[SQL Server Profiler]** をクリックします。  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>クエリ エディターから SQL Server Profiler を起動するには  
- クエリ エディター内で右クリックし、 **[SQL Server Profiler でクエリをトレース]** を選択します。  

  > [!NOTE]  
  >  接続コンテキストはエディター接続、トレース テンプレートは TSQL_SPs、適用されているフィルターは SPID = query window SPID です。  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>利用状況モニターから SQL Server Profiler を起動するには  
- 利用状況モニターで、 **[プロセス]** ウィンドウをクリックし、プロファイルするプロセスを右クリックします。次に、 **[SQL Server Profiler のトレース プロセス]** をクリックします。  

    > [!NOTE]  
    >  プロセスを選択したときに、利用状況モニターが開いていた場合、接続コンテキストはオブジェクト エクスプローラー接続になります。 トレース テンプレートはサーバーの種類に応じた既定値になります。SPID は、選択されたプロセスの SPID と等しくなります。  
    
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  
- Windows 認証モードでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行するユーザー アカウントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続するアクセス許可を持っている必要があります。  
- [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]でトレースを実行するには、ユーザーが ALTER TRACE 権限も持っている必要があります。  

## <a name="next-steps"></a>次のステップ  
 [SQL Server Profiler の概要](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Management Studio の使用 [SQL Server]](https://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
