---
title: SQL Server に接続しています (DB2eToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 84c9a0a994e087314fcd8d1ae66e1bb5a79fedba
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87863656"
---
# <a name="connecting-to-sql-server-db2etosql"></a>SQL Server に接続しています (DB2eToSQL)
DB2 データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012、2014、Azure SQL Database に移行するに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、これらのターゲットインスタンスのいずれかに接続する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 接続すると、SSMA はインスタンス内のすべてのデータベースに関するメタデータ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を取得し、メタデータエクスプローラーにデータベースのメタデータを表示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 SSMA は、接続されているのインスタンスに関する情報を格納し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ますが、パスワードは保存しません。  
  
への接続 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへのアクティブな接続が必要な場合は、に再接続する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 データベースオブジェクトをに読み込んでデータを移行するまで、オフラインで作業することができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
のインスタンスに関するメタデータ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、自動的には同期されません。 代わりに、メタデータエクスプローラーでメタデータを更新するには、メタデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 手動で更新する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] このトピックで後述する「メタデータの同期」を参照してください。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server アクセス許可  
への接続に使用するアカウントには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントが実行するアクションに応じて、異なるアクセス許可が必要です。  
  
-   DB2 オブジェクトを構文に変換し [!INCLUDE[tsql](../../includes/tsql-md.md)] たり、からメタデータを更新したり、変換され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] た構文をスクリプトに保存したりするには、アカウントがのインスタンスにログオンする権限を持っている必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
-   データベースオブジェクトをに読み込むには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントが**sysadmin**サーバーロールのメンバーである必要があります。 これは、CLR アセンブリをインストールするために必要です。  
  
-   にデータを移行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントが**sysadmin**サーバーロールのメンバーである必要があります。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのデータ移行パッケージを実行するために必要です。  
  
-   SSMA によって生成されるコードを実行するには、対象データベースの**ssma_DB2**スキーマに含まれるすべてのユーザー定義関数に対する**Execute**権限がアカウントに必要です。 これらの関数は、DB2 システム関数と同等の機能を提供し、変換されたオブジェクトによって使用されます。  
  
への接続に使用するアカウント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がすべての移行タスクを実行する場合、アカウントは**sysadmin**サーバーロールのメンバーである必要があります。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server 接続の確立  
DB2 データベースオブジェクトを構文に変換する前に、DB2 データベースの移行先となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続を確立する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、に接続した後、DB2 スキーマレベルでカスタマイズでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「 [DB2 スキーマを SQL Server スキーマ &#40;DB2ToSQL&#41;にマップする](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md)」を参照してください。  
  
> [!IMPORTANT]  
> に接続する前に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、のインスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていて、接続を受け入れることができることを確認してください。  
  
**SQL Server に接続するには**  
  
1.  [**ファイル**] メニューの [ **SQL Server に接続**] を選択します。  
  
    以前にに接続していた場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、コマンド名は**SQL Server に再接続**されます。  
  
2.  [接続] ダイアログボックスで、のインスタンスの名前を入力または選択し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
    -   ローカルコンピューター上の既定のインスタンスに接続している場合は、 **localhost**またはドット (**.**) を入力できます。  
  
    -   別のコンピューター上の既定のインスタンスに接続している場合は、コンピューターの名前を入力します。  
  
    -   別のコンピューター上の名前付きインスタンスに接続している場合は、コンピューター名の後に円記号を入力し、インスタンス名を入力します (例、myの myinstance)。  
  
3.  のインスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定以外のポートで接続を受け入れるように構成されている場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [**サーバーポート**] ボックスに接続に使用するポート番号を入力します。 の既定のインスタンスの場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、既定のポート番号は1433です。 名前付きインスタンスの場合、SSMA は Browser サービスからポート番号の取得を試み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
4.  [**データベース**] ボックスに、ターゲットデータベースの名前を入力します。  
  
    このオプションは、に再接続する場合は使用できません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
5.  [**認証**] ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するには、[ **Windows 認証**] を選択します。 ログインを使用するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、[ **SQL Server 認証**] を選択し、ログイン名とパスワードを入力します。  
  
6.  セキュリティで保護された接続では、[**暗号化接続**] チェックボックスと [ **trustservercertificate** ] チェックボックスの2つのコントロールが追加されます。 [**暗号化接続**] をオンにした場合にのみ、[ **trustservercertificate** ] チェックボックスが表示されます。 [**暗号化接続**] がオンになっている場合 (true)、 **trustservercertificate**がオフになっている場合 (false)、SQL Server の SSL 証明書が検証されます。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するには、証明書をクライアント側とサーバー側の両方にインストールする必要があります。  
  
7.  **[接続]** をクリックします。  
  
**より新しいバージョンの互換性**  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 移行プロジェクトが "2005" の場合、2008と2012、2014、および2016に接続でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 移行プロジェクトが2008であるにもかかわらず、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より低いバージョン (たとえば、2005) に接続できない場合は、2012および2014および2016に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続できます。  
  
-   作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロジェクトが 2012 SQL Server 場合は、2012および2014および2016に接続できます。  
  
|プロジェクトの種類と対象サーバーのバージョン|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 <br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(バージョン:13. x)|Azure SQL データベース|  
|-|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014|||はい||  
|Azure SQL データベース||||はい|  
  
> [!IMPORTANT]  
> データベースオブジェクトの変換は、プロジェクトの種類に従って実行されますが、接続しているのバージョンによっては実行されません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016、または Azure SQL Database の場合。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータの同期  
データベースに関するメタデータ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は自動的に更新されません。 メタデータエクスプローラーのメタデータ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、最初に接続したとき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、または前回手動でメタデータを更新したときのメタデータのスナップショットです。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  に接続されていることを確認し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[**データベース**] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを**右クリックし**、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   DB2 スキーマとデータベースおよびスキーマ間のマッピングをカスタマイズするには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [db2 スキーマを SQL Server スキーマ &#40;DB2ToSQL&#41;にマッピング](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md)する」を参照してください。  
  
-   プロジェクトの構成オプションをカスタマイズするには、「[プロジェクトの設定 &#40;変換&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)および関連するセクション」を参照してください。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [DB2 と SQL Server のデータ型 &#40;DB2ToSQL&#41;にマッピング](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)する」を参照してください。  
  
-   これらのタスクを実行する必要がない場合は、DB2 データベースオブジェクト定義をオブジェクト定義に変換でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「 [DB2 スキーマ &#40;DB2ToSQL&#41;の変換](../../ssma/db2/converting-db2-schemas-db2tosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[DB2 データベースを SQL Server &#40;DB2ToSQL&#41;に移行する](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
