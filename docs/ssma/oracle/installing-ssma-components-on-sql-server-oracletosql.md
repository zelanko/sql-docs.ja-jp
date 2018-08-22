---
title: SQL Server (OracleToSQL) での SSMA コンポーネントのインストール |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: d69ff9c07fe59edfd4aa0a4b8dc7357e43caefb5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "40396356"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>SQL Server での SSMA コンポーネントのインストール (OracleToSQL)
SSMA のインストール、に加えて必要がありますもコンポーネントをインストールする実行しているコンピューターで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 これらのコンポーネントには、データの移行、およびサーバー間の接続を有効にする Oracle プロバイダーをサポートする SSMA 拡張パックが含まれます。  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA for Oracle の拡張機能パック  
SSMA の拡張機能パックでは、データベースを追加します。 **sysdb**と**ssmatesterdb**、のインスタンスを指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 データベース**sysdb**テーブルとデータを移行するために必要なストアド プロシージャと Oracle システムの機能をエミュレートするユーザー定義関数が含まれています。 **Ssmatesterdb**データベースには、テーブルとテスト担当者のコンポーネントに必要な手順が含まれています。  
  
データを移行する場合にも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、SSMA 作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブのデータを移行するサーバー側のデータ移行のエンジンを使用するとします。  
  
### <a name="prerequisites"></a>前提条件  
SSMA for Oracle サーバー コンポーネントをインストールする前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システムが、次の要件を満たしていることを確認します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがインストールされます。 SSMA では、SQL Server 2008 Express Edition はサポートされていません。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows インストーラー 3.1 またはそれ以降のバージョン。  
  
-   Oracle クライアント プロバイダーまたは、OLE DB provider for Oracle、および移行する Oracle データベースに接続します。 Oracle 製品メディアまたは Oracle の Web サイトからプロバイダーをインストールすることができます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスをインストール中に実行する必要があります。 インスタンスの一覧を設定するために使用がこの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ ウィザードでします。 無効にすることができます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスのインストール後にします。  
  
    > [!NOTE]  
    > 場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されているが、まだ、セットアップでインスタンスの一覧表示されない、UDP ポート 1434 のブロックを解除する必要があります。 Windows ファイアウォールを使用するには、ポートに一時的にブロックを解除するか、Windows ファイアウォールを一時的に無効にすることができます。 ウイルス対策ソフトウェアを一時的に無効にすることもあります。 インストール後にファイアウォールやウイルス対策ソフトウェアを有効にしてください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックをインストールします。  
拡張機能パックをインストールするとデータを移行する前にいつ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、メンバーである、 **sysadmin**サーバー ロールのインスタンスを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
**拡張機能パックをインストールするには**  
  
1.  この手順をまだ行っていないことは場合、は、SSMA の Zip ファイルからすべてのファイルを抽出します。  
  
    、WinZip があるのバージョンに応じていずれか、ファイルをダブルクリックまたはファイルを右クリックして選択**すべて展開**または**WinZip で開く**します。 ファイルを抽出する WinZip のユーザー インターフェイスの指示に従います。  
  
2.  Oracle の拡張機能パックには、SSMA をコピーします。*n*します。Install.exe、場所*n*を実行しているコンピューターに、ビルド番号は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
3.  Oracle の拡張機能パックの SSMA をダブルクリックします。*n*します。Install.exe します。  
  
4.  [ようこそ] ページで、次のようにクリックします。**次**します。  
  
5.  使用許諾契約書 ページで、ライセンス契約を読みます。 同意する場合は、選択、 **、使用許諾契約書に同意**チェック ボックスをオンにし**次**。  
  
6.  セットアップの種類の選択 ページで、次のようにクリックします。**標準**します。  
  
7.  準備完了 [インストール] ページで、をクリックして**インストール**します。  
  
8.  最初のステップのインストール ページの完了 で、をクリックして**次**します。  
  
    インスタンスを選択する、新しいダイアログ ボックスが表示されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の拡張機能パックのインストール。  
  
9. インスタンスを選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Oracle のスキーマを移行およびする をクリックし、**次**。  
  
    既定のインスタンスには、コンピューターと同じ名前があります。 名前付きインスタンスの後に、円記号とインスタンス名が指定されます。  
  
10. [接続] ページで、認証方法を選択し、順にクリックします**次**します。  
  
    Windows 認証は、Windows 資格情報を使用してのインスタンスにログオンしようとする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 選択した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を入力する必要があります、認証、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン名とパスワード。  
  
11. 次のページで次のように選択します。**ユーティリティ データベースのインストール** *n*ここで、 *n* 、バージョン番号は、順にクリックします**次**します。  
  
    **Sysdb**データベースが作成され、ユーザー定義関数とストアド プロシージャは、そのデータベースに作成されます。  
  
    場合**テスター データベースのインストール**オプションがオンになって、テスト担当者**ssmatesterdb**データベースが作成されます。  
  
12. 別のインスタンスにユーティリティをインストールする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を選択します**はい**、順にクリックします**次**します。 または、をクリックしてウィザードを終了するには、**いいえ**します。  
  
13. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または sqlcmd ユーティリティを使用して CLR を有効にするのには、次のスクリプトを実行します。  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    SSMA に接続するときに、次のエラーを受信は CLR が有効でない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    SSMA は、拡張機能パックのアセンブリのバージョン情報を取得できませんでした。 データベース サーバーで、拡張機能パックを再インストールします。  
  
### <a name="sql-server-database-objects"></a>SQL Server データベース オブジェクト  
拡張機能パックをインストールした後を参照してください、 **ssma_oracle.bcp_migration_packages** 、テーブル、 **ssma_oracle.db_storage**テーブル、および**ssma_oracle.db_error_list**テーブルに、 **sysdb**データベース。 多くのストアド プロシージャおよびユーザー定義関数にも表示されます、 **ssma_oracle**スキーマ。  
  
データを移行するたびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、SSMA を作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブ。 これらのジョブの名前は**ssma_oracle データ移行パッケージ {GUID}** に表示し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエージェント ノード[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Jobs フォルダーでします。  
  
## <a name="see-also"></a>参照  
[SSMA for Oracle クライアントのインストール&#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
