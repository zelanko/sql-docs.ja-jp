---
title: SQL Server (AccessToSQL) への接続 |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- authentication
- instance of SQL Server
- metadata, refreshing
- ports
- refreshing metadata
- spaces in database names
- special characters
- SQL Server
- SQL Server, connecting
- SQL Server, connecting to
- SQL Server, reconnecting
ms.assetid: f84cf007-ddf1-4396-a07c-3e0729abc769
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 572c516cfac93f3122814cdc93a3eed4f2b9c291
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="connecting-to-sql-server-accesstosql"></a>SQL Server (AccessToSQL) に接続します。
Access データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のターゲット インスタンスに接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 SSMA がのインスタンス内のデータベースに関するメタデータを取得して接続すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でデータベースのメタデータを表示および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラー。 SSMA のインスタンスに関する情報を格納する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続しているが、パスワードは保存されません。  
  
プロジェクトを閉じるまで、SQL Server への接続がアクティブな保たれます。 プロジェクトを再度開くと、アクティブなサーバーに接続する場合 SQL Server に再接続する必要があります。 SQL Server にデータベース オブジェクトを読み込むし、データを移行するまで、オフライン作業できます。  
  
SQL Server のインスタンスに関するメタデータが自動的に同期されていません。 代わりに、SQL Server メタデータ エクスプ ローラー内のメタデータを更新するには、SQL Server のメタデータを手動で更新する必要があります。 詳細については、このトピックの後半の「SQL Server のメタデータの同期」セクションを参照してください。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server のアクセス許可  
接続に使用されるアカウント[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]そのアカウントで実行されるアクションに応じて異なるアクセス許可が必要です。  
  
-   アクセス オブジェクトに変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]からメタデータを更新する、構文[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、またはスクリプトに変換された構文を保存するアカウントがのインスタンスにログインする権限を持って[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   データベース オブジェクトに読み込むために[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]とデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、最小のアクセス許可の要件は、メンバーシップ、 **db_owner**ターゲット データベースのデータベース ロール。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server の接続を確立します。  
データベース オブジェクトを変換する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文のインスタンスへの接続を確立する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Access データベースを移行します。  
  
接続のプロパティを定義するときは、オブジェクトとデータを移行するデータベースを指定します。 接続した後は、データベース レベルのアクセスには、このマッピングをカスタマイズすることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 詳細については、次を参照してください[マッピング ソースとターゲット データベース。](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
> [!IMPORTANT]  
> 接続する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、ことを確認して、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]が実行されていると、接続を受け入れることができます。 詳細については、次を参照してください。"に接続する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース エンジン"の[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
**SQL Server に接続するには**  
  
1.  **ファイル**メニューの  **SQL Server への接続**です。  
  
    接続されていた場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、コマンド名になります**SQL Server に再接続**です。  
  
2.  **サーバー名**ボックス入力するかのインスタンスの名前を選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    -   ローカル コンピューターの既定のインスタンスに接続する場合は、入力**localhost**またはドット (**.**)。  
  
    -   別のコンピューターの既定のインスタンスに接続する場合は、コンピューターの名前を入力します。  
  
    -   名前付きインスタンスに接続する場合は、コンピューター名、バック スラッシュとインスタンス名を入力します。 例: myserver \myinstance です。  
  
    -   アクティブなユーザー インスタンスへの接続に[!INCLUDE[ssExpress](../../includes/ssexpress_md.md)]、名前付きパイプを使用して接続プロトコル、パイプ名をなどを指定して\\ \\.\pipe\sql\query です。 詳細については、[!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] のドキュメントを参照してください。  
  
3.  場合、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既定以外のポートで接続を受け入れる、使用されるポート番号を入力するように構成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]内の接続、**サーバー ポート**ボックス。 既定のインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既定のポート番号は 1433 です。 名前付きインスタンスは、SSMA はからのポート番号の取得を試みます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービス。  
  
4.  **データベース**ボックスで、オブジェクトおよびデータ移行のターゲット データベースの名前を入力します。  
  
    このオプションに再接続するときは使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    ターゲット データベース名には、スペースや特殊文字を含めることはできません。 たとえばに Access データベースを移行できます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "abc"という名前のデータベースです。 Access データベースを移行することはできませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース"、b、c"をという名前です。  
  
    接続した後、データベースごとには、このマッピングをカスタマイズすることができます。 詳細については、次を参照してください[マッピング ソースとターゲット データベース。](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
5.  **認証**ドロップダウン メニューで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するのには、選択**Windows 認証**です。 使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログインで、 **SQL Server 認証**、ユーザー名とパスワードを指定します。  
  
6.  セキュリティで保護された接続の場合は、2 つのコントロールが追加、**暗号化接続** チェック ボックスと**TrustServerCertificate**チェック ボックスをオンします。 場合にのみ**暗号化接続**チェック ボックスをオン**TrustServerCertificate**  チェック ボックスが表示されます。 ときに**暗号化接続**は checked(true) と**TrustServerCertificate** unchecked(false) は、SQL Server の SSL 証明書を検証します。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するのには、証明書をクライアント側およびサーバー側でにインストールする必要があります。  
  
7.  **[接続]**をクリックします。  
  
**高いバージョンの互換性**  
  
以降のバージョンの SQL Server への接続または再接続することができます。  
  
1.  作成されたプロジェクトが SQL Server 2005、SQL Server 2008 または SQL Server 2012 に接続することができます。  
  
2.  作成されたプロジェクトは、SQL Server 2008 が低いバージョンなどの SQL Server 2005 に接続することはできません、SQL Server 2012 に接続することができます。  
  
3.  作成されたプロジェクトが SQL Server 2012、SQL Server 2012 のみに接続することができます。  
  
4.  SQL Azure の高いバージョンの互換性が正しくありません。  
  
||||||||
|-|-|-|-|-|-|-|
|**プロジェクトの種類と対象サーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 (バージョン: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 (バージョン: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 (Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 (Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 (Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||はい|[ユーザー アカウント制御]|[ユーザー アカウント制御]|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||はい|[ユーザー アカウント制御]|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||はい|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||はい||
|SQL Azure||||||はい|
  
> [!IMPORTANT]  
> 接続されている SQL Server のバージョンに従っていませんが、プロジェクトの種類に従って、データベース オブジェクトの変換を実施します。 SQL Server 2005 プロジェクトが発生した場合の変換は実行がに従って SQL Server 2005 を SQL Server (SQL Server 2008/SQL Server 2012]/[SQL Server 2014/SQL Server 2016) の上位バージョンに接続している場合でもです。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータを同期します。  
場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマを変更する接続した後、サーバーと、メタデータを同期することができます。  
  
**SQL Server のメタデータを同期するために**  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ エクスプ ローラーで、右クリック**データベース**、し、**データベースと同期する**です。  
  
## <a name="reconnecting-to-sql-server"></a>SQL Server への再接続  
接続を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロジェクトを終了するまでアクティブに保ちます。 プロジェクトを開くときにに再接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アクティブなサーバーに接続する場合。 データベース オブジェクトが読み込まれるまでオフラインで作業できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]とデータを移行します。  
  
再接続プロシージャ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]接続を確立するための手順と同じです。  
  
## <a name="next-steps"></a>次の手順  
ソースとターゲット データベースの間のマッピングをカスタマイズする場合は、「[マッピング ソースとターゲット データベース](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)するデータベース オブジェクトに変換する、次の手順は、それ以外の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文を使用して[変換データベース オブジェクト](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
