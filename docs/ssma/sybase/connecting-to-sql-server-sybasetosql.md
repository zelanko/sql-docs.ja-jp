---
title: "SQL Server (SybaseToSQL) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3dd8b595d897aad93d580447af4afed330cb71f9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sql-server-sybasetosql"></a>SQL Server (SybaseToSQL) に接続します。
Sybase Adaptive Server Enterprise (ASE) データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のターゲット インスタンスのいずれかに接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 SSMA がのインスタンス内のすべてのデータベースに関するメタデータを取得して接続すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でデータベースのメタデータを表示し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラー。 SSMA のインスタンスに関する情報を格納する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続しているが、パスワードは保存されません。  
  
接続を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロジェクトを終了するまでアクティブに保ちます。 プロジェクトを開くときにに再接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アクティブなサーバーに接続する場合。 データベース オブジェクトが読み込まれるまでオフラインで作業できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]とデータを移行します。  
  
インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が自動的に同期されていません。 代わりに、内のメタデータを更新する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、必要があります手動で更新する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 」の説明に従って、メタデータ、"Synchronizing[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ"このトピックで後述します。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server のアクセス許可  
接続に使用されるアカウント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]そのアカウントで実行されるアクションに応じて異なるアクセス許可が必要です。  
  
-   ASE オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]からメタデータを更新する構文、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、またはスクリプトに変換された構文を保存するアカウントがのインスタンスにログインする権限を持って[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   データベース オブジェクトに読み込むために[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、最小のアクセス許可の要件は、メンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
-   データを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、アカウントのメンバーである必要があります、 **sysadmin**サーバーの役割です。 これは、実行に必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント データ移行のパッケージです。  
  
-   SSMA によって生成されるコードを実行するアカウントが必要**Execute**内のすべてのユーザー定義関数のアクセス許可、 **ssma_syb**のスキーマ、 **sysdb**データベース。 これらの関数は、ASE システム関数と同等の機能を提供され、変換後のオブジェクトによって使用されます。  
  
場合への接続に使用されるアカウント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]すべての移行を実行するタスク、アカウントのメンバーである必要がありますが、 **sysadmin**サーバーの役割です。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server の接続を確立します。  
ASE 使用するデータベース オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文のインスタンスへの接続を確立する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ASE データベースまたはデータベースを移行します。  
  
接続のプロパティを定義するときは、オブジェクトとデータを移行するデータベースを指定します。 接続した後、ASE スキーマ レベルでは、このマッピングをカスタマイズすることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください[Sybase ASE スキーマのマッピングを SQL Server スキーマ &#40;。SybaseToSQL &#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
> [!IMPORTANT]  
> 接続しようとする前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、ことを確認して、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が実行されていると、接続を受け入れることができます。  
  
**SQL Server に接続するには**  
  
1.  **ファイル**メニューの  **SQL Server への接続**です。  
  
    接続されていた場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、コマンド名になります**SQL Server に再接続**です。  
  
2.  接続ダイアログ ボックスで入力するかのインスタンスの名前を選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    -   ローカル コンピューターの既定のインスタンスに接続する場合は、入力**localhost**またはドット (**.**)。  
  
    -   別のコンピューターの既定のインスタンスに接続する場合は、コンピューターの名前を入力します。  
  
    -   別のコンピューターの名前付きインスタンスに接続する場合は、コンピューター名の後に、円記号とし、myserver \myinstance など、インスタンス名を入力します。  
  
3.  場合、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既定以外のポートで接続を受け入れる、使用されるポート番号を入力するように構成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]内の接続、**サーバー ポート**ボックス。 既定のインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既定のポート番号は 1433 です。 名前付きインスタンスは、SSMA はからのポート番号の取得を試みます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービス。  
  
4.  **データベース**ボックスで、ターゲット データベースの名前を入力します。  
  
    このオプションに再接続するときは使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
5.  **認証**ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するのには、選択**Windows 認証**です。 使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログインで、 **SQL Server 認証**ログイン名とパスワードを入力します。  
  
6.  セキュリティで保護された接続は、2 つのコントロールを追加、**暗号化接続**と**TrustServerCertificate**チェック ボックスです。 場合にのみ**暗号化接続**がオンになって、 **TrustServerCertificate**  チェック ボックスが表示されます。 ときに**暗号化接続**がオンになって (true) および**TrustServerCertificate**がオフになって (false)、これは SQL Server の SSL 証明書を検証します。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するのには、証明書をクライアント側およびサーバー側でにインストールする必要があります。  
  
7.  **[接続]**をクリックします。  
  
**高いバージョンの互換性**  
  
-   接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成した移行プロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 です。  
  
-   接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成した移行プロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 つまり下位バージョンに接続することはできませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   のみに接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016 は、作成したプロジェクトが SQL Server 2012 の場合。  
  
-   SQL Azure の高いバージョンの互換性が正しくありません。  
  
||||||||
|-|-|-|-|-|-|-|
|**プロジェクトの種類と対象サーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (バージョン: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (バージョン: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 <br />(Version:13.x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||はい|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||はい|はい|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||はい||  
|SQL Azure||||||はい|  
  
> [!IMPORTANT]  
> バージョンに従っていませんが、プロジェクトの種類に従って、データベース オブジェクトの変換は実行が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続しています。 場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005年プロジェクトの変換は実行が 1 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 より新しいバージョンに接続している場合でも[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016)  
  
## <a name="reconnecting-to-sql-server"></a>SQL Server への再接続  
接続を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロジェクトを終了するまでアクティブに保ちます。 プロジェクトを開くときにに再接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アクティブなサーバーに接続する場合。 データベース オブジェクトを読み込み、メタデータを更新するまでオフラインで作業できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データを移行します。  
  
再接続プロシージャ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]接続を確立するための手順と同じです。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータを同期します。  
に関するメタデータ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースが自動的に更新されません。 内のメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーは、最初に接続したときに、メタデータのスナップショットを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、または最後の時刻を手動で更新されたメタデータ。 すべてのデータベース、または任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  接続していることを確認してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、データベースの横にあるチェック ボックスをオンまたはデータベースのスキーマを更新します。  
  
    たとえば、すべてのデータベースのメタデータを更新するボックスをオンに、横に**データベース**です。  
  
3.  データベースまたは個々 のデータベースまたはデータベース スキーマを右クリックし、**データベースと同期する**です。  
  
## <a name="next-step"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   ASE データベースおよびスキーマ間のマッピングをカスタマイズするかどうかと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマを参照してください[に SQL Server スキーマ &#40; Sybase ASE スキーマのマッピング。SybaseToSQL &#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
-   プロジェクトの構成オプションをカスタマイズする場合を参照してください。[プロジェクト オプションの設定 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
-   カスタム ソースとターゲットのデータ型のマッピングを参照してください[マッピング Sybase ASE と SQL Server データ型 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Sybase ASE データベース オブジェクトの定義を変換できる場合は、これらのいずれかを実行する必要はありません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト定義します。 詳細については、次を参照してください。 [Sybase ASE データベース オブジェクトの変換 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

