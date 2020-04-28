---
title: SQL Server での SSMA コンポーネントのインストール (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 10/01/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 1f0cea859e9465eebefebc061ee51107dc7844aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "71713312"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>SQL Server での SSMA コンポーネントのインストール (OracleToSQL)

SSMA のインストールに加えて、を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターにコンポーネントをインストールする必要もあります。 これらのコンポーネントには、データ移行をサポートする SSMA extension pack と、サーバー間接続を有効にする Oracle プロバイダーが含まれます。  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA for Oracle extension pack

SSMA 拡張パックは、指定されたインスタンスに**sysdb**および**ssmatesterdb**データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を追加します。 データベース**sysdb**には、データを移行するために必要なテーブルとストアドプロシージャ、および Oracle システム関数をエミュレートするユーザー定義関数が含まれています。 **Ssmatesterdb**データベースには、Tester コンポーネントに必要なテーブルとプロシージャが含まれています。  
  
また、データをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するときに、サーバー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]側のデータ移行エンジンを使用してデータを移行するときに、ssma によってエージェントジョブが作成されます。  
  
### <a name="prerequisites"></a>前提条件

SSMA for Oracle サーバーコンポーネントをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールする前に、システムが次の要件を満たしていることを確認してください。  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスはインストールされています。 SSMA は SQL Server 2008 Express Edition をサポートしていません。
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
- Oracle クライアントプロバイダーまたは OLE DB provider for Oracle、および移行する Oracle データベースへの接続。 プロバイダーは、Oracle 製品メディアまたは Oracle Web サイトからインストールできます。  
  
- インストール[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中に Browser サービスが実行されている必要があります。 これは、セットアップウィザードでの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの一覧を設定するために使用されます。 インストール後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを無効にすることができます。  
  
    > [!NOTE]  
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが実行されていても、セットアップにインスタンスの一覧が表示されない場合は、UDP ポート1434のブロックを解除する必要があります。 Windows ファイアウォールを使用して、一時的にポートのブロックを解除することも、Windows ファイアウォールを一時的に無効にすることもできます。 また、ウイルス対策ソフトウェアを一時的に無効にすることが必要になる場合もあります。 インストール後に、ファイアウォールとウイルス対策ソフトウェアが有効になっていることを確認してください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックのインストール

にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に、拡張機能パックをいつでもインストールできます。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの**sysadmin**サーバーロールのメンバーである必要があります。  
  
**拡張機能パックをインストールするには**
  
1. SSMA Zip ファイルからすべてのファイルを抽出していない場合は、展開します。  
  
    使用している WinZip のバージョンに応じて、ファイルをダブルクリックするか、ファイルを右クリックして [**すべて展開**] または [ **winzip で開く**] を選択します。 WinZip のユーザーインターフェイスに記載されている手順に従って、ファイルを抽出します。  
  
2. **Ssma For Oracle Extension Pack をコピーします。*n*。** を実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しているコンピューターに .exe ( *n*はビルド番号) をインストールします。  
  
3. [ **Ssma For Oracle Extension Pack] をダブルクリックします。*n*。.Exe をインストールします**。  
  
4. **[ようこそ]** ページで **[次へ]** をクリックします。  
  
5. [使用許諾**契約書**] ページで、使用許諾契約書を読みます。 同意する場合は、[**使用許諾契約書に同意し**ます] チェックボックスをオンにし、[**次へ**] を選択します。  
  
6. [**セットアップの種類の選択**] ページで、[**標準**] を選択します。  
  
7. [**インストールの準備完了**] ページで、[**インストール**] を選択します。  
  
8. [**インストールの最初の手順を完了しまし**た] ページで、[**次へ**] を選択します。  
  
    新しいダイアログボックスが表示されます。このダイアログボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張機能パックのインストール用のインスタンスを選択します。  
  
9. Oracle スキーマを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するインスタンスを選択し、[**次へ**] を選択します。  
  
    既定のインスタンスには、コンピューターと同じ名前が付けられています。 名前付きインスタンスの後には、円記号とインスタンス名が続きます。  
  
10. [接続] ページで、[認証方法] を選択し、[**次へ**] を選択します。  
  
    Windows 認証では、Windows 資格情報を使用しての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにサインインしようとします。 [認証] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を選択した場合は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ログイン名とパスワードを入力する必要があります。  
  
11. 次のページで、[ **Install Utilities Database** *n*] を選択します。ここで、 *n*はバージョン番号です。次に、[**次へ**] を選択します。  
  
    **Sysdb**データベースが作成され、そのデータベースにユーザー定義関数およびストアドプロシージャが作成されます。  
  
    [**テスト担当者データベースをインストール**する] オプションがオンになっている場合は、tester **ssmatesterdb**データベースが作成されます。  
  
12. の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別のインスタンスにユーティリティをインストールするには、[**はい**] を選択し、[**次へ**] を選択します。または、ウィザードを終了するには、[**いいえ**] を選択します。  
  
13. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または sqlcmd ユーティリティを使用して、次のスクリプトを実行して CLR を有効にします。  
  
    ```
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```

    CLR が有効になっていない場合、SSMA がに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続すると、次のエラーが表示されます。  
  
    SSMA は、拡張パックのアセンブリのバージョン情報を取得できませんでした。 データベースサーバーに拡張パックを再インストールしてください。  
  
### <a name="sql-server-database-objects"></a>SQL Server データベースオブジェクト  

拡張機能パックをインストールすると、 **ssma_oracle bcp_migration_packages**テーブルが**sysdb**データベースに表示されます。

にデータを移行するたび[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、ssma に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]よってエージェントジョブが作成されます。 これらのジョブには**ssma_oracle データ移行パッケージ {GUID}** という名前が付け[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]られ、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [ジョブ] フォルダーのの [エージェント] ノードに表示されます。  
  
## <a name="see-also"></a>関連項目

[SSMA for Oracle Client &#40;OracleToSQL&#41;のインストール](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Oracle データベースの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
