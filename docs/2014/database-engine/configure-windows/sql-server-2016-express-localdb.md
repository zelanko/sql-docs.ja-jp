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
manager: craigg
ms.openlocfilehash: 224facf54b0cde09f97010be472e3cc28754e94b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62756992"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]は、プログラムの開発[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]者を対象としたの実行モードです。 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` `LocalDB`のインストールでは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を開始するために必要な最小限のファイルセットがコピーされます。 を`LocalDB`インストールすると、開発者は特殊な接続文字列を使用して接続を開始します。 接続時に、必要な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インフラストラクチャが自動的に作成および開始されるため、複雑な、または時間のかかる構成タスクを行わなくてもアプリケーションでデータベースを使用できます。 開発者ツールによって、開発者は [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを記述してテストすることができ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の完全なサーバー インスタンスを管理する必要はありません。 の[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] `LocalDB`インスタンスは、 `SqlLocalDB.exe`ユーティリティを使用して管理されます。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB`非推奨とされたユーザー [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]インスタンス機能の代わりに、を使用する必要があります。  
  
## <a name="installing-localdb"></a>LocalDB のインストール  
 をインストール`LocalDB`する主な方法は、SqlLocalDB プログラムを使用することです。 `LocalDB`は、の SKU をインストールする場合[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]のオプションです。 の`LocalDB`インストール中に [**機能**の[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]選択] ページでを選択します。 メジャー `LocalDB` [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]バージョンごとに、バイナリファイルを1つだけインストールできます。 複数の [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロセスを開始することができ、すべてのプロセスが使用するバイナリは同じです。 として開始[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]された`LocalDB`のインスタンスには、と同じ制限があります。[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>[説明]  
 `LocalDB`セットアッププログラムは、SqlLocalDB プログラムを使用して、コンピューターに必要なファイルをインストールします。 インストールが完了`LocalDB`すると、は[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]データベースを作成して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]開くことができるのインスタンスになります。 データベースのシステム データベース ファイルは、通常は非表示になっているユーザーのローカル AppData パスに格納されます。 たとえば、**C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\** などです。 ユーザー データベース ファイルは、ユーザーが指定する場所、通常は **C:\Users\\<user\>\Documents\\** フォルダーに格納されます。  
  
 アプリケーション`LocalDB`にを含める方法の詳細については[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 、ドキュメント「[ローカルデータの概要](https://msdn.microsoft.com/library/ms233817\(VS.110\).aspx)」、「[チュートリアル: SQL Server localdb データベースの作成](https://msdn.microsoft.com/library/ms233763\(VS.110\).aspx)」、および「[チュートリアル: SQL Server localdb データベースのデータへの接続 (Windows フォーム)](https://msdn.microsoft.com/library/ms171890\(VS.110\).aspx)」を参照してください。  
  
 Api の`LocalDB`詳細については、「 [SQL SERVER EXPRESS LocalDB インスタンス api リファレンス](https://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx)」および「 [localdbstartinstance 関数](https://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx)」を参照してください。  
  
 SqlLocalDb ユーティリティでは、の新しいインスタンス`LocalDB`を作成し、の`LocalDB`インスタンスを起動および停止することができます`LocalDB`。また、を管理するためのオプションも用意されています。  SqlLocalDb ユーティリティの詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
 の`LocalDB`インスタンスの照合順序は SQL_Latin1_General_CP1_CI_AS に設定されており、変更することはできません。 データベース レベル、列レベル、および式レベルの照合順序は正常にサポートされます。 包含データベースは、 [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)によって定義されたメタデータおよび tempdb の照合順序ルールに従います。  
  
### <a name="restrictions"></a>制限  
 `LocalDB`マージレプリケーションサブスクライバーにすることはできません。  
  
 `LocalDB`では、FILESTREAM はサポートされていません。  
  
 `LocalDB`Service Broker のローカルキューのみを許可します。  
  
 NT AUTHORITY\SYSTEM など`LocalDB`のビルトインアカウントによって所有されているのインスタンスは、windows ファイルシステムのリダイレクトによって、管理容易性の問題が発生する可能性があります。代わりに、通常の windows アカウントを所有者として使用します。  
  
### <a name="automatic-and-named-instances"></a>自動インスタンスと名前付きインスタンス  
 `LocalDB`では、自動インスタンスと名前付きインスタンスという2種類のインスタンスがサポートされています。  
  
-   の`LocalDB`自動インスタンスはパブリックです。 ユーザーのために自動的に作成および管理され、任意のアプリケーションから使用できます。 の`LocalDB` 1 つの自動インスタンスは、ユーザー `LocalDB`のコンピューターにインストールされているのすべてのバージョンに存在します。 の自動インスタンス`LocalDB`を使用すると、シームレスなインスタンス管理を実現できます。 インスタンスを作成する必要はありません。それだけで動作します。 これにより、アプリケーションのインストールと別のコンピューターへの移行が簡単になります。 対象コンピューターに指定バージョンの `LocalDB` がインストールされている場合、その対象コンピューターでも同じバージョンの `LocalDB` の自動インスタンスを使用できます。 の自動インスタンス`LocalDB`のインスタンス名には、予約済みの名前空間に属する特殊なパターンがあります。 これにより、の名前付きインスタンス`LocalDB`との名前の競合を防ぐことができます。 自動インスタンスの名前は **MSSQLLocalDB**です。  
  
-   の`LocalDB`名前付きインスタンスはプライベートです。 これらは、そのインスタンスの作成と管理を行う単一のアプリケーションによって所有されます。 名前付きインスタンスは他のインスタンスからの分離を可能にし、他のデータベース ユーザーとのリソースの競合を減らすことによってパフォーマンスを向上させることができます。 名前付きインスタンスは、 `LocalDB`管理 API を介してユーザーが明示的に作成するか、マネージアプリケーションの app.config ファイルを通じて暗黙的に作成する必要があります (ただし、マネージアプリケーションでは、必要に応じて API も使用できます)。 の`LocalDB`各名前付きインスタンスには`LocalDB` 、それぞれの`LocalDB`バイナリセットを指す、関連付けられたバージョンがあります。 のインスタンス名`LocalDB`は`sysname`データ型で、最大128文字まで使用できます。 (これは、の正規の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]名前付きインスタンスとは異なり、16の ASCII 文字の通常の NetBIOS 名に制限されます)。の`LocalDB`インスタンスの名前には、ファイル名の中で有効な Unicode 文字を含めることができます。  自動インスタンス名を使用する名前付きインスタンスは、自動インスタンスになります。  
  
 コンピューターの異なるユーザーが同じ名前のインスタンスを持つことができます。 各インスタンスは、別のユーザーとして実行している別のプロセスです。  
  
## <a name="shared-instances-of-localdb"></a>LocalDB の共有インスタンス  
 コンピューターの複数のユーザーがの1つの`LocalDB`インスタンスに接続する必要があるシナリオ`LocalDB`をサポートするために、はインスタンス共有をサポートしています。 インスタンスの所有者は、コンピューター上の他のユーザーに自分のインスタンスへの接続を許可することを選択できます。 の自動インスタンスと名前付き`LocalDB`インスタンスの両方を共有できます。 
  `LocalDB` のインスタンスを共有するには、ユーザーがその共有名 (別名) を選択します。 共有名はコンピューターのすべてのユーザーから参照できるため、この共有名はコンピューター上で一意である必要があります。 の`LocalDB`インスタンスの共有名は、の`LocalDB`名前付きインスタンスと同じ形式です。  
  
 の共有インスタンスを作成できるの`LocalDB`は、コンピューターの管理者だけです。 の`LocalDB`共有インスタンスは、管理者またはの`LocalDB`共有インスタンスの所有者によって共有を解除できます。 の`LocalDB`インスタンスを共有および共有解除するには`LocalDBShareInstance` 、 `LocalDBUnShareInstance` `LocalDB` API のメソッドとメソッド、または SqlLocalDb ユーティリティの share オプションと share オプションを使用します。  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>LocalDB の起動および LocalDB への接続  
  
### <a name="connecting-to-the-automatic-instance"></a>自動インスタンスへの接続  
 を使用`LocalDB`する最も簡単な方法は、接続文字列 **"Server = (localdb) \MSSQLLocalDB; Integrated Security = true"** を使用して、現在のユーザーが所有する自動インスタンスに接続することです。 ファイル名を使用して特定のデータベースに接続するには、 **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"** のような接続文字列を使用して接続します。  
  
> [!NOTE]  
>  コンピューターのユーザーが初めてに`LocalDB`接続しようとしたときに、自動インスタンスの作成と開始の両方を行う必要があります。 インスタンスの作成に時間がかかり、接続がタイムアウト メッセージで失敗する可能性があります。 この場合は、作成プロセスが完了するまで数秒待ってから再び接続します。  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>名前付きインスタンスの作成および接続  
 自動インスタンスに加えて、で`LocalDB`は名前付きインスタンスもサポートされています。 SqlLocalDB プログラムを使用して、の`LocalDB`名前付きインスタンスを作成、開始、および停止します。 SqlLocalDB.exe の詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
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
|Name|"LocalDBApp1"|  
|Version|\<現在のバージョン>|  
|共有名|""|  
|Owner|"\<Windows ユーザー>"|  
|自動作成|いいえ|  
|State|実行中|  
|前回の開始時刻|\<日付と時刻の>|  
|インスタンス パイプ名|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  アプリケーションで4.0.2 の前に .NET のバージョンを使用する場合は、 `LocalDB`の名前付きパイプに直接接続する必要があります。 インスタンスパイプ名の値は、の`LocalDB`インスタンスがリッスンしている名前付きパイプです。 LOCALDB # の後のインスタンスパイプ名の部分は、の`LocalDB`インスタンスが起動されるたびに変わります。 を`LocalDB`使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]してのインスタンスに接続するには、[**接続先[!INCLUDE[ssDE](../../includes/ssde-md.md)] ** ] ダイアログボックスの [**サーバー名**] ボックスにインスタンスパイプ名を入力します。 カスタムプログラムからは、のような接続文字列を使用`LocalDB`して、のインスタンスへの接続を確立できます。`SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>LocalDB の共有インスタンスへの接続  
 の`LocalDB`共有インスタンスに接続するには、接続文字列に. (ドット + 円記号) を追加**し\\ **て、共有インスタンス用に予約されている名前空間を参照します。 たとえば、という名前`LocalDB` `AppData`の共有インスタンスに接続するには、接続文字列の`(localdb)\.\AppData`一部としてなどの接続文字列を使用します。 所有していないの`LocalDB`共有インスタンスに接続するユーザーには、Windows 認証または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインが必要です。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 トラブルシューティング`LocalDB`の詳細については、「 [SQL Server 2012 Express LocalDB のトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/4609.aspx)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 の[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB`インスタンスは、ユーザーが使用するために作成したインスタンスです。 コンピューター上のすべてのユーザーは、の`LocalDB`インスタンスを使用してデータベースを作成し、そのユーザープロファイルにファイルを格納して、その資格情報でプロセスを実行することができます。 既定では、のインスタンスへの`LocalDB`アクセスは、その所有者に制限されています。 に含まれるデータ`LocalDB`は、データベースファイルへのファイルシステムアクセスによって保護されます。 ユーザーデータベースファイルが共有の場所に格納されている場合は、所有しているの`LocalDB`インスタンスを使用して、その場所へのファイルシステムアクセス権を持つすべてのユーザーがデータベースを開くことができます。 データベース ファイルがユーザー データ フォルダーなどの保護された場所に格納されている場合は、そのユーザーおよびそのフォルダーにアクセスできる管理者だけがデータベースを開くことができます。 ファイル`LocalDB`は、一度に1つの`LocalDB`インスタンスによってのみ開くことができます。  
  
> [!NOTE]  
>  `LocalDB`常にユーザーのセキュリティコンテキストで実行されます。つまり、 `LocalDB`ローカル管理者のグループの資格情報では実行されません。 つまり、 `LocalDB`インスタンスで使用されるすべてのデータベースファイルには、ローカルの Administrators グループのメンバーシップを考慮せずに、所有ユーザーの Windows アカウントを使用してアクセスできる必要があります。  
  
## <a name="see-also"></a>参照  
 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)  
  
  
