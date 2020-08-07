---
title: SQL Server に接続しています (MySQLToSQL) |Microsoft Docs
description: SQL Server のターゲットインスタンスに接続して MySQL データベースを移行する方法について説明します。 SSMA は SQL Server のデータベースに関するメタデータを取得します。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: f79784b6498f080b15f1ef370e8a3f31be81a871
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823301"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>SQL Server への接続 (MySQLToSQL)
MySQL データベースを SQL Server に移行するには、SQL Server のターゲットインスタンスに接続する必要があります。 接続すると、SSMA は SQL Server インスタンス内のすべてのデータベースに関するメタデータを取得し、SQL Server メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続している SQL Server のインスタンスの情報を格納しますが、パスワードは保存しません。  
  
SQL Server への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は SQL Server に再接続する必要があります。 データベースオブジェクトを SQL Server に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
SQL Server のインスタンスに関するメタデータは、自動的には同期されません。 代わりに SQL Server メタデータエクスプローラーでメタデータを更新するには、SQL Server メタデータを手動で更新する必要があります。 詳細については、このトピックで後述する「SQL Server メタデータの同期」を参照してください。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server アクセス許可  
SQL Server に接続するために使用するアカウントには、アカウントが実行するアクションに応じて、異なるアクセス許可が必要です。  
  
-   MySQL オブジェクトを構文に変換し [!INCLUDE[tsql](../../includes/tsql-md.md)] たり、SQL Server からメタデータを更新したり、変換された構文をスクリプトに保存したりするには、アカウントに SQL Server のインスタンスにログオンする権限が必要です。  
  
-   データベースオブジェクトを SQL Server に読み込むには、ターゲットデータベースの**db_owner**データベースロールのメンバーシップである最低限の権限が必要です。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server 接続の確立  
MySQL データベースオブジェクトを SQL Server 構文に変換する前に、MySQL データベースを移行する SQL Server のインスタンスへの接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、SQL Server に接続した後に MySQL スキーマレベルでカスタマイズできます。 詳細については、「 [MySQL データベースを SQL Server スキーマ &#40;MySQLToSQL&#41;にマップする](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)」を参照してください。  
  
> [!IMPORTANT]  
> SQL Server に接続する前に、SQL Server のインスタンスが実行されていて、接続を受け入れることができることを確認してください。  
  
**SQL Server に接続するには**  
  
1.  [**ファイル**] メニューの [ **SQL Server に接続**] を選択します (このオプションは、プロジェクトの作成後に有効になります)。  
  
    以前に SQL Server に接続している場合は、コマンド名が**SQL Server に再接続**されます。  
  
2.  [接続] ダイアログボックスで、SQL Server のインスタンスの名前を入力または選択します。  
  
    -   ローカルコンピューター上の既定のインスタンスに接続している場合は、 **localhost**またはドット (**.**) を入力できます。  
  
    -   別のコンピューター上の既定のインスタンスに接続している場合は、コンピューターの名前を入力します。  
  
    -   別のコンピューター上の名前付きインスタンスに接続している場合は、コンピューター名の後に円記号を入力し、インスタンス名を入力します (例、myの myinstance)。  
  
3.  SQL Server のインスタンスが既定以外のポートで接続を受け入れるように構成されている場合は、[**サーバーポート**] ボックスで SQL Server 接続に使用するポート番号を入力します。 SQL Server の既定のインスタンスの場合、既定のポート番号は1433です。 名前付きインスタンスの場合、SSMA は SQL Server Browser サービスからポート番号の取得を試みます。  
  
4.  [**認証**] ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するには、[ **Windows 認証**] を選択します。 SQL Server ログインを使用するには、[SQL Server 認証] を選択し、ログイン名とパスワードを入力します。  
  
5.  セキュリティで保護された接続では、[**暗号化接続**] チェックボックスと [ **trustservercertificate** ] チェックボックスの2つのコントロールが追加されます。 [**暗号化接続**] をオンにした場合にのみ、[ **trustservercertificate** ] チェックボックスが表示されます。 [**暗号化接続**] がオンになっている場合 (true)、 **trustservercertificate**がオフになっている場合 (false)、SQL Server の SSL 証明書が検証されます。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するには、証明書をクライアント側とサーバー側の両方にインストールする必要があります。  
  
6.  [接続] をクリックします。  
  
**より新しいバージョンの互換性**  
  
新しいバージョンの SQL Server に接続したり、再接続したりすることができます。  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロジェクトが "2005" の場合は、2008、2012、または2014または2016に接続でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]作成されたプロジェクトが2008の場合、2012または2014または2016に接続することはできますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] それより下位バージョンへの接続は許可されていません (例: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005)。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作成されたプロジェクトが2012の場合、2012または2014または2016に接続でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
4.  作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロジェクトが2014の場合、2014または2016にのみ接続でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
5.  "SQL Azure" に対して、より高いバージョンの互換性は無効です。  
  
|プロジェクトの種類と対象サーバーのバージョン|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (バージョン: 1.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (バージョン:10 .x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012<br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014<br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016<br />(バージョン:13. x)|SQL Azure|  
|-|-|-|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|はい|はい|はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||はい|はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||はい||  
|SQL Azure||||||はい|  
  
> [!IMPORTANT]  
> データベースオブジェクトの変換は、プロジェクトの種類に従って実行されますが、接続されているのバージョンによっては実行されません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 プロジェクトの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より上位のバージョン [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016) に接続している場合でも、変換は2005に従って実行されます。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータの同期  
SQL Server データベースに関するメタデータは自動的に更新されません。 SQL Server メタデータエクスプローラーのメタデータは、最初に SQL Server に接続したとき、またはメタデータを手動で更新したときにメタデータのスナップショットになります。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  SQL Server に接続していることを確認します。  
  
2.  SQL Server メタデータエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[データベース] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   MySQL スキーマと SQL Server データベースおよびスキーマ間のマッピングをカスタマイズするには、「 [Mysql データベースを SQL Server スキーマ &#40;MySQLToSQL にマッピング](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)する」を参照してください&#41;  
  
-   プロジェクトの構成オプションをカスタマイズするには、「[プロジェクトオプションの設定 &#40;MySQLToSQL](../../ssma/mysql/setting-project-options-mysqltosql.md) 」を参照してください&#41;  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [MySQL と SQL Server のデータ型 &#40;MySQLToSQL&#41;のマッピング](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)」を参照してください。  
  
-   これらのタスクを実行する必要がない場合は、MySQL データベースオブジェクト定義を SQL Server オブジェクト定義に変換できます。 詳細については、「 [MySQL データベース &#40;MySQLToSQL の変換](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)」を参照してください&#41;  
  
## <a name="see-also"></a>参照  
[MySQL データベースを SQL Server Azure SQL Database &#40;MySQLToSql&#41;に移行する](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
