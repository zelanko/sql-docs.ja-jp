---
title: ダウンロードし、Azure Data Studio のインストール |Microsoft Docs
description: ダウンロードと Windows 用の Azure データ Studio のインストール、macOS、または Linux
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88b79feb3b04dcc7f872653b2e24a9f70c370f57
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038996"
---
# <a name="download-and-install-azure-data-studio"></a>ダウンロードし、Azure Data Studio のインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で動作します。

ダウンロードして、最新のリリースでは、インストール、*年 9 月 GA リリース*:

> [!NOTE]
> SQL Operations Studio から更新しているし、設定、キーボード ショートカット、またはコード スニペットを保持する場合は、次を参照してください。[ユーザー設定の移動](#move-user-settings)します。

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=2024683)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2024680)|2018 年 9 月 24 日 |1.0|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2024677)|2018 年 9 月 24 日 |1.0|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2024668)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2024672)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2024675)|2018 年 9 月 24 日 |1.0|

最新のリリースに関する詳細は、次の [リリース ノート](release-notes.md) を参照してください。

## <a name="get-azure-data-studio-for-windows"></a>Windows 用 Azure Data Studio を入手します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)]のこのリリースは標準的な Windows インストーラーと .zip を含んでいます。 

**インストーラー**

1. [Windows 用の [!INCLUDE[name-sos](../includes/name-sos-short.md)] インストーラー](https://go.microsoft.com/fwlink/?linkid=2024683) ダウンロードして実行します。
1. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]のアプリを開始します。


**.zip ファイル**

1. [[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Windows .zip](https://go.microsoft.com/fwlink/?linkid=2024680) をダウンロードします。
2. ダウンロードしたファイルを参照し、展開します。
3. `\azuredatastudio-windows\azuredatastudio.exe`を実行します。


## <a name="get-azure-data-studio-for-macos"></a>MacOS 用の Azure データ Studio を入手します。

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for macOS](https://go.microsoft.com/fwlink/?linkid=2024677) をダウンロードします。
2. zip のコンテンツを展開するには、ダブルクリックします。
3. させる[!INCLUDE[name-sos](../includes/name-sos-short.md)]で使用できる、*スタート パッド*、ドラッグ*Azure データ Studio.app*を*アプリケーション*フォルダー。


## <a name="get-azure-data-studio-for-linux"></a>Linux 用 Azure Data Studio を入手します。

1. ダウンロード[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Linux を使用して、インストーラーまたは tar.gz アーカイブのいずれかで。
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2024668)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2024672)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2024675)
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
- Windows 7 (SP1) (64 ビット) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767) が必要です
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

## <a name="check-for-updates"></a>更新を確認する
最新の更新を確認するには、ウィンドウの左下にある歯車アイコンをクリックして **更新を確認する** をクリックしてください。

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


## <a name="next-steps"></a>次の手順

開始する次のクイック スタートのいずれかを参照してください。
- [接続および SQL Server のクエリ](quickstart-sql-server.md)
- [接続および Azure SQL Database のクエリ](quickstart-sql-database.md)
- [接続し、Azure Data Warehouse に対するクエリ](quickstart-sql-dw.md)

投稿する[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)します。
