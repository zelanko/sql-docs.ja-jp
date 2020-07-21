---
title: SQL Server への接続 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4f40fd6fa88b001eaa222789d6be35b83f9bf90a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67948544"
---
# <a name="connecting-to-sql-server-sybasetosql"></a>SQL Server への接続 (SybaseToSQL)
Sybase Adaptive Server Enterprise (ASE) データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するには、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットインスタンスのいずれかに接続する必要があります。 接続すると、SSMA はインスタンス内のすべてのデータベースに関するメタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを取得し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータエクスプローラーにデータベースのメタデータを表示します。 SSMA は、接続されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いるのインスタンスに関する情報を格納しますが、パスワードは保存しません。  
  
への接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクティブな接続が必要な場合は、に再接続する必要があります。 データベースオブジェクトをに読み込んでデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するまで、オフラインで作業することができます。  
  
の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに関するメタデータは、自動的には同期されません。 代わりに、メタデータエクスプローラーで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータを更新する場合は、このトピックで後述[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]する「メタデータの同期[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」セクションの説明に従って、メタデータを手動で更新する必要があります。  
  
## <a name="required-sql-server-permissions"></a>必要な SQL Server アクセス許可  
へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続に使用するアカウントには、そのアカウントによって実行されるアクションに応じて、異なるアクセス許可が必要です。  
  
-   ASE オブジェクトを構文に[!INCLUDE[tsql](../../includes/tsql-md.md)]変換したり、から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータを更新したり、変換された構文をスクリプトに保存したりするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アカウントにのインスタンスにログインする権限が必要です。  
  
-   データベースオブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込むには、権限の最小要件は、ターゲットデータベースの**db_owner**データベースロールのメンバーシップです。  
  
-   に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを移行するには、アカウントが**sysadmin**サーバーロールのメンバーである必要があります。 これは、エージェントの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ移行パッケージを実行するために必要です。  
  
-   SSMA によって生成されたコードを実行するには、アカウントに、 **sysdb**データベースの**ssma_syb**スキーマ内のすべてのユーザー定義関数に対する**Execute**権限が必要です。 これらの関数は、ASE システム関数と同等の機能を提供し、変換されたオブジェクトによって使用されます。  
  
へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続に使用するアカウントがすべての移行タスクを実行する場合、アカウントは**sysadmin**サーバーロールのメンバーである必要があります。  
  
## <a name="establishing-a-sql-server-connection"></a>SQL Server 接続の確立  
ASE データベースオブジェクトを構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換する前に、ase データベースを移行するインスタンスへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続を確立する必要があります。  
  
接続プロパティを定義するときに、オブジェクトとデータを移行するデータベースも指定します。 このマッピングは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続した後、ASE スキーマレベルでカスタマイズできます。 詳細については、「 [SQL Server スキーマ &#40;SybaseToSQL&#41;に SYBASE ASE スキーマをマップする](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)」を参照してください。  
  
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
  
    このオプションは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再接続するときには使用できません。  
  
5.  [**認証**] ボックスで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するには、[ **Windows 認証**] を選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインを使用するには、[ **SQL Server 認証**] を選択し、ログイン名とパスワードを指定します。  
  
6.  セキュリティで保護された接続では、[**暗号化接続**] チェックボックスと [ **trustservercertificate** ] チェックボックスの2つのコントロールが追加されます。 [**暗号化接続**] をオンにした場合にのみ、[ **trustservercertificate** ] チェックボックスが表示されます。 [**暗号化接続**] がオンになっている場合 (true)、 **trustservercertificate**がオフになっている場合 (false)、SQL Server の SSL 証明書が検証されます。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 これを実現するには、証明書をクライアント側とサーバー側の両方にインストールする必要があります。  
  
7.  **[Connect]** をクリックします。  
  
**より高いバージョンの互換性**  
  
-   作成された移行プロジェクトが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 と2012、2014、および2016に接続できます。  
  
-   作成された移行プロジェクトが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あるに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]もかかわらず、より低いバージョン (たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005) に接続できない場合は、2012および2014および2016に接続できます。  
  
-   作成されたプロジェクトが 2012 SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と2014、および2016にのみ接続できます。  
  
-   より新しいバージョンの互換性は、SQL Azure では無効です。  
  
||||||||
|-|-|-|-|-|-|-|
|**プロジェクトの種類 Vs ターゲットサーバーのバージョン**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (バージョン: 1.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (バージョン:10 .x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 <br />(バージョン: 2.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(バージョン:13. x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|はい|はい|はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||はい|はい|はい|はい||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||はい|はい|はい||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||はい|はい|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||はい||  
|SQL Azure||||||はい|  
  
> [!IMPORTANT]
> データベースオブジェクトの変換は、プロジェクトの種類に従って実行されますが、接続して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いるのバージョンによっては実行されません。 2005プロジェクトの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合は、より上位[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016) に接続している場合でも、変換は2005に従って実行されます。  
  
## <a name="reconnecting-to-sql-server"></a>SQL Server に再接続しています  
への接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、サーバーへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクティブな接続が必要な場合は、に再接続する必要があります。 オフラインで作業するには、メタデータを更新し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースオブジェクトをに読み込んで、データを移行します。  
  
に再接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]手順は、接続を確立する手順と同じです。  
  
## <a name="synchronizing-sql-server-metadata"></a>SQL Server メタデータの同期  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースに関するメタデータは自動的に更新されません。 メタデータエクスプローラー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のメタデータは、最初に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続したとき、または前回手動でメタデータを更新したときのメタデータのスナップショットです。 すべてのデータベース、または任意の1つのデータベースまたはデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを同期するには**  
  
1.  に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続されていることを確認します。  
  
2.  メタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データエクスプローラーで、更新するデータベースまたはデータベーススキーマの横にあるチェックボックスをオンにします。  
  
    たとえば、すべてのデータベースのメタデータを更新するには、[**データベース**] の横にあるチェックボックスをオンにします。  
  
3.  [データベース] または個々のデータベースまたはデータベーススキーマを右クリックし、[**データベースとの同期**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   ASE データベース、スキーマ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース、およびスキーマ間のマッピングをカスタマイズする場合は、「 [SQL Server スキーマ &#40;SybaseToSQL&#41;への Sybase ASE スキーマのマッピング](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)」を参照してください。  
  
-   プロジェクトの構成オプションをカスタマイズする場合は、「 [SybaseToSQL&#41;&#40;プロジェクトオプションを設定](../../ssma/sybase/setting-project-options-sybasetosql.md)する」を参照してください。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズする場合は、「 [SYBASE ASE と SQL Server のデータ型 &#40;SybaseToSQL&#41;にマップ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)する」を参照してください。  
  
-   これらのいずれかを実行する必要がない場合は、Sybase ASE データベースオブジェクトの定義をオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]定義に変換できます。 詳細については、「 [SYBASE ASE データベースオブジェクトの &#40;SybaseToSQL&#41;の変換](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
