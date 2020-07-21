---
title: SQL Server 2014 Express LocalDB |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- user instances
- LocalDB, described
- local database runtime
- file database
- LocalDB
ms.assetid: 5a641a46-7cfb-4d7b-a90d-6e4625719d74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3c43604604580c5924be4daf4d473407564d247
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934883"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` は、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] プログラムの開発者を対象としたの実行モードです。 `LocalDB`のインストールでは、を開始するために必要な最小限のファイルセットがコピーさ [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] れます。 `LocalDB`をインストールすると、開発者は特殊な接続文字列を使用して接続を開始します。 接続時に、必要な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インフラストラクチャが自動的に作成および開始されるため、複雑な、または時間のかかる構成タスクを行わなくてもアプリケーションでデータベースを使用できます。 開発者ツールによって、開発者は [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを記述してテストすることができ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の完全なサーバー インスタンスを管理する必要はありません。 のインスタンス [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] `LocalDB` は、ユーティリティを使用して管理され `SqlLocalDB.exe` ます。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB`[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]非推奨とされたユーザーインスタンス機能の代わりに、を使用する必要があります。  
  
## <a name="installing-localdb"></a>LocalDB のインストール  
 をインストールする主 `LocalDB` な方法は、SqlLocalDB.msi プログラムを使用することです。 `LocalDB`は、の SKU をインストールする場合のオプションです [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 。 `LocalDB`のインストール中に [**機能の選択**] ページでを選択し [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ます。 `LocalDB`メジャーバージョンごとに、バイナリファイルを1つだけインストールでき [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ます。 複数の [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロセスを開始することができ、すべてのプロセスが使用するバイナリは同じです。 として開始されたのインスタンスには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] `LocalDB` と同じ制限があります。[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>説明  
 `LocalDB`セットアッププログラムでは、SqlLocalDB.msi プログラムを使用して、コンピューターに必要なファイルをインストールします。 インストールが完了 `LocalDB` すると、は [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] データベースを作成して開くことができるのインスタンスになり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 データベースのシステム データベース ファイルは、通常は非表示になっているユーザーのローカル AppData パスに格納されます。 たとえば、**C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\** などです。 ユーザー データベース ファイルは、ユーザーが指定する場所、通常は **C:\Users\\<user\>\Documents\\** フォルダーに格納されます。  
  
 アプリケーションにを含める方法の詳細については、 `LocalDB` [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ドキュメント「[ローカルデータの概要](https://msdn.microsoft.com/library/ms233817\(VS.110\).aspx)」、「[チュートリアル: SQL Server localdb データベースの作成](https://msdn.microsoft.com/library/ms233763\(VS.110\).aspx)」、および「[チュートリアル: SQL Server localdb データベースのデータへの接続 (Windows フォーム)](https://msdn.microsoft.com/library/ms171890\(VS.110\).aspx)」を参照してください。  
  
 Api の詳細については `LocalDB` 、「 [SQL Server Express LOCALDB インスタンス api リファレンス](https://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx)」および「 [Localdbstartinstance 関数](https://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx)」を参照してください。  
  
 SqlLocalDb ユーティリティでは、の新しいインスタンスを作成し、 `LocalDB` のインスタンスを起動および停止することができ `LocalDB` ます。また、を管理するためのオプションも用意されてい `LocalDB` ます。  SqlLocalDb ユーティリティの詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
 のインスタンスの照合順序 `LocalDB` は SQL_Latin1_General_CP1_CI_AS に設定されており、変更することはできません。 データベース レベル、列レベル、および式レベルの照合順序は正常にサポートされます。 包含データベースは、 [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)によって定義されたメタデータおよび tempdb の照合順序ルールに従います。  
  
### <a name="restrictions"></a>制約  
 `LocalDB`マージレプリケーションサブスクライバーにすることはできません。  
  
 `LocalDB`では、FILESTREAM はサポートされていません。  
  
 `LocalDB`Service Broker のローカルキューのみを許可します。  
  
 `LocalDB`NT AUTHORITY\SYSTEM などのビルトインアカウントによって所有されているのインスタンスは、windows ファイルシステムのリダイレクトによって、管理容易性の問題が発生する可能性があります。代わりに、通常の windows アカウントを所有者として使用します。  
  
### <a name="automatic-and-named-instances"></a>自動インスタンスと名前付きインスタンス  
 `LocalDB`では、自動インスタンスと名前付きインスタンスという2種類のインスタンスがサポートされています。  
  
-   の自動インスタンス `LocalDB` はパブリックです。 ユーザーのために自動的に作成および管理され、任意のアプリケーションから使用できます。 の1つの自動インスタンスは `LocalDB` `LocalDB` 、ユーザーのコンピューターにインストールされているのすべてのバージョンに存在します。 の自動インスタンスを使用すると、 `LocalDB` シームレスなインスタンス管理を実現できます。 インスタンスを作成する必要はありません。それだけで動作します。 これにより、アプリケーションのインストールと別のコンピューターへの移行が簡単になります。 対象コンピューターに指定バージョンの `LocalDB` がインストールされている場合、その対象コンピューターでも同じバージョンの `LocalDB` の自動インスタンスを使用できます。 の自動インスタンスのインスタンス名には、 `LocalDB` 予約済みの名前空間に属する特殊なパターンがあります。 これにより、の名前付きインスタンスとの名前の競合を防ぐことができ `LocalDB` ます。 自動インスタンスの名前は **MSSQLLocalDB**です。  
  
-   の名前付きインスタンス `LocalDB` はプライベートです。 これらは、そのインスタンスの作成と管理を行う単一のアプリケーションによって所有されます。 名前付きインスタンスは他のインスタンスからの分離を可能にし、他のデータベース ユーザーとのリソースの競合を減らすことによってパフォーマンスを向上させることができます。 名前付きインスタンスは、管理 API を介してユーザーが明示的に作成するか、マネージアプリケーションの app.config ファイルを使用して暗黙的に作成する必要があり `LocalDB` ます (ただし、マネージアプリケーションでは、必要に応じて API も使用できます)。 の各名前付きインスタンスに `LocalDB` は `LocalDB` 、それぞれのバイナリセットを指す、関連付けられたバージョンがあり `LocalDB` ます。 のインスタンス名 `LocalDB` は `sysname` データ型で、最大128文字まで使用できます。 (これは、の正規の名前付きインスタンスと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は異なり、16の ASCII 文字の通常の NetBIOS 名に制限されます)。のインスタンスの名前には、 `LocalDB` ファイル名の中で有効な Unicode 文字を含めることができます。  自動インスタンス名を使用する名前付きインスタンスは、自動インスタンスになります。  
  
 コンピューターの異なるユーザーが同じ名前のインスタンスを持つことができます。 各インスタンスは、別のユーザーとして実行している別のプロセスです。  
  
## <a name="shared-instances-of-localdb"></a>LocalDB の共有インスタンス  
 コンピューターの複数のユーザーがの1つのインスタンスに接続する必要があるシナリオをサポートするために `LocalDB` 、はインスタンス共有をサポートしてい `LocalDB` ます。 インスタンスの所有者は、コンピューター上の他のユーザーに自分のインスタンスへの接続を許可することを選択できます。 の自動インスタンスと名前付きインスタンスの両方を `LocalDB` 共有できます。 `LocalDB` のインスタンスを共有するには、ユーザーがその共有名 (別名) を選択します。 共有名はコンピューターのすべてのユーザーから参照できるため、この共有名はコンピューター上で一意である必要があります。 のインスタンスの共有名は、 `LocalDB` の名前付きインスタンスと同じ形式 `LocalDB` です。  
  
 の共有インスタンスを作成できるのは、コンピューターの管理者だけ `LocalDB` です。 の共有インスタンスは、 `LocalDB` 管理者またはの共有インスタンスの所有者によって共有を解除でき `LocalDB` ます。 のインスタンスを共有および共有解除するに `LocalDB` `LocalDBShareInstance` は、 `LocalDBUnShareInstance` API のメソッドとメソッド、 `LocalDB` または SqlLocalDb ユーティリティの share オプションと share オプションを使用します。  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>LocalDB の起動および LocalDB への接続  
  
### <a name="connecting-to-the-automatic-instance"></a>自動インスタンスへの接続  
 を使用する最も簡単 `LocalDB` な方法は、接続文字列 **"Server = (localdb) \MSSQLLocalDB; Integrated Security = true"** を使用して、現在のユーザーが所有する自動インスタンスに接続することです。 ファイル名を使用して特定のデータベースに接続するには、 **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"** のような接続文字列を使用して接続します。  
  
> [!NOTE]  
>  コンピューターのユーザーが初めてに接続しようとしたときに、 `LocalDB` 自動インスタンスの作成と開始の両方を行う必要があります。 インスタンスの作成に時間がかかり、接続がタイムアウト メッセージで失敗する可能性があります。 この場合は、作成プロセスが完了するまで数秒待ってから再び接続します。  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>名前付きインスタンスの作成および接続  
 自動インスタンスに加えて、では `LocalDB` 名前付きインスタンスもサポートされています。 SqlLocalDB.exe プログラムを使用して、の名前付きインスタンスを作成、開始、および停止し `LocalDB` ます。 SqlLocalDB.exe の詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
```ms-dos  
REM Create an instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" create LocalDBApp1  
REM Start the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" start LocalDBApp1  
REM Gather information about the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\120\Tools\Binn\SqlLocalDB.exe" info LocalDBApp1  
```  
  
 上記の最後の行によって、次のような情報が返されます。  
  
|||  
|-|-|  
|名前|"LocalDBApp1"|  
|バージョン|\<Current Version>|  
|共有名|""|  
|所有者|"\<Your Windows User>"|  
|自動作成|いいえ|  
|State|実行中|  
|前回の開始時刻|\<Date and Time>|  
|インスタンス パイプ名|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  アプリケーションで4.0.2 の前に .NET のバージョンを使用する場合は、の名前付きパイプに直接接続する必要があり `LocalDB` ます。 インスタンスパイプ名の値は、のインスタンスがリッスンしている名前付きパイプです `LocalDB` 。 LOCALDB # の後のインスタンスパイプ名の部分は、のインスタンスが起動されるたびに変わり `LocalDB` ます。 を使用してのインスタンスに接続するには、[ `LocalDB` [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **接続先 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ** ] ダイアログボックスの [**サーバー名**] ボックスにインスタンスパイプ名を入力します。 カスタムプログラムからは、の `LocalDB` ような接続文字列を使用して、のインスタンスへの接続を確立できます。`SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>LocalDB の共有インスタンスへの接続  
 の共有インスタンスに接続するには、 `LocalDB` 接続文字列に. (ドット + 円記号) を追加**し \\ **て、共有インスタンス用に予約されている名前空間を参照します。 たとえば、という名前の共有インスタンスに接続するには、接続 `LocalDB` 文字列の一部としてなどの `AppData` 接続文字列を使用し `(localdb)\.\AppData` ます。 所有していないの共有インスタンスに接続するユーザーには、 `LocalDB` Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインが必要です。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 トラブルシューティングの詳細について `LocalDB` は、「 [SQL Server 2012 Express LocalDB のトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/4609.aspx)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 のインスタンス [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` は、ユーザーが使用するために作成したインスタンスです。 コンピューター上のすべてのユーザーは、のインスタンスを使用してデータベースを作成し `LocalDB` 、そのユーザープロファイルにファイルを格納して、その資格情報でプロセスを実行することができます。 既定では、のインスタンスへのアクセス `LocalDB` は、その所有者に制限されています。 に含まれるデータ `LocalDB` は、データベースファイルへのファイルシステムアクセスによって保護されます。 ユーザーデータベースファイルが共有の場所に格納されている場合は、所有しているのインスタンスを使用して、その場所へのファイルシステムアクセス権を持つすべてのユーザーがデータベースを開くことができ `LocalDB` ます。 データベース ファイルがユーザー データ フォルダーなどの保護された場所に格納されている場合は、そのユーザーおよびそのフォルダーにアクセスできる管理者だけがデータベースを開くことができます。 `LocalDB`ファイルは、一度に1つのインスタンスによってのみ開くことができ `LocalDB` ます。  
  
> [!NOTE]  
>  `LocalDB`常にユーザーのセキュリティコンテキストで実行されます。つまり、 `LocalDB` ローカル管理者のグループの資格情報では実行されません。 つまり、インスタンスで使用されるすべてのデータベースファイルには、 `LocalDB` ローカルの Administrators グループのメンバーシップを考慮せずに、所有ユーザーの Windows アカウントを使用してアクセスできる必要があります。  
  
## <a name="see-also"></a>参照  
 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)  
  
  
