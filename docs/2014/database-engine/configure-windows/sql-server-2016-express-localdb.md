---
title: SQL Server 2014 Express LocalDB |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user instances
- LocalDB, described
- local database runtime
- file database
- LocalDB
ms.assetid: 5a641a46-7cfb-4d7b-a90d-6e4625719d74
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8dcd0be9d5bdf14230be67c8ce2fffb708a713b9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071741"
---
# <a name="sql-server-2014-express-localdb"></a>SQL Server 2014 Express LocalDB
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] `LocalDB` 実行モードは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]プログラムの開発者を対象とします。 `LocalDB` インストールが開始に必要なファイルの最小セットをコピー、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 1 回`LocalDB`がインストールされている場合、開発者の接続を開始、特殊な接続文字列を使用しています。 接続時に、必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インフラストラクチャが自動的に作成され、開始、複雑なまたは時間のかかる構成タスクなしのデータベースを使用するアプリケーションを有効にします。 開発者ツールによって、開発者は [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを記述してテストすることができ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の完全なサーバー インスタンスを管理する必要はありません。 インスタンス[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB`を使用して管理されて、`SqlLocalDB.exe`ユーティリティです。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]`LocalDB` 代わりに使用する必要があります、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]ユーザー インスタンス機能は推奨されません。  
  
## <a name="installing-localdb"></a>LocalDB のインストール  
 インストールの主な方法`LocalDB`SqlLocalDB.msi プログラムを使用して、します。 `LocalDB` SKU をインストールするときのオプション[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]です。 選択`LocalDB`上、**機能の選択**のインストール中にページ[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]です。 インストールが 1 つだけ表示されます、`LocalDB`各メジャーのバイナリ ファイル[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]バージョン。 複数の [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロセスを開始することができ、すべてのプロセスが使用するバイナリは同じです。 インスタンス、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]として開始された、`LocalDB`として同じ制限があります [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  
  
## <a name="description"></a>説明  
 `LocalDB`セットアップ プログラムがコンピューターに必要なファイルをインストールする SqlLocalDB.msi プログラムを使用します。 インストールすると、`LocalDB`のインスタンスは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を作成して開くことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 データベースのシステム データベース ファイルは、通常は非表示になっているユーザーのローカル AppData パスに格納されます。 たとえば、**C:\Users\\<user\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\** などです。 ユーザー データベース ファイルは、ユーザーが指定する場所、通常は **C:\Users\\<user\>\Documents\\** フォルダーに格納されます。  
  
 などの詳細については`LocalDB`アプリケーションでは、次を参照してください、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ドキュメント[ローカル データの概要](http://msdn.microsoft.com/library/ms233817\(VS.110\).aspx)、[チュートリアル: SQL Server LocalDB データベースを作成する](http://msdn.microsoft.com/library/ms233763\(VS.110\).aspx)、および。[チュートリアル: SQL Server LocalDB データベース (Windows フォーム) 内のデータに接続する](http://msdn.microsoft.com/library/ms171890\(VS.110\).aspx)です。  
  
 詳細については、 `LocalDB` API を参照してください[SQL Server Express LocalDB インスタンス API リファレンス](http://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx)と[LocalDBStartInstance 関数](http://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx)です。  
  
 SqlLocalDb ユーティリティは、の新しいインスタンスを作成できます`LocalDB`、開始および停止のインスタンス`LocalDB`、管理に役立つオプションが含まれます`LocalDB`です。  SqlLocalDb ユーティリティの詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
 インスタンスの照合順序`LocalDB`SQL_Latin1_General_CP1_CI_AS に設定されているし、変更できません。 データベース レベル、列レベル、および式レベルの照合順序は正常にサポートされます。 包含データベースは、 [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)によって定義されたメタデータおよび tempdb の照合順序ルールに従います。  
  
### <a name="restrictions"></a>制限  
 `LocalDB` マージ レプリケーションのサブスクライバーをすることはできません。  
  
 `LocalDB` FILESTREAM をサポートしていません。  
  
 `LocalDB` Service Broker に対してローカル キューをのみが許可します。  
  
 インスタンス`LocalDB`windows ファイル システム リダイレクト; のための管理の容易性の問題を持つことができます NT authority \system などのビルトイン アカウントが所有します。代わりに、所有者として通常の windows アカウントを使用します。  
  
### <a name="automatic-and-named-instances"></a>自動インスタンスと名前付きインスタンス  
 `LocalDB` 2 つの種類のインスタンスをサポートしています: 自動インスタンスと名前付きインスタンス。  
  
-   自動インスタンス`LocalDB`はパブリックです。 ユーザーのために自動的に作成および管理され、任意のアプリケーションから使用できます。 自動インスタンスが 1 つ`LocalDB`のすべてのバージョンが存在する`LocalDB`ユーザーのコンピューターにインストールします。 自動インスタンス`LocalDB`シームレスなインスタンス管理を提供します。 インスタンスを作成する必要はありません。それだけで動作します。 これにより、アプリケーションのインストールと別のコンピューターへの移行が簡単になります。 対象コンピューターに指定されたバージョンの場合`LocalDB`の自動インスタンスをインストールします。`LocalDB`そのバージョンをターゲット コンピューターにも使用できます。 自動インスタンス`LocalDB`がある予約済み名前空間に属しているインスタンス名に特殊なパターンです。 これにより、名前付きインスタンスの名前の競合`LocalDB`です。 自動インスタンスの名前は **MSSQLLocalDB**です。  
  
-   名前付きインスタンス`LocalDB`はプライベートです。 これらは、そのインスタンスの作成と管理を行う単一のアプリケーションによって所有されます。 名前付きインスタンスは他のインスタンスからの分離を可能にし、他のデータベース ユーザーとのリソースの競合を減らすことによってパフォーマンスを向上させることができます。 ユーザーが実行して名前付きインスタンスを明示的に作成する必要があります、`LocalDB`管理 API または app.config を使用して暗黙的に、マネージ アプリケーションのファイルの (ただし、マネージ アプリケーションには、API も使用できます必要な場合)。 各名前付きインスタンスの`LocalDB`が関連付けられている`LocalDB`バージョンのそれぞれのセットを指す`LocalDB`バイナリです。 インスタンス名、`LocalDB`は`sysname`データを入力し、最大 128 文字を持つことができます。 (これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の正規の名前付きインスタンスとは異なり、16 の ASCII 文字で構成される正規の NetBIOS 名に制限されることはありません)。インスタンスの名前`LocalDB`は、ファイル名内で有効な任意の Unicode 文字を含めることができます。  自動インスタンス名を使用する名前付きインスタンスは、自動インスタンスになります。  
  
 コンピューターの異なるユーザーが同じ名前のインスタンスを持つことができます。 各インスタンスは、別のユーザーとして実行している別のプロセスです。  
  
## <a name="shared-instances-of-localdb"></a>LocalDB の共有インスタンス  
 コンピューターの複数のユーザーが 1 つのインスタンスに接続する必要があるシナリオをサポートする`LocalDB`、`LocalDB`はインスタンス共有をサポートします。 インスタンスの所有者は、コンピューター上の他のユーザーに自分のインスタンスへの接続を許可することを選択できます。 自動インスタンスと名前付きインスタンス両方の`LocalDB`を共有できます。 インスタンスを共有する`LocalDB`ユーザーがその共有の名前 (別名) を選択します。 共有名はコンピューターのすべてのユーザーから参照できるため、この共有名はコンピューター上で一意である必要があります。 インスタンスの共有名`LocalDB`の名前付きインスタンスと同じ形式を持つ`LocalDB`します。  
  
 共有インスタンスを作成できるは、コンピューターの管理者のみ`LocalDB`です。 共有インスタンス`LocalDB`の共有インスタンスの所有者または管理者によって共有解除できます`LocalDB`です。 共有するのインスタンスの非共有および`LocalDB`を使用して、`LocalDBShareInstance`と`LocalDBUnShareInstance`のメソッド、 `LocalDB` API、または共有および SqlLocalDb ユーティリティの共有解除オプション。  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>LocalDB の起動および LocalDB への接続  
  
### <a name="connecting-to-the-automatic-instance"></a>自動インスタンスへの接続  
 使用する最も簡単な方法`LocalDB`は接続文字列を使用して、現在のユーザーが所有する自動インスタンスに接続する **"Server = (localdb) \MSSQLLocalDB;Integrated セキュリティ = true"** です。 ファイル名を使用して特定のデータベースに接続するには、 **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"** のような接続文字列を使用して接続します。  
  
> [!NOTE]  
>  接続しようとしているコンピューター上のユーザーを初めて`LocalDB`、自動インスタンス両方の作成し、開始します。 インスタンスの作成に時間がかかり、接続がタイムアウト メッセージで失敗する可能性があります。 この場合は、作成プロセスが完了するまで数秒待ってから再び接続します。  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>名前付きインスタンスの作成および接続  
 自動インスタンスに加えて`LocalDB`名前付きインスタンスもサポートします。 SqlLocalDB.exe プログラムを作成、開始、およびの名前付きインスタンスの停止を使用して`LocalDB`です。 SqlLocalDB.exe の詳細については、「 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)」を参照してください。  
  
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
|バージョン|\<現在のバージョン>|  
|共有名|""|  
|[所有者]|"\<Windows ユーザー>"|  
|自動作成|いいえ|  
|状態|実行|  
|前回の開始時刻|\<日付と時刻>|  
|インスタンス パイプ名|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  名前付きパイプに直接接続する必要があります、アプリケーションで .net 4.0.2 より前に、のバージョンを使用する場合、`LocalDB`です。 インスタンス パイプ名の値は、名前付きパイプのインスタンス`LocalDB`でリッスンしています。 LOCALDB # は各変更後にインスタンス パイプ名の部分のインスタンスの時間`LocalDB`が開始します。 インスタンスに接続する`LocalDB`を使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、インスタンス パイプ名を入力、**サーバー名**のボックス、**への接続[!INCLUDE[ssDE](../../includes/ssde-md.md)]**   ダイアログ ボックス。 インスタンスへの接続を確立するカスタム プログラム`LocalDB`のような接続文字列を使用します。 `SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>LocalDB の共有インスタンスへの接続  
 共有インスタンスに接続する`LocalDB`追加 **.\\** (ドット + 円記号) を共有インスタンス用に予約されている名前空間を参照する接続文字列。 例については、共有インスタンスに接続する`LocalDB`という名前`AppData`など、接続文字列を使用して`(localdb)\.\AppData`接続文字列の一部として。 共有インスタンスに接続するユーザー`LocalDB`所有していないことがあります、Windows 認証または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインです。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 トラブルシューティングについては`LocalDB`を参照してください[SQL Server 2012 Express LocalDB のトラブルシューティング](http://social.technet.microsoft.com/wiki/contents/articles/4609.aspx)です。  
  
## <a name="permissions"></a>アクセス許可  
 インスタンス[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]`LocalDB`使用するためのユーザーによって作成されたインスタンスです。 コンピューター上のすべてのユーザーがのインスタンスを使用してデータベースを作成できる`LocalDB`、そのユーザー プロファイルのファイルに格納し、自分の資格情報の処理を実行します。 インスタンスへのアクセスを既定では、`LocalDB`その所有者に制限されます。 含まれるデータ、`LocalDB`データベース ファイルをファイル システム アクセスによって保護されます。 インスタンスを使用して、その場所にファイル システム アクセスを持つ任意のユーザー データベースを開くことがユーザー データベース ファイルが共有の場所に格納されている場合`LocalDB`自身のものです。 データベース ファイルがユーザー データ フォルダーなどの保護された場所に格納されている場合は、そのユーザーおよびそのフォルダーにアクセスできる管理者だけがデータベースを開くことができます。 `LocalDB`ファイルは、1 つのインスタンスでのみ開くことができます`LocalDB`一度にです。  
  
> [!NOTE]  
>  `LocalDB` ユーザーのセキュリティ コンテキストは常に実行されます。つまり、`LocalDB`ローカル管理者グループの資格情報で実行されません。 つまり、すべてのデータベースで使用されるファイル、`LocalDB`インスタンスは、ローカルの Administrators グループのメンバーシップを考慮せず、所有するユーザーの Windows アカウントを使用してアクセス可能である必要があります。  
  
## <a name="see-also"></a>参照  
 [SqlLocalDB ユーティリティ](../../tools/sqllocaldb-utility.md)  
  
  