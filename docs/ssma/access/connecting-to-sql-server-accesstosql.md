---
title: SQL Server への接続 (SQL server への接続) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4630ae8d92dbf0e9b1c5bf615dd82d436a5751f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006649"
---
# <a name="connecting-to-sql-server-accesstosql"></a>SQL Server への接続 (SQL server)
Access データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するには、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]対象インスタンスに接続する必要があります。 接続すると、SSMA はの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス内のデータベースに関するメタデータを取得し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続先のの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに関する情報を格納しますが、パスワードは保存しません。  
  
SQL Server への接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は SQL Server に再接続する必要があります。 データベースオブジェクトを SQL Server に読み込んでデータを移行するまで、オフラインで作業することができます。  
  
SQL Server のインスタンスに関するメタデータは、自動的には同期されません。 代わりに SQL Server メタデータエクスプローラーでメタデータを更新するには、SQL Server メタデータを手動で更新する必要があります。 詳細については、このトピックで後述する「SQL Server メタデータの同期」を参照してください。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server アクセス許可  
へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続に使用するアカウントには、そのアカウントによって実行されるアクションに応じて、異なるアクセス許可が必要です。  
  
-   Access オブジェクトを構文に[!INCLUDE[tsql](../../includes/tsql-md.md)]変換したり、から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータを更新したり、変換された構文をスクリプトに保存したりするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アカウントにのインスタンスにログインする権限が必要です。  
  
-   データベースオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をに読み込んでデータをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するには、権限の最小要件は、ターゲットデータベースの**db_owner**データベースロールのメンバーシップです。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server 接続の確立  
Access データベースオブジェクトを構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換する前に、access データベースを移行するインスタンスへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続した後、Access データベースレベルでカスタマイズできます。 詳細については、「[ソースデータベースとターゲットデータベースのマッピング](mapping-source-and-target-databases-accesstosql.md)」を参照してください。  
  
> [!IMPORTANT]  
> に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続する前に、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが実行されていて、接続を受け入れることができることを確認します。 詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「データベースエンジンへの接続」を参照してください。  
  
**SQL Server に接続するには**  
  
1.  [**ファイル**] メニューの [ **SQL Server に接続**] を選択します。  
  
    以前にに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続していた場合、コマンド名は**SQL Server に再接続**されます。  
  
2.  [**サーバー名**] ボックスに、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの名前を入力または選択します。  
  
    -   ローカルコンピューター上の既定のインスタンスに接続している場合は、 **localhost**またはドット (**.**) を入力できます。  
  
    -   別のコンピューター上の既定のインスタンスに接続している場合は、コンピューターの名前を入力します。  
  
    -   名前付きインスタンスに接続する場合は、コンピューター名、円記号、およびインスタンス名を入力します。 例: My\ myinstance。  
  
    -   の[!INCLUDE[ssExpress](../../includes/ssexpress_md.md)]アクティブなユーザーインスタンスに接続するには、名前付きパイププロトコルを使用して接続し、.\pipe\sql\query です。 \\ \\などのパイプ名を指定します。 詳細については、[!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] のドキュメントを参照してください。  
  
3.  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが既定以外のポートで接続を受け入れるように構成されている場合は、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **サーバーポート**] ボックスに接続に使用するポート番号を入力します。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定のインスタンスの場合、既定のポート番号は1433です。 名前付きインスタンスの場合、SSMA は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスからポート番号の取得を試みます。  
  
4.  [**データベース**] ボックスに、オブジェクトおよびデータ移行の対象となるデータベースの名前を入力します。  
  
    このオプションは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再接続するときには使用できません。  
  
    ターゲットデータベース名にスペースや特殊文字を含めることはできません。 たとえば、"abc" という名前の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースにアクセスデータベースを移行できます。 ただし、"a b-c" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]という名前のデータベースにアクセスデータベースを移行することはできません。  
  
    このマッピングは、接続後にデータベースごとにカスタマイズできます。 詳細については、「[ソースデータベースとターゲットデータベースのマッピング](mapping-source-and-target-databases-accesstosql.md)」を参照してください。  
  
5.  [**認証**] ドロップダウンメニューで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するには、[ **Windows 認証**] を選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインを使用するには、[ **SQL Server 認証**] を選択し、ユーザー名とパスワードを入力します。  
  
6.  セキュリティで保護された接続の場合は、2つのコントロールが追加され、[**接続の暗号化**] チェックボックスと [ **trustservercertificate** ] チェックボックスが **暗号化接続**チェックボックスがオンになっている場合にのみ、 **trustservercertificate**チェックボックスが表示されます。 [**暗号化接続**] がオンになっていて (true)、 **trustservercertificate**がオフになっている場合 (false)、は SQL Server の SSL 証明書を検証します。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するには、証明書をクライアント側とサーバー側の両方にインストールする必要があります。  
  
7.  **[Connect]** をクリックします。  
  
**より新しいバージョンの互換性**  
  
新しいバージョンの SQL Server に接続したり、再接続したりすることができます。  
  
1.  作成されたプロジェクトが 2005 SQL Server 場合は SQL Server 2008 または SQL Server 2012 に接続できます。  
  
2.  作成されたプロジェクトが 2008 SQL Server ときに、SQL Server 2012 に接続できるようになりますが、SQL Server 2005 などの下位バージョンへの接続は許可されていません。  
  
3.  作成されたプロジェクトが 2012 SQL Server 場合は、SQL Server 2012 にのみ接続できます。  
  
4.  より新しいバージョンの互換性は、SQL Azure では無効です。  
  
||||||||
|-|-|-|-|-|-|-|
|**プロジェクトの種類 Vs ターゲットサーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 (バージョン: 1.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008 (バージョン:10 .x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 (バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 (バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016 (バージョン:13. x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|はい|はい|はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||はい|はい|はい|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||はい|はい|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||はい|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||はい||
|SQL Azure||||||はい|
  
> [!IMPORTANT]  
> データベースオブジェクトの変換は、プロジェクトの種類に従って実行されますが、に接続されている SQL Server のバージョンごとには実行されません。 SQL Server 2005 プロジェクトの場合、SQL Server の上位バージョンに接続している場合でも、SQL Server 2005 に従って変換が実行されます (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016)。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータの同期  
接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]後にスキーマが変更された場合、メタデータをサーバーと同期させることができます。  
  
**SQL Server メタデータを同期するには**  
  
-   メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーで、[**データベース**] を右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="reconnecting-to-sql-server"></a>SQL Server に再接続しています  
への接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクティブな接続が必要な場合は、に再接続する必要があります。 データベースオブジェクトをに読み込んでデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するまで、オフラインで作業することができます。  
  
に再接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]手順は、接続を確立する手順と同じです。  
  
## <a name="next-steps"></a>次のステップ  
ソースデータベースとターゲットデータベース間のマッピングをカスタマイズする場合は、「[ソースデータベースとターゲットデータベースのマッピング](mapping-source-and-target-databases-accesstosql.md)」を参照してください。次[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の手順では、データベースオブジェクトの[変換](converting-access-database-objects-accesstosql.md)を使用してデータベースオブジェクトを構文に変換します。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
