---
title: "SQL Server (SybaseToSQL) へ SSMA コンポーネントのインストール |Microsoft ドキュメント"
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
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 716a45f706292e3011ed5c8c2871bfc8176fb5a5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>SQL server (SybaseToSQL) SSMA コンポーネントのインストール
サーバー側のデータ移行を使用するためには、SSMA をインストール、に加えて必要がありますもコンポーネントをインストールするを実行しているコンピューターで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これらのコンポーネントには、SSMA 拡張機能パックには、データの移行、および Sybase のプロバイダーをサーバーからサーバーへの接続を有効にするサポートが含まれます。  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA for Sybase の拡張機能パック  
SSMA 拡張機能パックには、データベースが追加されて**sysdb**と**ssmatesterdb_syb**のインスタンスを指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 **Sysdb**データベースには、テーブルとデータを移行するために必要なストアド プロシージャが含まれています。 **Ssmatester_syb**データベースには、スキーマが含まれています。 **ssma_sybase_utilities**、SSMA tester コンポーネントによって使用されるオブジェクト (テーブル、トリガー、ビュー) が作成されました。  
  
データを移行する場合にも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA 作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント ジョブ、データ移行のサーバー側のデータ移行のエンジンを使用するとします。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックをインストールします。  
拡張機能パックをインストールするとデータを移行する前にいつでも[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、インスタンスで sysadmin サーバー ロールのメンバーである[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
**拡張機能パックをインストールするには**  
  
1.  Sybase 拡張機能パックには、SSMA をコピーします。*n*.Install.exe、場所 *n* を実行しているコンピューターに、ビルド番号は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
2.  Sybase 拡張機能パックには、SSMA をダブルクリックします。*n*.Install.exe です。  
  
3.  [ようこそ] ページで、をクリックして**次**です。  
  
4.  使用許諾契約書 ページで、使用許諾契約書を読み取る。 同意する場合は、選択、**ライセンス契約の条項に同意**チェック ボックスをクリックして**次**です。  
  
5.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
6.  準備完了 [インストール] ページで、をクリックして**インストール**です。  
  
7.  最初のステップのインストール ページの完了 で、をクリックして**次**です。  
  
    インスタンスを選択して、新しいダイアログ ボックスが表示されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]拡張機能パックをインストールするためです。  
  
8.  インスタンスを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]場所 ASE データベースを移行し、をクリックして**次**です。  
  
    既定のインスタンスには、コンピューターと同じ名前があります。 名前付きインスタンスの後に、円記号とインスタンス名が指定されます。  
  
9. 接続パラメーター ページで、認証方法を選択し、をクリックして**次**です。  
  
    Windows 認証は、Windows 資格情報を使用してのインスタンスにログオンしよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を入力する必要があります、認証、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログイン名とパスワード。  
  
10. [サーバーの管理] ページで、**ユーティリティ データベースのインストール**  *n*ここで、  *n* バージョン番号は、をクリックして**次**です。  
  
    **Sysdb**データベースが作成され、そのデータベースにストアド プロシージャが作成されます。  
  
    場合**Tester データベースのインストール**オプションがオンになって、テスター **ssmatesterdb_syb**データベースが作成されます。  
  
11. 別のインスタンスにユーティリティをインストールする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**インスタンスに戻る**、順にクリック**[次へ]**です。 またはをクリックしてウィザードを終了するには、**終了**です。  
  
### <a name="sql-server-database-objects"></a>SQL Server データベース オブジェクト  
「」を参照は、拡張機能パックをインストールした後、 **ssma_syb.bcp_migration_packages**テーブルに、 **sysdb**データベース。 次のストアド プロシージャも表示されます。  
  
-   **bcp_clean_migration_data**  
  
-   **bcp_ensure_message_table**  
  
-   **bcp_insert_new_message**  
  
-   **bcp_post_process**  
  
-   **bcp_read_new_migration_messages**  
  
-   **bcp_save_migration_package**  
  
-   **bcp_smart_truncate**  
  
-   **bcp_start_migration_process**  
  
-   **get_jobstep_info**  
  
-   **stop_agent_process**  
  
データを移行するたびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA を作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント ジョブ。 これらのジョブの名前は**ssma_syb データ移行パッケージ {GUID}**に表示されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のエージェント ノード[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]Jobs フォルダーでします。  
  
## <a name="sybase-providers"></a>Sybase プロバイダー  
ASE からデータを移行する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ASE 間で直接 SQL Azure データの移行と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure です。 これを経由しない SSMA データ移行の速度が低下はこのためです。  
  
### <a name="installing-the-sybase-providers"></a>Sybase プロバイダーをインストールします。  
次の手順では、Sybase プロバイダーをインストールするため、基本的なインストール手順を説明します。 正確な手順については、Sybase セットアップ プログラムのバージョンによって異なります。  
  
> [!IMPORTANT]  
> セットアップ プログラムを実行する前に、ライセンス認証契約に違反していないことを確認します。  
  
1.  Sybase ASE セットアップ プログラムを実行します。  
  
2.  カスタム セットアップを選択します。  
  
3.  [機能の選択] ページで、ODBC、OLE DB および ADO.NET データ プロバイダーを選択します。  
  
4.  選択した機能を確認し、をクリックして**完了**データ プロバイダーをインストールします。  
  
## <a name="see-also"></a>参照  
[SSMA の Sybase クライアント &#40; のインストールSybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

