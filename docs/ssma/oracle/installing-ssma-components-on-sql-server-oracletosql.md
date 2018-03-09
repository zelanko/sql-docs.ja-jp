---
title: "SQL Server (OracleToSQL) へ SSMA コンポーネントのインストール |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 76880266efb8c38bffdaa4223e49822c6d3b0778
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>SQL server (OracleToSQL) SSMA コンポーネントのインストール
SSMA をインストールするだけでなくする必要がありますコンポーネントもインストールを実行しているコンピューターで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これらのコンポーネントには、データの移行、およびサーバーからサーバーへの接続を有効にする Oracle プロバイダーをサポートする、SSMA 拡張機能パックが含まれます。  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA for Oracle の拡張機能パック  
SSMA 拡張機能パックには、データベースが追加されて**sysdb**と**ssmatesterdb**のインスタンスを指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 データベース**sysdb**テーブルとデータを移行するために必要なストアド プロシージャと Oracle システムの機能をエミュレートするユーザー定義関数が含まれます。 **Ssmatesterdb**データベースには、テーブルと、テスター コンポーネントに必要な手順が含まれています。  
  
データを移行する場合にも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA 作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント ジョブ、データ移行のサーバー側のデータ移行のエンジンを使用するとします。  
  
### <a name="prerequisites"></a>Prerequisites  
SSMA for Oracle サーバー コンポーネントをインストールする前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]システムが、次の要件を満たしていることを確認します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンスがインストールされます。 SSMA は、SQL Server 2008 Express Edition をサポートしていません。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー 3.1 以降。  
  
-   Oracle クライアント プロバイダーまたは、OLE DB provider for Oracle、および移行する Oracle データベースに接続します。 プロバイダーは、Oracle 製品メディアまたは Oracle Web サイトからインストールできます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスをインストール中に実行する必要があります。 インスタンスの一覧を設定するのに使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]セットアップ ウィザードでします。 無効にすることができます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスのインストール後にします。  
  
    > [!NOTE]  
    > 場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスが実行されているが、まだ、セットアップ時にインスタンスの一覧表示されない、UDP ポート 1434 のブロックを解除する必要があります。 Windows ファイアウォールを使用するには、ポートに一時的にブロックを解除するか、Windows ファイアウォールを一時的に無効にすることができます。 ウイルス対策ソフトウェアを一時的に無効にすることもあります。 インストール後にファイアウォールとウイルス対策ソフトウェアを有効にすることを確認してください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックをインストールします。  
拡張機能パックをインストールするとデータを移行する前にいつでも[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、メンバーである、 **sysadmin**サーバーの役割のインスタンスを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
**拡張機能パックをインストールするには**  
  
1.  まだ行ってこのいない場合は、SSMA Zip ファイルからすべてのファイルを抽出します。  
  
    バージョンによっては、WinZip がある場合のいずれか、ファイルをダブルクリックまたはファイルを右クリックして選択できます**すべて展開**または**WinZip で開いて**です。 ファイルを抽出する WinZip ユーザー インターフェイスの手順に従います。  
  
2.  Oracle の拡張機能パックには、SSMA をコピーします。*n*.Install.exe、場所 *n* を実行しているコンピューターに、ビルド番号は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
3.  Oracle の拡張機能パックには、SSMA をダブルクリックします。*n*.Install.exe です。  
  
4.  [ようこそ] ページで、をクリックして**次**です。  
  
5.  使用許諾契約書 ページで、使用許諾契約書を読み取る。 同意する場合は、選択、**ライセンス契約の条項に同意**チェック ボックスをクリックして**次**です。  
  
6.  セットアップの種類の選択 ページで、をクリックして**標準**です。  
  
7.  準備完了 [インストール] ページで、をクリックして**インストール**です。  
  
8.  最初のステップのインストール ページの完了 で、をクリックして**次**です。  
  
    インスタンスを選択して、新しいダイアログ ボックスが表示されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]拡張機能パックをインストールするためです。  
  
9. インスタンスを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]場所 Oracle スキーマを移行し をクリックして**次**です。  
  
    既定のインスタンスには、コンピューターと同じ名前があります。 名前付きインスタンスの後に、円記号とインスタンス名が指定されます。  
  
10. [接続] ページで、認証方法を選択し、をクリックして**次**です。  
  
    Windows 認証は、Windows 資格情報を使用してのインスタンスにログオンしよう[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を入力する必要があります、認証、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログイン名とパスワード。  
  
11. 次のページで次のように選択します。**ユーティリティ データベースのインストール**  *n*ここで、  *n* バージョン番号は、[] をクリック**次**です。  
  
    **Sysdb**データベースが作成され、ユーザー定義関数とストアド プロシージャは、そのデータベースに作成されます。  
  
    場合**Tester データベースのインストール**オプションがオンになって、テスター **ssmatesterdb**データベースが作成されます。  
  
12. 別のインスタンスにユーティリティをインストールする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **[はい]**、順にクリック**[次へ]**です。 またはをクリックしてウィザードを終了するには、**いいえ**です。  
  
13. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]または sqlcmd ユーティリティを使用して CLR を有効にするのには、次のスクリプトを実行します。  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    SSMA に接続するときに、次のエラーを受信は CLR が有効でない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
    SSMA は、拡張機能パックのアセンブリのバージョン情報を取得できませんでした。 データベース サーバーで、拡張機能パックを再インストールします。  
  
### <a name="sql-server-database-objects"></a>SQL Server データベース オブジェクト  
拡張機能パックをインストールすると後、を参照してください、 **ssma_oracle.bcp_migration_packages** 、テーブル、 **ssma_oracle.db_storage**テーブル、および**ssma_oracle.db_error_list**テーブルに、 **sysdb**データベース。 多くのストアド プロシージャおよびユーザー定義関数にも表示されます、 **ssma_oracle**スキーマです。  
  
データを移行するたびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA を作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント ジョブ。 これらのジョブの名前は**ssma_oracle データ移行パッケージ {GUID}**に表示されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のエージェント ノード[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]Jobs フォルダーでします。  
  
## <a name="see-also"></a>参照  
[Oracle クライアント &#40;OracleToSQL"&"#41 です。 SSMA をインストールします。](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[SQL Server &#40;OracleToSQL&#41; への Oracle データベースの移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
