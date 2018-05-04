---
title: SQL Server (OracleToSQL) への接続 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server,Synchronizing SQL Server Metadata
ms.assetid: 1b2a8059-1829-4904-a82f-9c06de1e245f
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 76d292c3232cef760bb2dc1e28890a2fad530bee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-sql-server-oracletosql"></a>SQL Server (OracleToSQL) に接続します。
Oracle データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 R2 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 これらのいずれかに接続する必要がありますがのインスタンスを対象[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 SSMA がのインスタンス内のすべてのデータベースに関するメタデータを取得して接続すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でデータベースのメタデータを表示し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラー。 SSMA のインスタンスに関する情報を格納する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続しているが、パスワードは保存されません。  
  
接続を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロジェクトを終了するまでアクティブに保ちます。 プロジェクトを開くときにに再接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アクティブなサーバーに接続する場合。 データベース オブジェクトが読み込まれるまでオフラインで作業できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]とデータを移行します。  
  
インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が自動的に同期されていません。 代わりに、内のメタデータを更新する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、必要があります手動で更新する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。 詳細については、次を参照してください。、"Synchronizing[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ"このトピックで後述します。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server のアクセス許可  
接続に使用されるアカウント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アカウントで実行された操作に応じて異なるアクセス許可が必要です。  
  
-   Oracle オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]からメタデータを更新する構文、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、またはスクリプトに変換された構文を保存するアカウントがのインスタンスにログオンする権限を持って[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   データベース オブジェクトに読み込むために[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、アカウントのメンバーである必要があります、 **sysadmin**サーバーの役割です。 これは、CLR アセンブリをインストールする必要があります。  
  
-   データを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、アカウントのメンバーである必要があります、 **sysadmin**サーバーの役割です。 これは、実行に必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント データ移行のパッケージです。  
  
-   SSMA によって生成されるコードを実行するアカウントが必要**Execute**内のすべてのユーザー定義関数のアクセス許可、 **ssma_oracle**ターゲット データベースのスキーマです。 これらの関数は、Oracle システム関数と同等の機能を提供され、変換後のオブジェクトによって使用されます。  
  
場合への接続に使用されるアカウント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]すべての移行を実行するタスク、アカウントのメンバーである必要がありますが、 **sysadmin**サーバーの役割です。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server の接続を確立します。  
Oracle データベース オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文のインスタンスへの接続を確立する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または複数の Oracle データベースを移行します。  
  
接続のプロパティを定義するときは、オブジェクトとデータを移行するデータベースを指定します。 Oracle スキーマ レベルでは、このマッピングをカスタマイズするに接続した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください。 [SQL Server スキーマへの Oracle スキーマのマッピング&#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md)です。  
  
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
  
    再接続する場合は、このオプションは使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
5.  **認証**ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するのには、選択**Windows 認証**です。 使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログインで、 **SQL Server 認証**、ログイン名とパスワードを指定します。  
  
6.  セキュリティで保護された接続は、2 つのコントロールを追加、**暗号化接続**と**TrustServerCertificate**チェック ボックスです。 場合にのみ**暗号化接続**がオンになって、 **TrustServerCertificate**  チェック ボックスが表示されます。 ときに**暗号化接続**がオンになって (true) および**TrustServerCertificate**がオフになって (false)、これは SQL Server の SSL 証明書を検証します。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するのには、証明書をクライアント側およびサーバー側でにインストールする必要があります。  
  
7.  **[接続]** をクリックします。  
  
**高いバージョンの互換性**  
  
-   接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2008 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成した移行プロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 です。  
  
-   接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ときに、作成した移行プロジェクトは、2016 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 つまり下位バージョンに接続することはできませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   接続することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016 は、作成したプロジェクトが SQL Server 2012 の場合。  
  
||||||||  
|-|-|-|-|-|-|-|  
|**プロジェクトの種類と対象サーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (バージョン: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (バージョン: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 <br />(Version:13.x)|Azure SQL DB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||はい|[ユーザー アカウント制御]|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||はい|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||はい||
|Azure SQL DB||||||はい|
  
> [!IMPORTANT]  
> バージョンに従っていませんが、プロジェクトの種類に従って、データベース オブジェクトの変換は実行が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続しています。 場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005年プロジェクトの変換は実行が 1 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 より新しいバージョンに接続している場合でも[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2012 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016)。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータを同期します。  
に関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースが自動的に更新されません。 内のメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーは、最初に接続したときに、メタデータのスナップショットを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、または最後の時刻を手動で更新されたメタデータ。 すべてのデータベース、または任意の 1 つのデータベースまたはデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを同期するには**  
  
1.  接続していることを確認してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、データベースの横にあるチェック ボックスをオンまたはデータベースのスキーマを更新します。  
  
    たとえば、すべてのデータベースのメタデータを更新するボックスをオンに、横に**データベース**です。  
  
3.  右クリック**データベース**、または個々 のデータベースまたはデータベース スキーマ、および選択**データベースと同期する**です。  
  
## <a name="next-step"></a>次の手順  
次の手順では、プロジェクトのニーズによって異なります。  
  
-   Oracle スキーマ間のマッピングをカスタマイズして[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマを参照してください。 [SQL Server スキーマへの Oracle スキーマのマッピング&#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md)です。  
  
-   プロジェクトの構成オプションをカスタマイズするを参照してください。[プロジェクト オプションの設定&#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md)です。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするを参照してください。[マッピング Oracle と SQL Server データ型&#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)です。  
  
-   Oracle データベース オブジェクトの定義を変換できる場合は、次のタスクを実行する必要はありません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト定義します。 詳細については、次を参照してください。 [Oracle スキーマを変換する&#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)です。  
  
## <a name="see-also"></a>参照  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
