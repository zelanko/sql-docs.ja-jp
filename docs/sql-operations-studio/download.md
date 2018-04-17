---
title: Microsoft SQL Operations Studio (プレビュー) のダウンロードおよびインストール | Microsoft ドキュメント
description: Windows、macOS、そして Linux に対応する Microsoft SQL Operations Studio (プレビュー) のダウンロードおよびインストール
ms.custom: tools|sos
ms.date: 03/28/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 836d34cdb019b7defd16736b21485a32474a8757
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>SQL Operations Studio (プレビュー) のダウンロードおよびインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で動作します。

下載並安裝最新版本，*3 月公開預覽*:

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=870837)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=870838)|2018 年 3 月 28日 |0.27.3|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=870839)|2018 年 3 月 28日 |0.27.3|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=870842)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=870841)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=870840)|2018 年 3 月 28日 |0.27.3|

最新のリリースに関する詳細は、次の [リリース ノート](release-notes.md) を参照してください。

## <a name="get-sql-operations-studio-preview-for-windows"></a>SQL Operations Studio (プレビュー) for Windows の取得

[!INCLUDE[name-sos](../includes/name-sos-short.md)]のこのリリースは標準的な Windows インストーラーと .zip を含んでいます。 

**インストーラー**

1. [Windows 用の [!INCLUDE[name-sos](../includes/name-sos-short.md)] インストーラー](https://go.microsoft.com/fwlink/?linkid=870837) ダウンロードして実行します。
1. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]のアプリを開始します。


**.zip ファイル**

1. [[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Windows .zip](https://go.microsoft.com/fwlink/?linkid=870838) をダウンロードします。
2. ダウンロードしたファイルを参照し、展開します。
3. `\sqlops-windows\sqlops.exe`を実行します。


## <a name="get-sql-operations-studio-preview-for-macos"></a>SQL Operations Studio (プレビュー) for MacOS の取得

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for macOS](https://go.microsoft.com/fwlink/?linkid=870839) をダウンロードします。
2. zip のコンテンツを展開するには、ダブルクリックします。
3. [!INCLUDE[name-sos](../includes/name-sos-short.md)] を *Launchpad* で有効にするため *sqlops.app* を *アプリケーション* フォルダーへドラッグします。


## <a name="get-sql-operations-studio-preview-for-linux"></a>SQL Operations Studio (プレビュー) for Linux の取得

1. ダウンロード[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Linux のインストーラーまたは tar.gz アーカイブのいずれかを使用します。
    - [.deb](https://go.microsoft.com/fwlink/?linkid=870842)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=870841)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=870840)
1. ファイルを展開し、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を起動するため、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   **Debian のインストール:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **rpm インストール:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **tar.gz インストール:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > Debian、Redhat、および Ubuntu で、依存関係が見つからないことがあります。 これらの依存関係をインストールするために、Linux のバージョンに応じて、次のコマンドを使用してください。
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
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


## <a name="uninstall-sql-operations-studio-preview"></a>SQL Operations Studio (プレビュー)</a> のアンインストール

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

## <a name="next-steps"></a>次の手順

作業を開始する次のクイック スタートのいずれかを参照してください。
- [接続し、クエリの SQL Server](quickstart-sql-server.md)
- [接続し、Azure SQL データベースの照会](quickstart-sql-database.md)
- [接続し、Azure データ ウェアハウスのクエリ](quickstart-sql-dw.md)

投稿[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)です。
