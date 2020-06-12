---
title: SQL Server での SSMA コンポーネントのインストール (OracleToSQL) |Microsoft Docs
description: Oracle データベースの変換をサポートするために SQL Server を実行しているコンピューターに SSMA 拡張パックと Oracle プロバイダーをインストールする方法について説明します。
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
ms.openlocfilehash: 3df476f5fa14840af0b023253b79702ed7a85c8a
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292932"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>SQL Server での SSMA コンポーネントのインストール (OracleToSQL)

SSMA のインストールに加えて、を実行しているコンピューターにコンポーネントをインストールする必要もあり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 これらのコンポーネントには、データ移行をサポートする SSMA extension pack と、サーバー間接続を有効にする Oracle プロバイダーが含まれます。  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA for Oracle extension pack

SSMA 拡張パックは、指定されたインスタンスに**sysdb**および**ssmatesterdb**データベースを追加し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 データベース**sysdb**には、データを移行するために必要なテーブルとストアドプロシージャ、および Oracle システム関数をエミュレートするユーザー定義関数が含まれています。 **Ssmatesterdb**データベースには、Tester コンポーネントに必要なテーブルとプロシージャが含まれています。  
  
また、データをに移行するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、サーバー側のデータ移行エンジンを使用してデータを移行するときに、ssma によって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントジョブが作成されます。  
  
### <a name="prerequisites"></a>前提条件

SSMA for Oracle サーバーコンポーネントをにインストールする前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムが次の要件を満たしていることを確認してください。  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスはインストールされています。 SSMA は SQL Server 2008 Express Edition をサポートしていません。
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows インストーラー3.1 以降のバージョン。  
  
- Oracle クライアントプロバイダーまたは OLE DB provider for Oracle、および移行する Oracle データベースへの接続。 プロバイダーは、Oracle 製品メディアまたは Oracle Web サイトからインストールできます。  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール中に Browser サービスが実行されている必要があります。 これは、セットアップウィザードでのインスタンスの一覧を設定するために使用され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 インストール後に Browser サービスを無効にすることができ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
    > [!NOTE]  
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser サービスが実行されていても、セットアップにインスタンスの一覧が表示されない場合は、UDP ポート1434のブロックを解除する必要があります。 Windows ファイアウォールを使用して、一時的にポートのブロックを解除することも、Windows ファイアウォールを一時的に無効にすることもできます。 また、ウイルス対策ソフトウェアを一時的に無効にすることが必要になる場合もあります。 インストール後に、ファイアウォールとウイルス対策ソフトウェアが有効になっていることを確認してください。  
  
### <a name="installing-the-extension-pack"></a>拡張機能パックのインストール

にデータを移行する前に、拡張機能パックをいつでもインストールでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
> [!IMPORTANT]  
> 拡張機能パックをインストールするには、のインスタンスの**sysadmin**サーバーロールのメンバーである必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
**拡張機能パックをインストールするには**
  
1. SSMA Zip ファイルからすべてのファイルを抽出していない場合は、展開します。  
  
    使用している WinZip のバージョンに応じて、ファイルをダブルクリックするか、ファイルを右クリックして [**すべて展開**] または [ **winzip で開く**] を選択します。 WinZip のユーザーインターフェイスに記載されている手順に従って、ファイルを抽出します。  
  
2. **Ssma For Oracle Extension Pack をコピーします。*n*.Install.exe** ( *n*はビルド番号) で、を実行しているコンピューターを指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
3. [ **Ssma For Oracle Extension Pack] をダブルクリックします。*n*.Install.exe**。  
  
4. **[ようこそ]** ページで **[次へ]** をクリックします。  
  
5. [使用許諾**契約書**] ページで、使用許諾契約書を読みます。 同意する場合は、[**使用許諾契約書に同意し**ます] チェックボックスをオンにし、[**次へ**] を選択します。  
  
6. [**セットアップの種類の選択**] ページで、[**標準**] を選択します。  
  
7. [**インストールの準備完了**] ページで、[**インストール**] を選択します。  
  
8. [**インストールの最初の手順を完了しまし**た] ページで、[**次へ**] を選択します。  
  
    新しいダイアログボックスが表示されます。このダイアログボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張機能パックのインストール用のインスタンスを選択します。  
  
9. Oracle スキーマを移行するインスタンスを選択 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] し、[**次へ**] を選択します。  
  
    既定のインスタンスには、コンピューターと同じ名前が付けられています。 名前付きインスタンスの後には、円記号とインスタンス名が続きます。  
  
10. [接続] ページで、[認証方法] を選択し、[**次へ**] を選択します。  
  
    Windows 認証では、Windows 資格情報を使用してのインスタンスにサインインしようとし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [認証] を選択した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン名とパスワードを入力する必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
11. 次のページで、[ **Install Utilities Database** *n*] を選択します。ここで、 *n*はバージョン番号です。次に、[**次へ**] を選択します。  
  
    **Sysdb**データベースが作成され、そのデータベースにユーザー定義関数およびストアドプロシージャが作成されます。  
  
    [**テスト担当者データベースをインストール**する] オプションがオンになっている場合は、tester **ssmatesterdb**データベースが作成されます。  
  
12. の別のインスタンスにユーティリティをインストールするには、[はい] を選択し、[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **次へ**] を選択します。または、ウィザードを終了するには、[**いいえ**] を選択します。 **Yes**  
  
13. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または sqlcmd ユーティリティを使用して、次のスクリプトを実行して CLR を有効にします。  
  
    ```
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```

    CLR が有効になっていない場合、SSMA がに接続すると、次のエラーが表示され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
    SSMA は、拡張パックのアセンブリのバージョン情報を取得できませんでした。 データベースサーバーに拡張パックを再インストールしてください。  
  
### <a name="sql-server-database-objects"></a>SQL Server データベースオブジェクト  

拡張機能パックをインストールすると、 **ssma_oracle bcp_migration_packages**テーブルが**sysdb**データベースに表示されます。

にデータを移行するたびに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ssma によってエージェントジョブが作成さ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。 これらのジョブには**ssma_oracle データ移行パッケージ {GUID}** という名前が付けられ、[ジョブ] フォルダーのの [エージェント] ノードに表示され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。  
  
## <a name="see-also"></a>関連項目

[SSMA for Oracle Client &#40;OracleToSQL&#41;のインストール](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Oracle データベースの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
