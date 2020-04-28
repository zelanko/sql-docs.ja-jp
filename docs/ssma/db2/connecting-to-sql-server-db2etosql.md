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
ms.openlocfilehash: 7ab4c1f691820fb19dde7a3e3166abc2ff065b18
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68126641"
---
# <a name="connecting-to-sql-server-db2etosql"></a>SQL Server に接続しています (DB2eToSQL)
DB2 データベースを2012、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL DB に移行するには、これらの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットインスタンスのいずれかに接続する必要があります。 接続すると、SSMA はインスタンス内のすべてのデータベースに関するメタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを取得し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いるのインスタンスに関する情報を格納しますが、パスワードは保存しません。  
  
への接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクティブな接続が必要な場合は、に再接続する必要があります。 データベースオブジェクトをに読み込んでデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するまで、オフラインで作業することができます。  
  
の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに関するメタデータは、自動的には同期されません。 代わりに、メタデータエクスプローラーで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータを更新するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータを手動で更新する必要があります。 詳細については、このトピック[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で後述する「メタデータの同期」を参照してください。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server アクセス許可  
へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続に使用するアカウントには、アカウントが実行するアクションに応じて、異なるアクセス許可が必要です。  
  
-   DB2 オブジェクトを構文に[!INCLUDE[tsql](../../includes/tsql-md.md)]変換したり、から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータを更新したり、変換された構文をスクリプトに保存したりするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アカウントがのインスタンスにログオンする権限を持っている必要があります。  
  
-   データベースオブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込むには、アカウントが**sysadmin**サーバーロールのメンバーである必要があります。 これは、CLR アセンブリをインストールするために必要です。  
  
-   に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを移行するには、アカウントが**sysadmin**サーバーロールのメンバーである必要があります。 これは、エージェントの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ移行パッケージを実行するために必要です。  
  
-   SSMA によって生成されるコードを実行するには、対象データベースの**ssma_DB2**スキーマに含まれるすべてのユーザー定義関数に対する**Execute**権限がアカウントに必要です。 これらの関数は、DB2 システム関数と同等の機能を提供し、変換されたオブジェクトによって使用されます。  
  
へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続に使用するアカウントがすべての移行タスクを実行する場合、アカウントは**sysadmin**サーバーロールのメンバーである必要があります。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server 接続の確立  
DB2 データベースオブジェクトを構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換する前に、db2 データベースの移行先となる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続した後、DB2 スキーマレベルでカスタマイズできます。 詳細については、「 [DB2 スキーマを SQL Server スキーマ &#40;DB2ToSQL&#41;にマップする](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md)」を参照してください。  
  
> [!IMPORTANT]  
> に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続する前に、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが実行されていて、接続を受け入れることができることを確認してください。  
  
**SQL Server に接続するには**  
  
1.  [**ファイル**] メニューの [ **SQL Server に接続**] を選択します。  
  
    以前にに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続していた場合、コマンド名は**SQL Server に再接続**されます。  
  
2.  [接続] ダイアログボックスで、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの名前を入力または選択します。  
  
    -   ローカルコンピューター上の既定のインスタンスに接続している場合は、 **localhost**またはドット (**.**) を入力できます。  
  
    -   別のコンピューター上の既定のインスタンスに接続している場合は、コンピューターの名前を入力します。  
  
    -   別のコンピューター上の名前付きインスタンスに接続している場合は、コンピューター名の後に円記号を入力し、インスタンス名を入力します (例、myの myinstance)。  
  
3.  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが既定以外のポートで接続を受け入れるように構成されている場合は、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **サーバーポート**] ボックスに接続に使用するポート番号を入力します。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定のインスタンスの場合、既定のポート番号は1433です。 名前付きインスタンスの場合、SSMA は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスからポート番号の取得を試みます。  
  
4.  [**データベース**] ボックスに、ターゲットデータベースの名前を入力します。  
  
    このオプションは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再接続する場合は使用できません。  
  
5.  [**認証**] ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するには、[ **Windows 認証**] を選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインを使用するには、[ **SQL Server 認証**] を選択し、ログイン名とパスワードを入力します。  
  
6.  セキュリティで保護された接続では、[**暗号化接続**] チェックボックスと [ **trustservercertificate** ] チェックボックスの2つのコントロールが追加されます。 [**暗号化接続**] をオンにした場合にのみ、[ **trustservercertificate** ] チェックボックスが表示されます。 [**暗号化接続**] がオンになっている場合 (true)、 **trustservercertificate**がオフになっている場合 (false)、SQL Server の SSL 証明書が検証されます。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するには、証明書をクライアント側とサーバー側の両方にインストールする必要があります。  
  
7.  **[Connect]** をクリックします。  
  
**より高いバージョンの互換性**  
  
-   作成された移行プロジェクトが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 と2012、2014、および2016に接続できます。  
  
-   作成された移行プロジェクトが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あるに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]もかかわらず、より低いバージョン (たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005) に接続できない場合は、2012および2014および2016に接続できます。  
  
-   作成されたプロジェクトが 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server 場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 および2014および2016に接続できます。  
  
||||||  
|-|-|-|-|-|  
|**プロジェクトの種類 Vs ターゲットサーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 <br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(バージョン:13. x)|Azure SQL DB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014|||はい||  
|Azure SQL DB||||はい|  
  
> [!IMPORTANT]  
> データベースオブジェクトの変換は、プロジェクトの種類に従って実行されますが、接続して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いるのバージョンによっては実行されません。 2012、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016、または Azure SQL DB の場合。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータの同期  
データベースに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]関するメタデータは自動的に更新されません。 メタデータエクスプローラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のメタデータは、最初に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続したとき、または前回手動でメタデータを更新したときのメタデータのスナップショットです。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続されていることを確認します。  
  
2.  メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[**データベース**] の横にあるチェックボックスをオンにします。  
  
3.  [データベース]、または個々のデータベースまたはデータベーススキーマを**右クリックし**、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   DB2 スキーマと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースおよびスキーマ間のマッピングをカスタマイズするには、「 [db2 スキーマを SQL Server スキーマ &#40;DB2ToSQL&#41;にマッピング](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md)する」を参照してください。  
  
-   プロジェクトの構成オプションをカスタマイズするには、「[プロジェクトの設定 &#40;変換&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)および関連するセクション」を参照してください。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [DB2 と SQL Server のデータ型 &#40;DB2ToSQL&#41;にマッピング](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)する」を参照してください。  
  
-   これらのタスクを実行する必要がない場合は、DB2 データベースオブジェクト定義をオブジェクト定義に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換できます。 詳細については、「 [DB2 スキーマ &#40;DB2ToSQL&#41;の変換](../../ssma/db2/converting-db2-schemas-db2tosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[DB2 データベースを SQL Server &#40;DB2ToSQL&#41;に移行する](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
