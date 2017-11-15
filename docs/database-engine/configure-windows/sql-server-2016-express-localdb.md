---
title: SQL Server 2016 Express LocalDB | Microsoft Docs
ms.custom: 
ms.date: 08/10/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user instances
- LocalDB, described
- local database runtime
- file database
- LocalDB
ms.assetid: 5a641a46-7cfb-4d7b-a90d-6e4625719d74
caps.latest.revision: "42"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 15c7e7ce18d60b766251f171a6f671a679d93990
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-2016-express-localdb"></a>SQL Server 2016 Express LocalDB

 > 以前のバージョンの SQL Server に関連するコンテンツの詳細については、「[SQL Server 2014 Express LocalDB](https://msdn.microsoft.com/en-US/library/hh510202(SQL.120).aspx)」を参照してください。

Microsoft SQL Server 2016 Express **LocalDB** は、開発者を対象とした [SQL Server Express](https://msdn.microsoft.com/library/ms144275(SQL.130).aspx) の機能です。 SQL Server 2016 Express with Advanced Services で利用できます。  

 **LocalDB** インストールによって、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の開始に最低限必要なファイルがコピーされます。 LocalDB のインストール後に、特殊な接続文字列を使用して接続を開始できます。 接続時に、必要な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インフラストラクチャが自動的に作成および開始されるため、複雑な構成タスクを行わなくてもアプリケーションでデータベースを使用できます。 開発者ツールによって、開発者は [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを記述してテストすることができ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の完全なサーバー インスタンスを管理する必要はありません。 
 
 
 ## <a name="try-it-out"></a>お試しください 
  
-   SQL Server 2016 Express は、「**[SQL Server ダウンロード](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)**」からダウンロードしてインストールできます。 LocalDB は、インストール中に選択する機能で、メディアをダウンロードするときに使用できます。 メディアをダウンロードする場合は、 **[Express Advanced]** または **[LocalDB]** パッケージを選択します。 
  
-   Azure アカウントをすでにお持ちですか?  すでにお持ちの場合は、 **[こちら](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/)** にアクセスして、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] がインストール済みの仮想マシンをすぐにご利用いただけます。  
  
## <a name="install-localdb"></a>LocalDB をインストールする  
 インストール ウィザードまたは SqlLocalDB.msi プログラムを使用して、 **LocalDB** をインストールします。 **LocalDB** は [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]をインストールするときのオプションです。 
 
インストール時に **[機能の選択/共有機能]** ページで **LocalDB** を選択します。 主要な **のバージョンごとに** LocalDB [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のバイナリ ファイルのインストールが 1 つだけ表示されます。 複数の [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロセスを開始することができ、すべてのプロセスが使用するバイナリは同じです。 LocalDB [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] として開始された **LocalDB** のインスタンスには [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  

 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] **LocalDB** のインスタンスは、 **SqlLocalDB.exe** ユーティリティを使用して管理されます。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] **LocalDB** LocalDB [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] を使用する必要があります。 
  
## <a name="description"></a>説明  
 **LocalDB** セットアップ プログラムは、SqlLocalDB.msi プログラムを使用してコンピューターに必要なファイルをインストールします。 **LocalDB** はインストールされると [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のインスタンスとなり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを作成して開くことができます。 データベースのシステム データベース ファイルは、通常は非表示になっているユーザーのローカル AppData パスに格納されます。 たとえば、**C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\** などです。 ユーザー データベース ファイルは、ユーザーが指定する場所、通常は **C:\Users\\<user\>\Documents\\** フォルダーに格納されます。  
  
 **LocalDB** をアプリケーションに含める方法については、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のマニュアル「[ローカル データの概要](http://msdn.microsoft.com/library/ms233817\(VS.110\).aspx)」、「[チュートリアル: SQL Server LocalDB データベースの作成](http://msdn.microsoft.com/library/ms233763\(VS.110\).aspx)」、「[チュートリアル: SQL Server LocalDB データベースのデータへの接続 (Windows Forms)](http://msdn.microsoft.com/library/ms171890\(VS.110\).aspx)」を参照してください。  
  
 **LocalDB** API の詳細については、「 [SQL Server Express LocalDB のインスタンス API リファレンス](http://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx) 」および「 [LocalDBStartInstance 関数](http://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx)」を参照してください。  
  
 SqlLocalDb ユーティリティは、 **LocalDB**の新しいインスタンス作成、 **LocalDB**インスタンスの起動と終了を行うことができ、 **LocalDB**の管理に役立つオプションが含まれます。  SqlLocalDb ユーティリティの詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
 **LocalDB** のインスタンスの照合順序は SQL_Latin1_General_CP1_CI_AS に設定され、変更することはできません。 データベース レベル、列レベル、および式レベルの照合順序は正常にサポートされます。 包含データベースは、 [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)によって定義されたメタデータおよび tempdb の照合順序ルールに従います。  
  
### <a name="restrictions"></a>制限  
 **LocalDB** はマージ レプリケーションのサブスクライバーとして使用することはできません。  
  
 **LocalDB** では FILESTREAM がサポートされていません。  
  
 **LocalDB** では Service Broker に対してローカル キューのみが許可されます。  
  
 NT AUTHORITY\SYSTEM などの組み込みのアカウントが所有する **LocalDB** のインスタンスには、Windows ファイル システムのリダイレクトのため管理の容易性の問題が生じることがあります。代わりに、所有者として通常の Windows アカウントを使用します。  
  
### <a name="automatic-and-named-instances"></a>自動インスタンスと名前付きインスタンス  
 **LocalDB** では、自動インスタンスと名前付きインスタンスという 2 種類のインスタンスがサポートされています。  
  
-   **LocalDB** の自動インスタンスはパブリックです。 ユーザーのために自動的に作成および管理され、任意のアプリケーションから使用できます。 どのバージョンの **LocalDB** に対しても、ユーザーのコンピューターにインストールされている **LocalDB** の自動インスタンスが 1 つ存在します。 **LocalDB** の自動インスタンスを使用すると、シームレスなインスタンス管理を実行できます。 インスタンスを作成する必要はありません。それだけで動作します。 これにより、アプリケーションのインストールと別のコンピューターへの移行が簡単になります。 対象コンピューターに指定バージョンの **LocalDB** がインストールされている場合、その対象コンピューターでも同じバージョンの **LocalDB** の自動インスタンスを使用できます。 **LocalDB** の自動インスタンスのインスタンス名には特殊なパターンがあり、これは予約済み名前空間に属します。 これにより、 **LocalDB**の名前付きインスタンスとの名前の競合を防ぎます。 自動インスタンスの名前は **MSSQLLocalDB**です。  
  
-   **LocalDB** の名前付きインスタンスはプライベートです。 これらは、そのインスタンスの作成と管理を行う単一のアプリケーションによって所有されます。 名前付きインスタンスは他のインスタンスからの分離を可能にし、他のデータベース ユーザーとのリソースの競合を減らすことによってパフォーマンスを向上させることができます。 名前付きインスタンスは、ユーザーが **LocalDB** 管理 API を通じて明示的に作成するか、マネージ アプリケーションの app.config ファイルを通じて暗黙的に作成する必要があります (ただし、マネージ アプリケーションでは必要に応じて API も使用できます)。 **LocalDB** の各名前付きインスタンスには、 **LocalDB** バイナリの特定のセットを指す特定の **LocalDB** バージョンが関連付けられています。 **LocalDB** のインスタンス名は **sysname** データ型で、最大文字数は 128 文字です (これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の正規の名前付きインスタンスとは異なり、16 の ASCII 文字で構成される正規の NetBIOS 名に制限されることはありません)。**LocalDB** のインスタンス名には、ファイル名内で有効な任意の Unicode 文字を使用できます。  自動インスタンス名を使用する名前付きインスタンスは、自動インスタンスになります。  
  
 コンピューターの異なるユーザーが同じ名前のインスタンスを持つことができます。 各インスタンスは、別のユーザーとして実行している別のプロセスです。  
  
## <a name="shared-instances-of-localdb"></a>LocalDB の共有インスタンス  
 コンピューターの複数のユーザーが **LocalDB**の単一インスタンスに接続する必要のあるシナリオをサポートするために、 **LocalDB** はインスタンス共有をサポートします。 インスタンスの所有者は、コンピューター上の他のユーザーに自分のインスタンスへの接続を許可することを選択できます。 **LocalDB** の自動インスタンスと名前付きインスタンスの両方を共有できます。 **LocalDB** のインスタンスを共有するには、ユーザーがその共有名 (別名) を選択します。 共有名はコンピューターのすべてのユーザーから参照できるため、この共有名はコンピューター上で一意である必要があります。 **LocalDB** のインスタンスの共有名は、 **LocalDB**の名前付きインスタンスと同じ形式です。  
  
 コンピューターの管理者だけが、 **LocalDB**の共有インスタンスを作成できます。 **LocalDB** の共有インスタンスは、管理者または **LocalDB**の共有インスタンスの所有者が共有解除できます。 **LocalDB**のインスタンスを共有または共有解除するには、 `LocalDBShareInstance` LocalDB `LocalDBUnShareInstance` API の **メソッドと** メソッドを使用するか、SqlLocalDb ユーティリティの共有および共有解除オプションを使用します。  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>LocalDB の起動および LocalDB への接続  
  
### <a name="connecting-to-the-automatic-instance"></a>自動インスタンスへの接続  
 **LocalDB** を使用する最も簡単な方法は、接続文字列 **"Server=(localdb)\MSSQLLocalDB;Integrated Security=true"**を使用して、現在のユーザーが所有する自動インスタンスに接続することです。 ファイル名を使用して特定のデータベースに接続するには、 **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"**のような接続文字列を使用して接続します。  
  
> [!NOTE]  
>  あるコンピューターでユーザーが初めて **LocalDB**に接続しようとする場合、自動インスタンスが必ず作成され開始されます。 インスタンスの作成に時間がかかり、接続がタイムアウト メッセージで失敗する可能性があります。 この場合は、作成プロセスが完了するまで数秒待ってから再び接続します。  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>名前付きインスタンスの作成および接続  
 **LocalDB** では、自動インスタンスに加えて名前付きインスタンスもサポートされます。 SqlLocalDB.exe プログラムを使用して、 **LocalDB**の名前付きインスタンスを作成、開始、および停止します。 SqlLocalDB.exe の詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
```ms-dos  
REM Create an instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" create LocalDBApp1  
REM Start the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" start LocalDBApp1  
REM Gather information about the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" info LocalDBApp1  
```  
  
 上記の最後の行によって、次のような情報が返されます。  
  
|||  
|-|-|  
|名前|"LocalDBApp1"|  
|バージョン|\<現在のバージョン>|  
|共有名|""|  
|所有者|"\<Windows ユーザー>"|  
|自動作成|いいえ|  
|状態|実行|  
|前回の開始時刻|\<日付と時刻>|  
|インスタンス パイプ名|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  アプリケーションで .NET 4.0.2 より前のバージョンを使用している場合、 **LocalDB**の名前付きパイプに直接接続する必要があります。 インスタンス パイプ名の値は、 **LocalDB** のインスタンスがリッスンしている名前付きパイプです。 LOCALDB# の後ろのインスタンス パイプ名の部分は、**LocalDB** のインスタンスが開始されるたびに変わります。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して **LocalDB** のインスタンスに接続するには、**[[!INCLUDE[ssDE](../../includes/ssde-md.md)]への接続]** ダイアログ ボックスにある **[サーバー名]** ボックスにインスタンス パイプ名を入力します。 カスタム プログラムで **LocalDB** LocalDB `SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>LocalDB の共有インスタンスへの接続  
 **LocalDB** の共有インスタンスに接続するには、**.\\** (ドット + 円記号) を接続文字列に追加して、共有インスタンス用に予約されている名前空間を参照します。 たとえば、 **という名前の** LocalDB `AppData` の共有インスタンスに接続するには、接続文字列の一部として `(localdb)\.\AppData` などの接続文字列を使用します。 自身のものではない **LocalDB** の共有インスタンスに接続するユーザーには、Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインが必要です。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 **LocalDB**のトラブルシューティングについては、「 [SQL Server 2012 Express LocalDB のトラブルシューティング](http://social.technet.microsoft.com/wiki/contents/articles/4609.aspx)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 NT AUTHORITY\SYSTEM などの組み込みのアカウントが所有する [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]**LocalDB** のインスタンスは、ユーザーによって作成される、ユーザー専用のインスタンスです。 コンピューター上のユーザーであれば、データベースを作成できます。データベースを作成するには、 **LocalDB**のインスタンスを使用して、ファイルをそのユーザー プロファイルに格納し、自分の資格情報を使用して処理を実行します。 既定では、 **LocalDB** のインスタンスにアクセスできるのは、その所有者に制限されます。 **LocalDB** に含まれるデータは、データベース ファイルにアクセスするファイル システムによって保護されます。 ユーザー データベース ファイルが共有の場所に格納されている場合は、ファイル システムでその場所にアクセスできるユーザーであればだれでも、所有する **LocalDB** のインスタンスを使用してデータベースを開くことができます。 データベース ファイルがユーザー データ フォルダーなどの保護された場所に格納されている場合は、そのユーザーおよびそのフォルダーにアクセスできる管理者だけがデータベースを開くことができます。 **LocalDB** ファイルを開く際には、 **LocalDB** のインスタンスを一度に 1 つしか使用できません。  
  
> [!NOTE]  
>  **LocalDB** は、常にユーザーのセキュリティ コンテキストに基づいて実行されます。つまり、 **LocalDB** は、ローカル管理者グループの資格情報で実行されることはありません。 そのため、 **LocalDB** インスタンスで使用されるすべてのデータベース ファイルは、ローカルの Administrators グループのメンバーシップを考慮することなく、所有するユーザーの Windows アカウントを使用してアクセスできる必要があります。  
  
## <a name="see-also"></a>参照  
 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)  
  
  
