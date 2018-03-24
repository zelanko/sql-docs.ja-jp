---
title: "Microsoft SQL Operations Studio (プレビュー) のダウンロードおよびインストール | Microsoft ドキュメント"
description: "Windows、macOS、そして Linux に対応する Microsoft SQL Operations Studio (プレビュー) のダウンロードおよびインストール"
ms.custom: tools|sos
ms.date: 03/05/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1cb41e1824fc157932e2cb08292608bb97e46712
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="download-and-install-sql-operations-studio-preview"></a>SQL Operations Studio (プレビュー) のダウンロードおよびインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で動作します。

最新のリリース, *2 月のパブリック プレビュー* のダウンロードとインストール:

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=867998)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=867997)|2018 年 2 月 15日 |0.26.7|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=867999)|2018 年 2 月 15日 |0.26.7|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=868002)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=868001)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=868000)|2018 年 2 月 15日|0.26.7|

最新のリリースに関する詳細は、次の [リリース ノート](release-notes.md) を参照してください。

## <a name="get-sql-operations-studio-preview-for-windows"></a>SQL Operations Studio (プレビュー) for Windows の取得

[!INCLUDE[name-sos](../includes/name-sos-short.md)] のこのリリースは標準的な Windows インストーラーと .zip を含んでいます。

**インストーラー**

1. ダウンロードし、[ [!INCLUDE[name-sos](../includes/name-sos-short.md)] Windows 用のインストーラー](https://go.microsoft.com/fwlink/?linkid=867998) を実行します。
1. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] のアプリを開始します。


**.zip file**

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for Windows .zip](https://go.microsoft.com/fwlink/?linkid=867997) をダウンロードします。
2. ダウンロードしたファイルを参照し、展開します。
3. `\sqlops-windows\sqlops.exe` を実行します。


## <a name="get-sql-operations-studio-preview-for-macos"></a>SQL Operations Studio (プレビュー) for MacOS の取得

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] macOS の](https://go.microsoft.com/fwlink/?linkid=867999) をダウンロードします。
2. zip の内容を展開し、ダブルクリックします。
3. [!INCLUDE[name-sos](../includes/name-sos-short.md)] を *Launchpad* で有効にするため *sqlops.app* を *アプリケーション* フォルダーへドラッグします。


## <a name="get-sql-operations-studio-preview-for-linux"></a>SQL Operations Studio (プレビュー) for Linux の取得

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for Linux](https://go.microsoft.com/fwlink/?linkid=868000) をダウンロードします。
1. ファイルを展開し、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を起動するため、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   > [!NOTE]
   > Debian、Redhat、および Ubuntu で、依存関係が見つからないことがあります。これらの依存関係をインストールするために、Linux のバージョンに応じて、次のコマンドを使用してください。


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


## <a name="uninstall-sql-operations-studio-preview"></a>SQL Operations Studio (プレビュー) のアンインストール

Windows インストーラーを使用して [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] をインストールした場合、他の Windows アプリケーションの削除と同じ方法でアンインストールしてください。

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

## <a name="check-for-updates"></a>アップデートの確認
最新のアップデートを確認するためには、ウィンドウの左下にある歯車アイコンをクリックして **更新プログラムの確認** をクリックしてください。

## <a name="next-steps"></a>次の手順

作業を開始する次のクイック スタートのいずれかを参照してください。
- [接続し、クエリの SQL Server](quickstart-sql-server.md)
- [接続し、Azure SQL データベースの照会](quickstart-sql-database.md)
- [接続し、Azure データ ウェアハウスのクエリ](quickstart-sql-dw.md)

投稿[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)です。
