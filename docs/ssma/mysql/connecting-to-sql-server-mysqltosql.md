---
title: "SQL Server (MySQLToSQL) への接続 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
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
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8a00088252b6cab4971b7574f6f3e840c326d2f8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sql-server-mysqltosql"></a>SQL Server (MySQLToSQL) に接続します。
MySQL データベースを SQL Server に移行するには、SQL Server のターゲット インスタンスに接続する必要があります。 接続するときに、SSMA は SQL Server のインスタンス内のすべてのデータベースに関するメタデータを取得し、SQL Server メタデータ エクスプ ローラーでデータベースのメタデータを表示します。 SSMA は、パスワードは保存されませんに接続している SQL Server のインスタンスの情報を格納します。  
  
プロジェクトを閉じるまで、SQL Server への接続がアクティブな保たれます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Server に再接続する必要があります。 SQL Server にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン作業できます。  
  
SQL Server のインスタンスに関するメタデータが自動的に同期されていません。 代わりに、SQL Server メタデータ エクスプ ローラー内のメタデータを更新するには、SQL Server のメタデータを手動で更新する必要があります。 詳細については、このトピックの後半の「SQL Server のメタデータの同期」セクションを参照してください。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server のアクセス許可  
SQL Server への接続に使用されるアカウントには、アカウントが実行する操作に応じて異なるアクセス許可が必要です。  
  
-   MySQL オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプトの構文は、SQL Server からのメタデータを更新するかに変換された構文を保存する、アカウントに SQL Server のインスタンスにログオンする権限が必要です。  
  
-   データベース オブジェクトを SQL Server に読み込むには、最小限のアクセス許可の要件は、メンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server の接続を確立します。  
MySQL データベースのオブジェクトを SQL Server の構文に変換する前に、または複数の MySQL データベースを移行する SQL Server のインスタンスへの接続を確立する必要があります。  
  
接続のプロパティを定義するときは、オブジェクトとデータを移行するデータベースを指定します。 SQL Server に接続した後は、MySQL スキーマ レベルでは、このマッピングをカスタマイズできます。 詳細については、次を参照してください[MySQL データベースを SQL Server スキーマ &#40; にマッピング。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> SQL Server に接続しようとすると、前に、SQL Server のインスタンスが実行されているとが接続を受け入れることを確認します。  
  
**SQL Server に接続するには**  
  
1.  **ファイル**メニューの  **SQL Server への接続**(プロジェクトの作成後にこのオプションは有効です)。  
  
    SQL Server に以前接続した場合、コマンド名になります**SQL Server に再接続**です。  
  
2.  接続ダイアログ ボックスで入力または SQL Server のインスタンスの名前を選択します。  
  
    -   ローカル コンピューターの既定のインスタンスに接続する場合は、入力**localhost**またはドット (**.**)。  
  
    -   別のコンピューターの既定のインスタンスに接続する場合は、コンピューターの名前を入力します。  
  
    -   別のコンピューターの名前付きインスタンスに接続する場合は、コンピューター名の後に、円記号とし、myserver \myinstance など、インスタンス名を入力します。  
  
3.  SQL Server のインスタンスが既定以外のポートで接続を受け入れるように構成されている場合で SQL Server の接続に使用されるポート番号を入力、**サーバー ポート**ボックス。 SQL Server の既定のインスタンス、既定のポート番号は 1433 です。 名前付きインスタンスは、SSMA を SQL Server Browser サービスからポート番号を取得を試みます。  
  
4.  **認証**ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するのには、選択**Windows 認証**です。 SQL Server ログインを使用するのには、SQL Server 認証を選択し、ログイン名とパスワードを入力します。  
  
5.  セキュリティで保護された接続は、2 つのコントロールを追加、**暗号化接続**と**TrustServerCertificate**チェック ボックスです。 場合にのみ**暗号化接続**がオンになって、 **TrustServerCertificate**  チェック ボックスが表示されます。 ときに**暗号化接続**がオンになって (true) および**TrustServerCertificate**がオフになって (false)、これは SQL Server の SSL 証明書を検証します。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するのには、証明書をクライアント側およびサーバー側でにインストールする必要があります。  
  
6.  [接続] をクリックします。  
  
**高いバージョンの互換性**  
  
以降のバージョンの SQL Server への接続または再接続することができます。  
  
1.  接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成したプロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 です。  
  
2.  接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成したプロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 つまり下位バージョンに接続することはできませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
3.  接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成したプロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 です。  
  
4.  のみに接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成したプロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 です。  
  
5.  "SQL azure"より高いバージョンの互換性が正しくありません。  
  
||||||||  
|-|-|-|-|-|-|-|  
|**プロジェクトの種類と対象サーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (バージョン: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (バージョン: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012<br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014<br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016<br />(Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||はい|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014||||はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016|||||はい||  
|SQL Azure||||||はい|  
  
> [!IMPORTANT]  
> バージョンに従っていませんが、プロジェクトの種類に従って、データベース オブジェクトの変換は実行が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続します。 場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005年プロジェクトの変換は実行が 1 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 より新しいバージョンに接続している場合でも[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)](SQL Server 2008/SQL Server 2012]/[SQL Server 2014/SQL Server 2016)。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータを同期します。  
SQL Server データベースについてのメタデータは自動的に更新されません。 SQL Server メタデータ エクスプ ローラー内のメタデータは、まず、SQL Server に接続されているか、前回を手動でときのメタデータのスナップショットには、メタデータが更新されました。 です。 すべてのデータベース、または任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  SQL Server に接続していることを確認します。  
  
2.  SQL Server メタデータ エクスプ ローラーで、データベースまたは更新するデータベース スキーマの横にあるチェック ボックスを選択します。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、データベースの横にあるボックスを選択します。  
  
3.  データベース、または個々 のデータベースまたはデータベース スキーマを右クリックし **データベースと同期する**です。  
  
## <a name="next-step"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   MySQL のスキーマと SQL Server データベースおよびスキーマ間のマッピングをカスタマイズするを参照してください。[マッピング MySQL データベースを SQL Server スキーマと #40 です。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   プロジェクトの構成オプションをカスタマイズするを参照してください。[プロジェクト オプションの設定 & #40 です。MySQLToSQL &#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング MySQL および SQL Server データ型 & #40 です。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   次のタスクを実行する必要はない場合、は、SQL Server オブジェクトの定義に MySQL のデータベース オブジェクトの定義を変換することができます。 詳細については、次を参照してください。 [MySQL データベースを変換する & #40 です。MySQLToSQL &#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への MySQL データベースの移行MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

