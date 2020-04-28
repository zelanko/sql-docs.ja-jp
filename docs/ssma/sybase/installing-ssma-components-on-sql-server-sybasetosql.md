---
title: SQL Server での SSMA コンポーネントのインストール (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1fbc3a8f74b21bd5a53bdd874b5c41ef522e29f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029008"
---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>SQL Server での SSMA コンポーネントのインストール (SybaseToSQL)
SSMA のインストールに加えて、サーバー側のデータ移行を使用するために、を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターにコンポーネントをインストールする必要もあります。 これらのコンポーネントには、データの移行をサポートする SSMA 拡張パックと、サーバーとサーバー間の接続を有効にする Sybase プロバイダーが含まれます。  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA for Sybase Extension Pack  
SSMA 拡張パックは、指定されたインスタンスに**ssmatesterdb_syb**データベース、 **sysdb** 、および ssmatesterdb_syb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を追加します。 **Sysdb**データベースには、データの移行に必要なテーブルとストアドプロシージャが含まれています。 **Ssmatester_syb**データベースには、ssma tester コンポーネントによって使用されるオブジェクト (テーブル、トリガー、ビュー) が作成されるスキーマ**ssma_sybase_utilities**が含まれています。  
  
また、データをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するときに、サーバー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]側のデータ移行エンジンを使用してデータを移行するときに、ssma によってエージェントジョブが作成されます。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックのインストール  
にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に、いつでも拡張機能パックをインストールできます。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの sysadmin サーバーロールのメンバーである必要があります。  
  
**拡張機能パックをインストールするには**  
  
1.  SSMA for Sybase Extension Pack をコピーします。*n*。を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターに、.exe ( *n*はビルド番号) をインストールします。  
  
2.  [SSMA for Sybase Extension Pack] をダブルクリックします。*n*。.Exe をインストールします。  
  
3.  [ようこそ] ページで **[次へ]** をクリックします。  
  
4.  [使用許諾契約書] ページで、使用許諾契約書を読みます。 同意する場合は、[**使用許諾契約書に同意し**ます] チェックボックスをオンにして、[**次へ**] をクリックします。  
  
5.  [セットアップの種類の選択] ページで、[**標準**] をクリックします。  
  
6.  [インストールの準備完了] ページで、[**インストール**] をクリックします。  
  
7.  [インストールの最初の手順を完了しました] ページで、[**次へ**] をクリックします。  
  
    新しいダイアログボックスが表示されます。このダイアログボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張機能パックのインストール用のインスタンスを選択します。  
  
8.  ASE データベースを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するのインスタンスを選択し、[**次へ**] をクリックします。  
  
    既定のインスタンスには、コンピューターと同じ名前が付けられています。 名前付きインスタンスの後には、円記号とインスタンス名が続きます。  
  
9. [接続パラメーター] ページで、認証方法を選択し、[**次へ**] をクリックします。  
  
    Windows 認証では、Windows 資格情報を使用しての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにログオンしようとします。 [認証] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を選択した場合は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ログイン名とパスワードを入力する必要があります。  
  
10. [サーバーの管理] ページで、[**ユーティリティデータベース** *n*をインストールする] を選択します。 *n*はバージョン番号です。次に、[**次へ**] をクリックします。  
  
    **Sysdb**データベースが作成され、ストアドプロシージャがそのデータベースに作成されます。  
  
    [ **Tester データベースをインストール**する] オプションがオンになっている場合、 **ssmatesterdb_syb**データベースが作成されます。  
  
11. の別の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにユーティリティをインストールするには、[**インスタンスに戻る**] を選択し、[**次へ**] をクリックします。 または、ウィザードを終了するには、[**終了**] をクリックします。  
  
### <a name="sql-server-database-objects"></a>SQL Server データベースオブジェクト  
拡張機能パックをインストールすると、 **sysdb**データベースに**ssma_syb bcp_migration_packages**テーブルが表示されます。 次のストアドプロシージャも表示されます。  
  
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
  
に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを移行するたびに、ssma によっ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]てエージェントジョブが作成されます。 これらのジョブには**ssma_syb データ移行パッケージ {GUID}** という名前が付け[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]られ、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [ジョブ] フォルダーのの [エージェント] ノードに表示されます。  
  
## <a name="sybase-providers"></a>Sybase プロバイダー  
ASE から sql Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを移行すると、ase と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sql azure の間でデータが直接移行されます。 SSMA を経由することはありません。これは、データ移行の速度が低下するためです。  
  
### <a name="installing-the-sybase-providers"></a>Sybase プロバイダーのインストール  
次の手順では、Sybase プロバイダーをインストールするための基本的なインストール手順について説明します。 正確な手順は、Sybase セットアッププログラムのバージョンによって異なります。  
  
> [!IMPORTANT]  
> セットアッププログラムを実行する前に、ライセンス契約に違反していないことを確認してください。  
  
1.  Sybase ASE セットアッププログラムを実行します。  
  
2.  [カスタムセットアップ] を選択します。  
  
3.  [機能の選択] ページで、ODBC、OLE DB および ADO.NET データプロバイダーを選択します。  
  
4.  選択した機能を確認し、[**完了**] をクリックしてデータプロバイダーをインストールします。  
  
## <a name="see-also"></a>参照  
[SSMA for Sybase Client &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
