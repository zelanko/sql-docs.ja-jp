---
title: "SMO イベントの処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
caps.latest.revision: "48"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f71df8b210fff4524a4e84a5ee64da039d741e6c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="handling-smo-events"></a>SMO イベントの処理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]イベント ハンドラーを使用してサブスクライブできるサーバー イベントの種類があると、<xref:Microsoft.SqlServer.Management.Common.ServerConnection>オブジェクト。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) のインスタンス クラスの多くは、サーバー上で特定のアクションが発生した場合にイベントをトリガーすることができます。  
  
 これらのイベントは、イベント ハンドラーを設定し、関連するイベントをサブスクライブすることで、プログラムを使用して処理を行うことができます。 サブスクリプションは SMO クライアント プログラムの終了時にすべて削除されるため、この種類のイベント ハンドリングは一時的なものです。  
  
## <a name="connectioncontext-event-handling"></a>ConnectionContext イベント ハンドリング  
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトは複数のイベントの種類をサポートしています。 イベント プロパティは、適切なイベント ハンドラーのインスタンスに対して設定されている必要があります。また、イベント ハンドラー オブジェクトは、イベントを処理するプロテクト関数として定義されている必要があります。  
  
## <a name="event-subscription"></a>イベント サブスクリプション  
 イベントを処理するには、イベント ハンドラー クラスを作成し、イベント ハンドラー クラスのインスタンスの作成して、イベント ハンドラーを親オブジェクトに割り当てて、イベントをサブスクライブします。  
  
 イベントを処理するためには、イベント ハンドラー クラスが作成される必要があります。 イベント ハンドラー クラスは、2 つ以上のイベント ハンドラー関数を含めることができます。また、処理されるイベントに対してインストールされている必要があります。 イベント ハンドラー関数からのイベントに関する情報が表示される、 *ServerEventNotificatificationArgs*イベントに関する情報を報告するために使用するパラメーターです。  
  
 処理可能なデータベースとサーバーのイベントの種類で表示されます、<xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet>クラスおよび<xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>クラスです。  
  
## <a name="example"></a>例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください[Visual C &#35; を作成する。Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  

  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a>Visual Basic でのイベント ハンドラーの登録およびイベント ハンドリングのサブスクライブ  
 このコード例では、イベント ハンドラーを設定する方法およびデータベース イベントをサブスクライブする方法を示します。  
  
```VBNET
'Create an event handler subroutine that runs when a table is created.
Private Sub MyCreateEventHandler(ByVal sender As Object, ByVal e As ServerEventArgs)
    Console.WriteLine("A table has just been added to the AdventureWorks2012 2008 database.")
End Sub
'Create an event handler subroutine that runs when a table is deleted.
Private Sub MyDropEventHandler(ByVal sender As Object, ByVal e As ServerEventArgs)
    Console.WriteLine("A table has just been dropped from the AdventureWorks2012 2008 database.")
End Sub
Sub Main()
    'Connect to the local, default instance of SQL Server.
    Dim srv As Server
    srv = New Server
    'Reference the AdventureWorks2012 database.
    Dim db As Database
    db = srv.Databases("AdventureWorks2012")
    'Create a database event set that contains the CreateTable event only.
    Dim databaseCreateEventSet As New DatabaseEventSet
    databaseCreateEventSet.CreateTable = True
    'Create a server event handler and set it to the first event handler subroutine.
    Dim serverCreateEventHandler As ServerEventHandler
    serverCreateEventHandler = New ServerEventHandler(AddressOf MyCreateEventHandler)
    'Subscribe to the first server event handler when a CreateTable event occurs.
    db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler)
    'Create a database event set that contains the DropTable event only.
    Dim databaseDropEventSet As New DatabaseEventSet
    databaseDropEventSet.DropTable = True
    'Create a server event handler and set it to the second event handler subroutine.
    Dim serverDropEventHandler As ServerEventHandler
    serverDropEventHandler = New ServerEventHandler(AddressOf MyDropEventHandler)
    'Subscribe to the second server event handler when a DropTable event occurs.
    db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler)
    'Start event handling.
    db.Events.StartEvents()
    'Create a table on the database.
    Dim tb As Table
    tb = New Table(db, "Test_Table")
    Dim mycol1 As Column
    mycol1 = New Column(tb, "Name", DataType.NChar(50))
    mycol1.Collation = "Latin1_General_CI_AS"
    mycol1.Nullable = True
    tb.Columns.Add(mycol1)
    tb.Create()
    'Remove the table.
    tb.Drop()
    'Wait until the events have occured.
    Dim x As Integer
    Dim y As Integer
    For x = 1 To 1000000000
        y = x * 2
    Next
    'Stop event handling.
    db.Events.StopEvents()

End Sub
``` 
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a>Visual C# でのイベント ハンドラーの登録およびイベント ハンドリングのサブスクライブ  
 このコード例では、イベント ハンドラーを設定する方法およびデータベース イベントをサブスクライブする方法を示します。  
  
```csharp  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
