---
title: AMO の補足的なクラスとメソッドのプログラミング |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: amo
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8972d0659180558689302c77994f0c14f931593d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="programming-amo-complementary-classes-and-methods"></a>AMO の補足的なクラスとメソッドのプログラミング
  このトピックには、次のセクションが含まれます。  
  
-   [アセンブリ クラス](#Assembly)  
  
-   [バックアップと復元](#BU)  
  
-   [Trace クラス](#TRC)  
  
-   [CaptureLog クラスと CaptureXML 属性](#CL)  
  
##  <a name="Assembly"></a> アセンブリ クラス  
 アセンブリにより、ユーザーの機能を拡張[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]によって新しいストアド プロシージャや多次元式 (MDX) 関数を追加します。 詳細については、次を参照してください。 [AMO のその他のクラスとメソッド](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)です。  
  
 アセンブリの追加や削除は簡単で、オンラインで実行できます。 アセンブリをデータベースに追加するにはデータベース管理者である必要があり、サーバー オブジェクトに追加するにはサーバー管理者である必要があります。  
  
 次のサンプルは、指定されたデータベースにアセンブリを追加し、そのアセンブリを実行するためのサービス アカウントを割り当てます。 このアセンブリが既にデータベースに存在する場合は、追加する前に削除します。  
  
```  
static public void CreateStoredProcedures(Database db)  
{  
    ClrAssembly clrAssembly;  
  
    // Verify That assembly exist in database and drop it  
    if (db.Assemblies.ContainsName("StoredProcedures"))  
    {  
        clrAssembly = db.Assemblies.FindByName("StoredProcedures");  
        clrAssembly.Drop();  
    }  
  
    // Create the CLR assembly  
    clrAssembly = db.Assemblies.Add("StoredProcedures");  
    clrAssembly.ImpersonationInfo = new ImpersonationInfo(  
        ImpersonationMode.ImpersonateServiceAccount);  
    clrAssembly.PermissionSet = PermissionSet.Unrestricted;  
  
    // Load the assembly files  
    clrAssembly.LoadFiles(Environment.CurrentDirectory  
        + @"\StoredProcedures2.dll", false);  
  
    clrAssembly.Update();  
}  
  
```  
  
##  <a name="BU"></a> バックアップと復元方法  
 管理者は、Backup メソッドと Restore メソッドを使用して、データベースのバックアップや復元を行えます。  
  
 次のサンプルは、指定されたサーバーのすべてのデータベースのバックアップを作成します。 バックアップ ファイルが既に存在する場合は上書きします。 バックアップ ファイルは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ フォルダーの BackUp フォルダーに保存されます。  
  
```  
static public void BackUpAllDatabases(Server svr)  
{  
    string fileName;  
    if ((svr != null) && ( svr.Connected))  
        foreach (Database db in svr.Databases)  
        {  
            fileName = db.Name + "_" + ((Int64)(DateTime.Today.Year * 10000 + DateTime.Today.Month * 100 + DateTime.Today.Day)).ToString()+ ".abf";  
            db.Backup(fileName, true);  
        }  
}  
```  
  
 次のサンプルは、前のサンプルの "Adventure Works" バックアップを復元します。 "My Adventure WorksDW" データベースが既に存在する場合は上書きします。  
  
```  
static public void RestoreAdventureWorks(Server svr)  
{  
    svr.Restore("Adventure Works DW_20051025.abf", "My Adventure WorksDW", true);  
}  
```  
  
##  <a name="TRC"></a> Trace クラス  
 サーバーの利用状況を監視するには、セッション トレースとサーバー トレースの 2 種類のトレースを使用する必要があります。 サーバーをトレースすると、現在のタスクがサーバーでどのように処理されているかを確認したり (セッション トレース)、サーバーの全体的な利用状況をサーバーに接続せずに確認したり (サーバー トレース) できます。  
  
 現在の利用状況のトレース (セッション トレース) では、現在のアプリケーションがサーバーで発生させているイベントに関する通知がサーバーからそのアプリケーションに送信されます。 イベントは、現在のアプリケーションのイベント ハンドラーを使用してキャプチャされます。 セッション トレースを開始するには、まず、イベントを処理するルーチンを <xref:Microsoft.AnalysisServices.SessionTrace> オブジェクトに割り当てます。  
  
 次のサンプルは、セッション トレースをセットアップして現在の利用状況をトレースする方法を示しています。 イベント ハンドラー ルーチンはサンプルの末尾にあります。これにより、すべてのトレース情報が System.Console オブジェクトに出力されます。 トレース イベントを生成するために、トレースが開始された後に "Adventure Works" サンプル キューブが完全に処理されます。  
  
```  
static public void TestSessionTraces(Server svr)  
{  
    // Start the default trace  
  
    svr.SessionTrace.OnEvent  
        += new TraceEventHandler(DefaultTrace_OnEvent);  
    svr.SessionTrace.Stopped  
        += new TraceStoppedEventHandler(DefaultTrace_Stopped);  
    svr.SessionTrace.Start();  
  
    // Process the databases  
    // The trace handlers will output all progress notifications   
    // to the console  
    Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    cube.Process(ProcessType.ProcessFull);  
  
    // Stop the default trace  
    svr.SessionTrace.Stop();  
  
}  
static public void DefaultTrace_OnEvent(object sender, TraceEventArgs e)  
{  
    Console.WriteLine("{0}", e.TextData);  
}  
  
static public void DefaultTrace_Stopped(ITrace sender, TraceStoppedEventArgs e)  
{  
    switch (e.StopCause)  
    {  
        case TraceStopCause.StoppedByUser:  
        case TraceStopCause.Finished:  
            Console.WriteLine("Processing completed successfully");  
            break;  
  
        case TraceStopCause.StoppedByException:  
            Console.WriteLine("Processing failed: {0}",  
                e.Exception.Message);  
            break;  
    }  
}  
```  
  
 サーバー トレースは、すべての情報をトレース ファイルに記録するように構成したり、サービスが再起動した場合に自動的に再開するように構成したりできます。  
  
 サーバー トレースを設定するには、まず、どのイベントをサーバーで監視するか、イベントのどのデータをトレース ファイルに保存するかを定義する必要があります。 各イベントについて、トレース ファイルに保存するデータ列を定義する必要があります。  
  
 サーバー トレースを作成するには、次の 4 つのステップを実行します。  
  
1.  サーバー トレース オブジェクトを作成し、共通の基本属性を設定します。  
  
     LogFileSize は、トレース ファイルの最大サイズ (単位は MB) を定義します。LogFileRollOver は、LogFileSize が制限に達した場合に別のファイルでログの記録を開始できるようにします。この属性を有効にすると、ファイル名にシーケンス番号が追加されます。AutoRestart は、サービスが再起動した場合にトレースを再開できるようにします。  
  
2.  イベントと、対応するデータ列を作成します。  
  
3.  必要に応じてトレースを開始/停止します。  
  
     このトレースは、サーバーに存在して、AutoRestart としてトレースが定義されている場合、もう一度開始する必要があります、トレースを停止すると後も =**true**です。  
  
4.  不要になったトレースを削除します。  
  
 次のサンプルは、トレースが既に存在する場合はそれを削除して再作成します。 トレース ファイルは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ フォルダーの Log フォルダーに保存されます。  
  
```  
static public void TestServerTraces(Server svr)  
{  
    Trace trc;  
    TraceEvent te;  
  
        trc = svr.Traces.FindByName("TestServerTraces");  
        if (trc != null)  
            trc.Drop();  
        trc = svr.Traces.Add("TestServerTraces", "TestServerTraces");  
        trc.LogFileName = ("TestServerTraces_" +((Int64)(DateTime.Now.Year * 10000 + DateTime.Now.Month * 100 + DateTime.Now.Day)).ToString() + "_" +  
                ((Int64)(DateTime.Now.Hour * 10000 + DateTime.Now.Minute * 100 + DateTime.Now.Second)).ToString() + ".trc");  
        trc.LogFileSize = 100;  
        trc.LogFileRollover = true;  
        trc.AutoRestart = false;  
  
        #region Define Events to trace & data columns per event  
        te = trc.Events.Add(TraceEventClass.ProgressReportBegin);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportCurrent);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportEnd);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.EndTime);  
        te.Columns.Add(TraceColumn.Success);  
        te.Columns.Add(TraceColumn.Error);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
        #endregion  
  
        trc.Update();  
        trc.Start();  
  
        #region Process the Adventure Works Cube  
        // The trace settings will output all progress notifications   
        // to the trace file  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        Cube cube = db.Cubes.FindByName("Adventure Works");  
        cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        trc.Stop();  
        trc.Drop();  
  
}  
```  
  
##  <a name="CL"></a> CaptureLog 属性と CaptureXml 属性  
 CaptureLog 属性を使用すると、AMO の操作から XMLA バッチ ファイルを作成できます。 CaptureLog では、データベース、キューブ、ディメンション、マイニング構造などのサーバー オブジェクトのスクリプトを作成できます。  
  
 CaptureLog を作成するには、次の手順を実行します。  
  
1.  サーバーを設定して XMLA ログのキャプチャを開始する CaptureXml 属性**true**です。  
  
     このオプションにより、これ以降のすべての AMO 操作は、サーバーに送信される代わりに文字列コレクションに保存されます。  
  
2.  通常どおりに AMO の操作を開始します。ただし、アクションは一切サーバーに送信されないので注意してください。 オブジェクトの処理、作成、削除、更新など、あらゆる操作を実行できます。  
  
3.  CaptureXml をリセットすることにより、XMLA ログのキャプチャを停止**false**です。  
  
4.  キャプチャした XMLA を確認します。そのためには、CaptureLog 文字列コレクション内の各文字列を確認するか、ConcatenateCaptureLog メソッドを使用して、すべての文字列を含む 1 つの文字列を生成します。 ConcatenateCaptureLog では、XMLA バッチを 1 つのトランザクションとして生成したり、並列処理オプションをバッチに追加したりできます。  
  
 次のサンプルで返される文字列には、[Adventure Works DW Multidimensional 2012] データベースのすべてのディメンションとすべてのキューブで完全な処理を実行するバッチ コマンドが含まれています。  
  
```  
static public string TestCaptureLog(Server svr)  
{  
    String capturedXmla = "";  
    if ((svr != null) && (svr.Connected))  
    {  
        svr.CaptureXml = true;  
  
        #region Actions to be captured to an XMLA file  
        //No action is executed during CaptureXml = true  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        foreach (Dimension dim in db.Dimensions)  
            dim.Process(ProcessType.ProcessFull);  
        foreach (Cube cube in db.Cubes)  
            cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        svr.CaptureXml = false;  
  
        capturedXmla = svr.ConcatenateCaptureLog(true, true);  
  
    }  
  
    return capturedXmla;  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [AMO の他のクラスとメソッド](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [多次元モデルの処理&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
