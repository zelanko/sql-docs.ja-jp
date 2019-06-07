---
title: ダウンロードしてインストールする
titleSuffix: Azure Data Studio
description: ダウンロードと Windows 用の Azure データ Studio のインストール、macOS、または Linux
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.custom: seodec18
ms.date: 06/06/2019
ms.reviewer: alayu; sstein
ms.openlocfilehash: 39985ea8a13b4102393434dd2ef0981fe022798f
ms.sourcegitcommit: 32dce314bb66c03043a93ccf6e972af455349377
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744142"
---
# <a name="download-and-install-azure-data-studio"></a>ダウンロードし、Azure Data Studio のインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で動作します。


ダウンロードして、最新のリリースでは、インストール、*年 6 月リリース*:

> [!NOTE]
> SQL Operations Studio から更新しているし、設定、キーボード ショートカット、またはコード スニペットを保持する場合は、次を参照してください。[ユーザー設定の移動](#move-user-settings)します。

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[ユーザーのインストーラー (推奨)](https://go.microsoft.com/fwlink/?linkid=2094100)<br>[システムのインストーラー](https://go.microsoft.com/fwlink/?linkid=2094200)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2094201)|2019 年 6 月 6日 |1.8.0|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2094202)|2019 年 6 月 6日 |1.8.0|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2094203)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2094102)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2094101)|2019 年 6 月 6日 |1.8.0|

最新のリリースに関する詳細は、次の [リリース ノート](release-notes.md) を参照してください。

## <a name="get-azure-data-studio-for-windows"></a>Windows 用 Azure Data Studio を入手します。

このリリースの[!INCLUDE[name-sos](../includes/name-sos-short.md)]標準の Windows インストーラー エクスペリエンスと、.zip ファイルが含まれています。

*ユーザー インストーラー*は必要ありません、管理者特権がのインストールとアップグレードの両方を簡略化されますのでお勧めします。 ユーザーのインストーラーは、ユーザーのローカル AppData (%%LOCALAPPDATA%%) フォルダーの下の場所は、管理者特権は必要ありません。 ユーザーのインストーラーより滑らかなバック グラウンド更新プログラムのエクスペリエンスも提供します。 詳細については、次を参照してください。 [Windows のユーザー セットアップ](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows)します。


**ユーザーのインストーラー** (推奨)

1. ダウンロードし、実行、 [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *ユーザー* Windows 用のインストーラー](https://go.microsoft.com/fwlink/?linkid=2094100)します。
2. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]のアプリを開始します。

**システムのインストーラー**

1. ダウンロードし、実行、 [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *システム*Windows 用のインストーラー](https://go.microsoft.com/fwlink/?linkid=2094200)します。
2. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]のアプリを開始します。


**zip ファイル**

1. [[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Windows .zip](https://go.microsoft.com/fwlink/?linkid=2094201) をダウンロードします。
2. ダウンロードしたファイルを参照し、展開します。
3. `\azuredatastudio-windows\azuredatastudio.exe`を実行します。


## <a name="get-azure-data-studio-for-macos"></a>MacOS 用の Azure データ Studio を入手します。

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for macOS](https://go.microsoft.com/fwlink/?linkid=2094202) をダウンロードします。
2. zip のコンテンツを展開するには、ダブルクリックします。
3. させる[!INCLUDE[name-sos](../includes/name-sos-short.md)]で使用できる、*スタート パッド*、ドラッグ*Azure データ Studio.app*を*アプリケーション*フォルダー。


## <a name="get-azure-data-studio-for-linux"></a>Linux 用 Azure Data Studio を入手します。

1. ダウンロード[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Linux を使用して、インストーラーまたは tar.gz アーカイブのいずれかで。
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2094203)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2094102)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2094101)
1. ファイルを展開し、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を起動するため、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   **Debian のインストール:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **rpm のインストール:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **tar.gz インストール:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Debian、Redhat、および Ubuntu で、依存関係が見つからないことがあります。 これらの依存関係をインストールするために、Linux のバージョンに応じて、次のコマンドを使用してください。
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-azure-data-studio"></a>Azure Data Studio をアンインストールします。

Windows インストーラーを使用して[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]をインストールした場合、他の Windows アプリケーションの削除と同じ方法でアンインストールしてください。

.zip またはその他のアーカイブから [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] をインストールした場合、ファイルを削除してください。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

[!INCLUDE[name-sos](../includes/name-sos-short.md)] は Windows、macOS、そして Linux で動作し、次のプラットフォームでサポートされています。

### <a name="windows"></a>Windows
- Windows 10 (64 ビット)
- Windows 8.1 (64 ビット)
- Windows 8 (64 ビット)
- Windows 7 (SP1) (64 ビット) - [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767) が必要です
- Windows Server 2016
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>推奨システム要件
最適なエクスペリエンスは、推奨システム要件を使用してください。
[メモリを定量化する更新プログラムは、ここを必要があります]

|             | CPU コア | メモリと RAM |
|:-----------|:---------|:----------|
| 推奨 |     4     |      8 GB    |
|   最小   |     2     |      4 GB     |
|             |           |            |

## <a name="check-for-updates"></a>更新を確認する
最新の更新を確認するには、ウィンドウの左下にある歯車アイコンをクリックして **更新を確認する** をクリックしてください。

## <a name="supported-sql-offerings"></a>サポートされる SQL 製品

* このバージョンの Azure データ Studio はすべて[サポート対象バージョンの SQL Server 2014 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ](https://support.microsoft.com/lifecycle?C2=1044) Azure SQL Database と Azure SQL Data Warehouse で最新のクラウド機能の使用をサポートしています。 Azure Data Studio には、Azure SQL マネージ インスタンスのプレビュー サポートも提供します。

## <a name="upgrade-from-sql-operations-studio"></a>SQL Operations Studio からのアップグレード

SQL Operations Studio を使用している場合は、Azure Data Studio にアップグレードする必要があります。 SQL Operations Studio は、Azure Data Studio のプレビュー バージョンとプレビュー名前でした。 2018 年 9 月に、私たち[Azure Data Studio に名前が変更](https://cloudblogs.microsoft.com/sqlserver/2018/09/25/azure-data-studio-for-sql-server/)と一般公開 (GA) バージョンをリリースしました。 SQL Operations Studio は不要になったされている更新もサポート、SQL Operations Studio のすべてのユーザー要求を最新の機能では、セキュリティ更新プログラムを取得する Azure Data Studio の最新バージョンをダウンロードして、修正するためです。
 
最新の Azure Data Studio には、古いプレビューからアップグレードする際、現在の設定と拡張機能は失われます。 設定を移動するには次の手順に従います*ユーザー設定の移動*セクション。


## <a name="move-user-settings"></a>ユーザー設定を移動します。

カスタム設定を移動する場合はキーボード ショートカット、またはコード スニペットでは、以下の手順に従います。 これは、SQL Operations Studio のバージョンから Azure Data Studio にアップグレードする場合に重要です。

*Azure Data Studio が既にあるか、インストールまたは SQL Operations Studio をカスタマイズしたことはありません、このセクションを無視できます。*


1. 左下にある歯車をクリックして設定を開く**設定します。**

   ![オープン設定](./media/download/open-settings.png)

2. 右クリックし、**ユーザー設定**上部タブし、をクリックして**エクスプ ローラーで表示**

   ![エクスプ ローラーの表示](./media/download/reveal-in-explorer.png)

3. このフォルダー内のすべてのファイルをコピーし、ドキュメント フォルダーのように、ローカル ドライブ上の場所を検索する形で保存します。

   ![設定のコピー](./media/download/copy-settings.png)

4. 新しいバージョンの Azure Data Studio、手順 3 の後は、1 ~ 2 がフォルダーに保存した内容を貼り付ける手順に従います。 設定、キー バインド、またはスニペットではそれぞれの場所を手動でコピーできます。

5. 既存のインストールを上書きする場合は、リソース エクスプ ローラーの Azure アカウントへの接続エラーを回避するためにインストールする前に、古いインストール ディレクトリを削除します。

## <a name="next-steps"></a>次の手順

開始する次のクイック スタートのいずれかを参照してください。
- [接続および SQL Server のクエリ](quickstart-sql-server.md)
- [接続および Azure SQL Database のクエリ](quickstart-sql-database.md)
- [接続し、Azure Data Warehouse に対するクエリ](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)します。